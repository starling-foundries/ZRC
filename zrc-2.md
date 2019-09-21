|  ZRC | Title | Status| Type | Author | Created (yyyy-mm-dd) | Updated (yyyy-mm-dd)
|--|--|--|--| -- | -- | -- |
| 2  | Standard for Fungible Tokens | Draft | Meta  | Gareth Mensah <gareth@zilliqa.com> | 2019-09-21 | 2019-09-21 

<br/> 

## What are Fungible Tokens?

ZRC-2 is Zilliqa's standard for fungible tokens, which are tokens of the same type that are interchangeable and divisible into smaller units. This standard API provides basic functionalities such as transfer, approval and spending.
<br/>

## Abstract 

The following standard allows for the implementation of a standard API for tokens within smart contracts. This standard provides basic functionality to transfer tokens, as well as allow tokens to be approved so they can be spent by another on-chain third party.
<br/>

## Motivation

A standard interface allows any tokens on Zilliqa to be re-used by other applications: from wallets to decentralized exchanges.
<br/>

## Specification

**Errror Codes**
```ocaml
let code_success = Uint32 0
let code_failure = Uint32 1
let code_not_authorized = Uint32 2
let code_not_found = Uint32 4
let code_bad_request = Uint32 5
let code_unexpected_error = Uint32 9
let code_owner_not_right = Uint32 10
```

<br/>

**Approve()**

```ocaml
(* Approves an address to transfer the given amount of tokens *)
transition approve(to: ByStr20, tokens: Uint128)
```

|  | Name | Type| Description
|--|--|--|--|
| @param | to | ByStr20 | Address to be approved for the given token id. |
| @param | tokens | Uint128 | Amount of tokens to be approved. |

|  | Name | Description
|--|--|--|
| eventName | "Approve" | emit event if the call is successful. |
  
<br/>

**Transfer()**

```ocaml
(* Transfer the ownership of a given token ID to another address *)
transition transfer(to: ByStr20, tokens: Uint128)
```

|  | Name | Type| Description
|--|--|--|--|
| @param | from | ByStr20 | Current owner of the token. |
| @param | to | ByStr20 | Recipient address of the token. |
| @param | tokens | Uint128 | Amount of tokens to be transferred. |

|  | Name | Description
|--|--|--|
| eventName | "Transfer" | emit event if the call is successful. |

<br/>

**OwnerOf()**

```ocaml
(* Get the owner of a particular tokenId *)
transition ownerOf(tokenId: Uint256)
```

|  | Name | Type| Description
|--|--|--|--|
| @param | tokenId | Uint256 | Id of a given token. |

|  | Name | Description
|--|--|--|
| eventName | "OwnerOf" | emit event if the call is successful. |

<br/>

**BalanceOf()**

```ocaml
(* Count the number of NFTs assigned to an owner *)
transition balanceOf(address: ByStr20)
```

|  | Name | Type| Description
|--|--|--|--|
| @param | address | ByStr20 | Address of an owner. |

|  | Name | Description
|--|--|--|
| eventName | "BalanceOf" | emit event if the call is successful. |

<br/>

**Mint()**

```ocaml
(* Mint new tokens *)
transition mint(to: ByStr20, key: String)
```

|  | Name | Type| Description
|--|--|--|--|
| @param | to | ByStr20 | Address of the token recipient. |
| @param | key | String | Token key of the new token. |

|  | Name | Description
|--|--|--|
| eventName | "Birth" | emit event if the call is successful. |

<br/>

## Existing Implementations

* [Zilliqa Celebrity card](https://viewblock.io/zilliqa/address/zil1262aknuja095r33kk20mcmwfvjc4wn9wwcjx7u)
* [SuperPlayer NFT](https://viewblock.io/zilliqa/address/zil1vxl33hrua4wsld32zk2fjm6qv3qu4tg6cw4azu)

<br/>

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
