---
page_title: "onepassword_item Data Source - terraform-provider-onepassword"
subcategory: ""
description: |-
  Use this data source to get details of an item by its vault uuid and either the title or the uuid of the item.
---

# Data Source `onepassword_item`

Use this data source to get details of an item by its vault uuid and either the title or the uuid of the item.

## Example Usage

```terraform
data "onepassword_item" "example" {
  vault = var.demo_vault
  uuid  = onepassword_item.demo_sections.uuid
}
```

## Schema

### Required

- **vault** (String, Required) The UUID of the vault the item is in.

### Optional

- **id** (String, Optional) The ID of this resource.
- **tags** (List of String, Optional) An array of strings of the tags assigned to the item.
- **title** (String, Optional) The title of the item.
- **uuid** (String, Optional) The UUID of the item. Item identifiers are unique within a specific vault.

### Read-only

- **category** (String, Read-only) The category of the item. One of ["login" "password" "database"]
- **database** (String, Read-only) (Only applies to the database category) The name of the database.
- **hostname** (String, Read-only) (Only applies to the database category) The address where the database can be found
- **password** (String, Read-only) Password for this item.
- **port** (String, Read-only) (Only applies to the database category) The port the database is listening on.
- **section** (List of Object, Read-only) A list of custom sections in an item (see [below for nested schema](#nestedatt--section))
- **type** (String, Read-only) (Only applies to the database category) The type of database. One of ["db2" "filemaker" "msaccess" "mssql" "mysql" "oracle" "postgresql" "sqlite" "other"]
- **url** (String, Read-only) The primary URL for the item.
- **username** (String, Read-only) Username for this item.

<a id="nestedatt--section"></a>
### Nested Schema for `section`

- **field** (List of Object) (see [below for nested schema](#nestedobjatt--section--field))
- **id** (String)
- **label** (String)

<a id="nestedobjatt--section--field"></a>
### Nested Schema for `section.field`

- **id** (String)
- **label** (String)
- **purpose** (String)
- **type** (String)
- **value** (String)


