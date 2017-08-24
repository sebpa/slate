---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---
# Dokumentacja GMP

Witaj na stronie dokumentującej moduły GMP. Każdy z modułów realizuje szereg metod potrzebnych od kompleksowej obsługi płatności.
Niektóre z metod są wystawione poprzez API, część z nich jest wywoływanych poprzez odpowiednie eventy wrzucone do RabbitMQ. 
Reszta to metody wewnętrzne.

# Access Manager

## checkProductAccess

Sprawdzenie czy użytkownik ma dostęp do produktu.

```shell
# Przykładowe wywołanie
curl -H "Content-Type: application/json" -X POST -d 
'
{  
   "jsonrpc":"2.0",
   "id":0,
   "method":"checkProductAccess",
   "params":{  
      "portal":"ipla",
      "userId":"9997081",
      "accessGroups":[  
         "loc:pl"
      ],
      "product":{  
         "id":"ELEVEN",
         "type":"multiple",
         "subType":"packet",
         "portal":"ipla",
         "modificationDate":"2017-03-23 14:47:59"
      },
      "message":{  
         "id":"ipla_buy_plusbill",
         "timestamp":"2017-06-10T13:32:08.000+0200"
      }
   }
}'
http://localhost:8080/B2CPurchase
```

> Przykładowa odpowiedź

```json
{  
   "jsonrpc":"2.0",
   "id":0,
   "result":{  
      "status":-1,
      "statusDescription":"no access"
   }
}
```

### System

`GMP`
### Protokół
`JsonRpc`


### Parametry

Parametr | Wymagany | Typ | Przykład
--------- | --------- | --------- | --------- |
portal | | | |
userId | | | |
accessGroups | | | |
message | | | |
product &#124;&#124; products  | | | |

## preplayData

## getAcquiredProducts

## getCpWalletOptionData

## getProduct

## getMultipleProducts

## getVASProducts

## getOffer

## getPurchaseCodeProduct

# Transaction Manager

## getOrderId

## getOptionData

## buy

## buyStatus

## notifyProductAccessGranted

## getOrderStatus

## getPurchaseCodeProduct

## getPurchaseCodeOffer

## submitPurchaseCode

## ActivatePartnerProductRequest

## ActivatePartnerProductResponse

## DeactivatePartnerProductResponse

## ApplyChargeRequest

## ApplyChargeResponse

## canTrial

## updateOrderStatus

## dotpayStatus

## registerCard

# Renewal Manager

## prolongUserSubscription

## prolongAllEndingSubscriptions

# Post-Transaction Handler

## sendEmail

## sendSMS

## sendPush
Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Przykładowa sekcja

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

## Get All Kittens

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

