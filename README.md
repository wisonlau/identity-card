China (region) citizen ID card tool
------------------------
<br>

>  China (Mainland) ID card package, the data from the national standard `GB/T 2260-2007`  <a href="http://www.stats.gov.cn" target="_blank"> (People's Republic of China administrative divisions code standard).</a>

## Installing

```bash

    composer require wisonlau/identity-card
```


## Instructions
A component based on People's Republic of China citizen ID card to obtain the user information.This works for any php framework, but only if the php version is greater than 7.1.

## Useing

#### Verify your Chinese ID card
```php

    // Result false OR Ofcold\IdentityCard\IdentityCard instance.
    $result = Ofcold\IdentityCard\IdentityCard::make('32010619831029081');

    if ( $result === false ) {

        return 'Your ID number is incorrect';
    }

    print_r($result->toArray());


```

#### OR test file.
```bash
    php test
```


```php

$idCard = Ofcold\IdentityCard\IdentityCard::make('320106198310290811', 'en');
//  Use locale, Current supported zh-cn,en
// $idCard = Ofcold\IdentityCard\IdentityCard::make('320106198310290811', 'zh-cn');
if ( $idCard === false ) {

    return 'Your ID number is incorrect';
}
$area = $idCard->getArea();
$gender = $idCard->getGender();
$birthday = $idCard->getBirthday();
$age = $idCard->getAge();
$constellation = $idCard->getConstellation();
```


#### Results:
```json
{
    "area": "shan xi sheng yun cheng di qu yun cheng shi",
    "province": "shan xi sheng",
    "city": "yun cheng di qu",
    "county": "yun cheng shi",
    "gender": "Male",
    "birthday": "1980-03-12",
    "zodiac": "Pig",
    "age": 38,
    "constellation": "Pisces"
}
```

### Api
- getArea() : string `Get Area`
- getConstellation() : string `Get constellation`
- getZodiac() : string `Get zodiac`
- getAge() : int `Get age`
- getBirthday(string $foramt = 'Y-m-d') : string `Get birthday`
- getGender() : string `Get gender`
- getCounty() : string|null `Get county`
- getCity() : string|null `Get city`
- getProvince() : string|null `Get province`
- toArray() : array `Get all information.`
- toJson(int $option) : string `Json format all information`
- __get() : mixed
- __toString() : toJson
