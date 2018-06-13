---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the NoMoreBounce API! You can use our API to access NoMoreBounce API endpoints.

You can view code examples in the dark area to the right,
and you can switch the programming language of the examples with the tabs in the top right.

To use the API you have to create a "Connector". To do this you have to go in
the "Connectors" menu. Than you can add an "API Connector" pushing the "Connect"
button.
You can add all the connectors you want, to use from different applications.
Once you have pushed the "Add" button, you can chose a name for your connector.
After pushed the "Save" button you will see a "Connector ID" and a "Token".


# Checker

## Check a single email address

This endpoint retrieves all kittens.

> The above command returns JSON structured like this:

```json
{
  "status": 200,
  "msg": "A specific message",
  "email": "The email checked"
}
```

### HTTP Request

`GET https://www.nomorebounce.com/api/v1/check/<CONN_ID>/`

### Query Parameters

Parameter | Description
--------- | -----------
email | The email address that you want to check (required)
token | The token that you can find in the connectors page (required)

Parameter | Default | Description
--------- | ------- | -----------
force_check | false | If true erases the result (if checked in the past) and makes another check.

<aside class="success">
Remember — if you force check you will consume a credit per email address.
</aside>


# Account

## Credits Available

> The above command returns JSON structured like this:

```json
{
  "status": 200,
  "credits": 1500
}
```

This endpoint gives you the available total credit (free credits and payed credits).

### HTTP Request

`GET https://www.nomorebounce.com/api/v1/account/credits/<CONN_ID>/`

### URL Parameters

Parameter | Description
--------- | -----------
token | The token that you can find in the connectors page (required)


# Mail importer

## Listing the imported emails lists

> The above command returns JSON structured like this:

```json
{
  "status": 200,
  "lists" : [{"id":1,
            "code": "List name",
            "created": "2018-03-03 10:00:00",
            "last_modified": "2018-03-03 10:00:00"}, ...]
}
```

This endpoint returns all the lists imported.

### HTTP Request

`GET https://www.nomorebounce.com/api/v1/importer/lists/<CONN_ID>/`

### URL Parameters

Parameter | Description
--------- | -----------
token | The token that you can find in the connectors page (required)


## Listing the emails in a specific list

> The above command returns JSON structured like this:

```json
{
  "status": 200,
  "count": 120,
  "num_pages": 10,
  "emails" : [{"email":1,
            "msg": "Exists",
            "last_check": "2018-03-03 10:00:00",
            "created": "2018-03-03 10:00:00"}, ...]
}
```

This endpoint returns all the emails in a list. The list is paginated, 1000 emails per page.

### HTTP Request

`GET https://www.nomorebounce.com/api/v1/importer/emails-list/<CONN_ID>/`

### URL Parameters

Parameter | Description
--------- | -----------
token | The token that you can find in the connectors page (required)
list_id | The list ID (you can find it also in the Imported page)

Parameter | Default | Description
--------- | ------- | -----------
page | 1 | The page of the pagination. 1000 emails per page.
