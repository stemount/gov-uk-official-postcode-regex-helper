# GOV.UK Official Postcode Regex and Helpers

This repo contains the GOV.UK Postcode Regex which is a good place to start for UK Postcodes as this has been carefully considered by the GOV.UK team, ensuring it will match all valid UK Postcodes.

There will very likely existing solutions postcode regex available in your GraphQL/REST MVC API framework, but this project does not have these helpers yet [Issue #2](https://github.com/stemount/gov-uk-official-postcode-regex-helper/issues/2).

This would not be suitable if you wanted to localise postcode lookup to postcodes outside of the UK, there's already great things for that. Follow [Issue #6](https://github.com/stemount/gov-uk-official-postcode-regex-helper/issues/6) here.

## Source<sup>1</sup>

#### UK Postcode Regular Expression

The following is the UK Postcode Regular Expression and the corresponding detail explaining the logic behind the UK Postcode Regular Expression.

###### 3.1 Expression

`^([Gg][Ii][Rr] 0[Aa]{2})|((([A-Za-z][0-9]{1,2})|(([A-Za-z][A-Ha-hJ-Yj-y][0-9]{1,2})|(([A- Za-z][0-9][A-Za-z])|([A-Za-z][A-Ha-hJ-Yj-y][0-9]?[A-Za-z])))) [0-9][A-Za-z]{2})$`

###### 3.2 Logic

"GIR 0AA"
- **OR**
  - One letter followed by either one or two numbers
  - One letter followed by a second letter that must be one of ABCDEFGHJ KLMNOPQRSTUVWXY (i.e..not I) and then followed by either one or two numbers
- **OR**
  - One letter followed by one number and then another letter
- **OR**
  - A two part post code
    where the first part must be
    One letter followed by a second letter that must be one of ABCDEFGH JKLMNOPQRSTUVWXY (i.e..not I) and then followed by one number and optionally a further letter after that
  - **AND**
  - The second part (separated by a space from the first part) must be One number followed by two letters.

A combination of upper and lower case characters is allowed.
Note: the length is determined by the regular expression and is between 2 and 8 characters.

## Sources
[1] [Page 3 of Bulk Transfer Validation](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/488478/Bulk_Data_Transfer_-_additional_validation_valid_from_12_November_2015.pdf)
