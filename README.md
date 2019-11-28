## Performax CPI

##### Admin & Guide

* Admin : [network-console.theallad.co.kr](http://network-console.theallad.co.kr)

* Guide : [http://wiki.performax.co.kr](http://wiki.performax.co.kr)



##### Tracker 연동 완료 후 진행 절차

1. Test Offer & Affiliate 생성
2. Test 진행 (모바일 기기) 및 실적 전환 확인 (Performax & Tracker)
3. 광고주 연동



## Tracker 연동 내역

### Appsflyer

* Dashboard :  [https://hq1.appsflyer.com/auth/login](https://hq1.appsflyer.com/auth/login)

* Test Link : [https://app.appsflyer.com/com.appsflyer.adNetworkTest?af_siteid={affiliate_id}&af_sub_siteid={source}&af_c_id={offer_id}&af_sub1={aff_sub}&af_sub2={aff_sub2}&af_sub3={aff_sub3}&af_sub4={aff_sub4}&af_sub5={aff_sub5}&pid=alladfun_int&af_click_lookback=7d&clickid={transaction_id}](https://app.appsflyer.com/com.appsflyer.adNetworkTest?af_siteid={affiliate_id}&af_sub_siteid={source}&af_c_id={offer_id}&af_sub1={aff_sub}&af_sub2={aff_sub2}&af_sub3={aff_sub3}&af_sub4={aff_sub4}&af_sub5={aff_sub5}&pid=alladfun_int&af_click_lookback=7d&clickid={transaction_id})

##### 1. Click Attribution Link

```
http://app.appsflyer.com/{app_id}?pid=&clickid={transaction_id}&af_siteid={affiliate_id}&af_sub_siteid={source}&af_c_id={offer_id}&af_click_lookback=7d&af_viewthrough_lookback=7d&af_sub1={aff_sub}&af_sub2={aff_sub2}&af_sub3={aff_sub3}&af_sub4={aff_sub4}&af_sub5={aff_sub5}
```

| Appsflyer Parameters    | Description                                                  | Performax Macros | Description   |
| ----------------------- | ------------------------------------------------------------ | ---------------- | ------------- |
| pid                     | 미디어 소스, AppsFlyer에서 제공하며 변경 안됨                |                  |               |
| clickid                 | 고유 클릭 ID                                                 | {transaction_id} | 고유 클릭 ID  |
| af_siteid               | 매체 ID                                                      | {affiliate_id}   | 매체 ID       |
| af_sub_siteid           | 서브 매체 ID                                                 | {source}         | 서브 매체 ID  |
| af_c_id                 | 캠페인 ID                                                    | {offer_id}       | 캠페인 ID     |
| af_click_lookback       | 클릭 기여에 대한 전환 확인 기간, 이 기간은 새 사용자가 광고 / 링크를 표시하는 소스에 기인 한 최대 CTIT (클릭하여 설치 시간) | 7d               |               |
| af_viewthrough_lookback | 조회 후 기여에 대한 전환 확인 기간                           | 7d               |               |
| af_sub1                 | Sub Parameter 1                                              | {aff_sub}        | 추가 파라미터 |
| af_sub2                 | Sub Parameter 2                                              | {aff_sub2}       | 추가 파라미터 |
| af_sub3                 | Sub Parameter 3                                              | {aff_sub3}       | 추가 파라미터 |
| af_sub4                 | Sub Parameter 4                                              | {aff_sub4}       | 추가 파라미터 |
| af_sub5                 | Sub Parameter 5                                              | {aff_sub5}       | 추가 파라미터 |

##### 2. Install Postback

```
http://network-tracking.theallad.co.kr/aff_lsr?transaction_id=(clickid)&google_aid=(advertiserId)&ios_ifa=(idfa)&conv_ip=(ip)&mobile_carrier=(carrier)&device_os_version=(os-version)&device_brand=(device-brand)&device_model=(device-model)&adv_sub=(af_sub1)&adv_sub2=(af_sub2)&adv_sub3=(af_sub3)&adv_sub4=(af_sub4)&adv_sub5=(af_sub5)
```

| Performax Parameters | Description           | Appsflyer Macros |
| -------------------- | --------------------- | ---------------- |
| transaction_id       | 고유 클릭 ID          | (clickid)        |
| google_aid           | ADID                  | (advertiserId)   |
| ios_ifa              | IDFA                  | (idfa)           |
| conv_ip              | 전환이 발생한 기기 IP | (ip)             |
| mobile_carrier       | 통신사                | (carrier)        |
| device_os_version    | 기기 OS 버전          | (os-version)     |
| device_brand         | 기기 제조사           | (device-brand)   |
| device_model         | 기기 모델명           | (device-model)   |
| adv_sub              | 추가 파라미터         | (af_sub1)        |
| adv_sub2             | 추가 파라미터         | (af_sub2)        |
| adv_sub3             | 추가 파라미터         | (af_sub3)        |
| adv_sub4             | 추가 파라미터         | (af_sub4)        |
| adv_sub5             | 추가 파라미터         | (af_sub5)        |

##### 3. In-app Event Postback

```
http://network-tracking.theallad.co.kr/aff_goal?a=lsr&goal_id=(event-name)&transaction_id=(clickid)&google_aid=(advertiserId)&ios_ifa=(idfa)&conv_ip=(ip)&mobile_carrier=(carrier)&device_os_version=(os-version)&device_brand=(device-brand)&device_model=(device-model)&amount=(monetary)&conversion_event_datetime=(timestamp)&adv_sub=(af_sub1)&adv_sub2=(af_sub2)&adv_sub3=(af_sub3)&adv_sub4=(af_sub4)&adv_sub5=(af_sub5)
```

| Performax Parameters      | Description           | Appsflyer Macros |
| ------------------------- | --------------------- | ---------------- |
| goal_id                   | 이벤트 이름           | (event-name)     |
| transaction_id            | 고유 클릭 ID          | (clickid)        |
| google_aid                | ADID                  | (advertiserId)   |
| ios_ifa                   | IDFA                  | (idfa)           |
| conv_ip                   | 전환이 발생한 기기 IP | (ip)             |
| mobile_carrier            | 통신사                | (carrier)        |
| device_os_version         | 기기 OS 버전          | (os-version)     |
| device_brand              | 기기 제조사           | (device-brand)   |
| device_model              | 기기 모델명           | (device-model)   |
| amount                    | 이벤트 금액           | (monetary)       |
| conversion_event_datetime | 이벤트 발생 시간      | (timestamp)      |
| adv_sub                   | 추가 파라미터         | (af_sub1)        |
| adv_sub2                  | 추가 파라미터         | (af_sub2)        |
| adv_sub3                  | 추가 파라미터         | (af_sub3)        |
| adv_sub4                  | 추가 파라미터         | (af_sub4)        |
| adv_sub5                  | 추가 파라미터         | (af_sub5)        |

참고 자료

* [https://www.appsflyer.com/kr/resources/ecommerce/getting-started-mobile-
  attribution-guide](https://www.appsflyer.com/kr/resources/ecommerce/getting-started-mobile-attribution-guide)
* [https://support.appsflyer.com/hc/en-us/articles/207447163-AppsFlyer-Tracking-Link-Structure-and-Parameters](https://support.appsflyer.com/hc/en-us/articles/207447163-AppsFlyer-Tracking-Link-Structure-and-Parameters)
* [https://support.appsflyer.com/hc/en-us/articles/207273946-Postback-macros-for-Ad-Networks](https://support.appsflyer.com/hc/en-us/articles/207273946-Postback-macros-for-Ad-Networks)


### Adbrix

##### 1. Attribution Postback

```
http://network-tracking.theallad.co.kr/aff_lsr?transaction_id={cb_1}&google_aid={req.common.identity.adid}&ios_ifa={req.common.identity.adid}&conv_ip={a_ip}&mobile_carrier={req.common.device_info.carrier}&device_os_version={req.common.device_info.os}&device_brand={req.common.device_info.vendor}&device_model={req.common.device_info.model}&adv_sub2={cb_2}&adv_sub3={cb_3}&adv_sub4={cb_4}&adv_sub5={cb_5}
```
| Performax Parameters | Description           | Adbrix Macros                    |
| -------------------- | --------------------- | -------------------------------- |
| transaction_id       | 고유 클릭 ID          | {cb_1}                           |
| google_aid           | ADID                  | {req.common.identity.adid}       |
| ios_ifa              | IDFA                  | {req.common.identity.adid}       |
| conv_ip              | 전환이 발생한 기기 IP | {a_ip}                           |
| mobile_carrier       | 통신사                | {req.common.device_info.carrier} |
| device_os_version    | 기기 OS 버전          | {req.common.device_info.os}      |
| device_brand         | 기기 제조사           | {req.common.device_info.vendor}  |
| device_model         | 기기 모델명           | {req.common.device_info.model}   |
| adv_sub2             | 추가 파라미터         | {cb_2}                           |
| adv_sub3             | 추가 파라미터         | {cb_3}                           |
| adv_sub4             | 추가 파라미터         | {cb_4}                           |
| adv_sub5             | 추가 파라미터         | {cb_5}                           |

##### 2. Event Postback

```
http://network-tracking.theallad.co.kr/aff_goal?a=lsr&goal_id={req.evt.event_name}&transaction_id={last.cb_1}&google_aid={req.common.identity.adid}&ios_ifa={req.common.identity.adid}&conv_ip={last.a_ip}&mobile_carrier={req.common.device_info.carrier}&device_os_version={req.common.device_info.os}&device_brand={req.common.device_info.vendor}&device_model={req.common.device_info.model}&conversion_event_datetime={req.evt.event_timestamp}&adv_sub2={last.cb_2}&adv_sub3={last.cb_3}&adv_sub4={last.cb_4}&adv_sub5={last.cb_5}
```

| Performax Parameters      | Description           | Adbrix Macros                    |
| ------------------------- | --------------------- | -------------------------------- |
| goal_id                   | 이벤트 이름           | {req.evt.event_name}             |
| transaction_id            | 고유 클릭 ID          | {last.cb_1}                      |
| google_aid                | ADID                  | {req.common.identity.adid}       |
| ios_ifa                   | IDFA                  | {req.common.identity.adid}       |
| conv_ip                   | 전환이 발생한 기기 IP | {last.a_ip}                      |
| mobile_carrier            | 통신사                | {req.common.device_info.carrier} |
| device_os_version         | 기기 OS 버전          | {req.common.device_info.os}      |
| device_brand              | 기기 제조사           | {req.common.device_info.vendor}  |
| device_model              | 기기 모델명           | {req.common.device_info.model}   |
| conversion_event_datetime | 이벤트 발생 시간      | {req.evt.event_timestamp}        |
| adv_sub2                  | 추가 파라미터         | {last.cb_2}                      |
| adv_sub3                  | 추가 파라미터         | {last.cb_3}                      |
| adv_sub4                  | 추가 파라미터         | {last.cb_4}                      |
| adv_sub5                  | 추가 파라미터         | {last.cb_5}                      |

참고 자료

* [https://help.adbrix.io/hc/ko/sections/360001417213-Partner-Integration](https://help.adbrix.io/hc/ko/sections/360001417213-Partner-Integration)

