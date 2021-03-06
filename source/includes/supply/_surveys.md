## Surveys

The Survey resource contains basic information about a survey opportunity posted by a sample buyer. More detailed information about who qualifies for the survey is contained in the [Qualifications](#qualifications) and [Quotas](#quotas) resources.

#### Surveys Model

| Property                     | Type     | Description                                                                                                                                             |
|------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| SurveyName                   | string   | External name of the survey. This name may be exposed to respondents. This value is not unique across surveys.                                          |
| SurveyNumber                 | int      | Unique number associated with the survey.                                                                                                               |
| SurveySID                    | string   | Unique hash value (GUID) assoicated with the survey.                                                                                                    |
| AccountName                  | string   | Name of the buyer running the survey.                                                                                                                   |
| CountryLanguageID            | int      | Unique id associated with the country-language pair the survey is open to.                                                                              |
| LengthOfInterview            | int      | Median time for a respondent to complete the survey excluding the Fulcrum prescreener in minutes.                                                       |
| BidIncidence                 | double   | Estimated incidence rate of the survey as provided by the buyer.                                                                                        |
| Conversion                   | int      | Percentage of respondents who complete the survey after qualifying.                                                                                     |
| CPI                          | double   | Gross payout per complete. This value is before any applicable commissions or fees.                                                                     |
| FieldEndDate                 | datetime | Target date for survey closure. This field usually does not indicate a hard closure time, although buyers may opt to automatically close the study.     |
| IndustryID                   | int      | Industry associated with the survey's topic.                                                                                                            |
| StudyTypeID                  | int      | Indicates the survey's format and purpose (i.e. adhoc, recruit, etc).                                                                                   |
| OverallCompletes             | int      | Number of completes already achieved.                                                                                                                   |
| TotalRemaining               | int      | Number of completes still available.                                                                                                                    |
| CompletionPercentage         | int      | Percentage of the survey that has filled in terms of completes.                                                                                         |
| SurveyGroup                  | string   | Deprecated: Will return `null`. Instead use the SurveyGroupExists property.                                                                             |
| SurveyGroupID                | int      | Deprecated: Will return `null`. If SurveyGroupExists is `true`, then [list the survey's groups](#get-list-a-survey’s-groups).                           |
| SurveyGroupExists            | int      | Indicates whether there is a survey group(s) associated with the survey. (0=`false`, 1=`true`)                                                          |
| BidLengthOfInterview         | int      | Estimated time for a respondent to complete the survey excluding the Fulcrum prescreener in minutes as provided by the buyer.                           |
| TerminationLengthOfInterview | int      | Median time for a respondent to be termed in minutes.                                                                                                   |
| IsTrueSample                 | string   | Indicates whether True Sample's Identity Validation feature is enabled for the study.                                                                   |
| SurveyMobileConversion       | int      | Percentage of mobile respondents who complete the survey after qualifying.                                                                              |
| SurveyQuotaCalcTypeID        | int      | Indicates whether quotas are calculated based on completes or prescreens (1=Completes, 2=Prescreens).                                                   |
| SampleTypeID                 | int      | The type of sample the survey is open to (i.e. consumer, business-to-business, etc).                                                                    |

### GET List Exchange Surveys

> Definition

```plaintext
GET  https://api.samplicio.us/Supply/v1/Surveys/AllOfferwall/{SupplierCode}
```

> Example Request

```shell
curl -H "Authorization: YOUR_API_KEY_HERE" https://api.samplicio.us/Supply/v1/Surveys/AllOfferwall/{SupplierCode}
```

```ruby
require 'net/http'

uri = URI('https://api.samplicio.us/Supply/v1/Surveys/AllOfferwall/{SupplierCode}')

http = Net::HTTP.new(uri.host, uri.port)

http.use_ssl = true

request = Net::HTTP::Get.new(uri.request_uri)

request['Authorization'] = YOUR_API_KEY_HERE

response = http.request(request)  
```

```php
<?php
$URL = "https://api.samplicio.us/Supply/v1/Surveys/AllOfferwall/{SupplierCode}";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Authorization: YOUR_API_KEY_HERE";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);
?>
```

```python
import requests

url = 'https://api.samplicio.us/Supply/v1/Surveys/AllOfferwall/{SupplierCode}'

headers = {'Authorization' : YOUR_API_KEY_HERE}

response = requests.get(url, headers=headers)
```

```csharp
using System.Net;

WebRequest request = WebRequest.Create("https://api.samplicio.us/Supply/v1/Surveys/AllOfferwall/{SupplierCode}");

request.Headers.Add("Authorization", YOUR_API_KEY_HERE);

WebResponse response = request.GetResponse();
```

```javascript
const https = require('https');

var options = {
  "method": "GET",
  "hostname": "api.samplicio.us",
  "path": "/Supply/v1/Surveys/AllOfferwall/{SupplierCode}",
  "headers": {'Authorization': YOUR_API_KEY_HERE}
};

var request = https.request(options, function (response) {
  var chunks = [];

  response.on("data", function (chunk) {
    chunks.push(chunk);
  });

});

request.end();
```

> Example Response

```json
{
  "ApiResult": 0,
  "ApiResultCode": 0,
  "ApiAccount": "Anon",
  "AccountType": 2,
  "ApiAccountStatus": 1,
  "AccountCode": "AA",
  "ApiMessages": [
    "API Message: Response initialized.",
    "API Message: GetAllOfferwallSurveys successful."
  ],
  "ResultCount": 1,
  "Surveys": [
    {
      "SurveyName": "Asthma Sufferers",
      "SurveyNumber": 457751,
      "SurveySID": "26CB55E2-74CC-4E19-88E3-7F2F8D4DE74D",
      "AccountName": "Sample Company",
      "CountryLanguageID": 9,
      "LengthOfInterview": 12,
      "BidIncidence": 30,
      "Conversion": 1,
      "CPI": 1.5,
      "FieldEndDate": "\/Date(1388293200000-0600)\/",
      "IndustryID": 30,
      "StudyTypeID": 1,
      "OverallCompletes": 5,
      "TotalRemaining": 995,
      "CompletionPercentage": 0,
      "SurveyGroup": null,
      "SurveyGroupID": null,
      "SurveyGroupExists": 1,
      "BidLengthOfInterview": 10,
      "TerminationLengthOfInterview": 6,
      "SurveyQuotaCalcTypeID": 1,
      "IsTrueSample": false,
      "SurveyMobileConversion": 0,
      "SampleTypeID": null
    }
  ]
}
```

Returns a list of all live survey opportunities available through the Exchange for which you do not have an allocation or entry link.

<aside class="notice">After <a href="#post-create-a-link">creating an entry link</a> you can <a href="#get-list-allocated-surveys">list allocated surveys</a> or <a href="#get-show-an-allocated-survey">show an allocated survey</a> to access these opportunities.</aside>


#### Arguments

| Property                     | Type     | Required | Description                                                                                                                                  |
|------------------------------|----------|----------|----------------------------------------------------------------------------------------------------------------------------------------------|
| SupplierCode                 | string   | true     | Unique code associated with a supplier account.                                                                                              |
