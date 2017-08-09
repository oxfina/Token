# OxToken contract

## Testing

These contracts have been developed using the Truffle framework:  
https://github.com/trufflesuite/truffle

To test, you can:

1. Run `testrpc` (see https://github.com/ethereumjs/testrpc).
1. Run `truffle test`

Expected output from test is:
```
Using network 'development'.

Compiling ./contracts/Migrations.sol...
Compiling ./contracts/OxToken.sol...
Compiling ./contracts/test/OxTokenMock.sol...
Compiling ./installed_contracts/zeppelin/contracts/SafeMath.sol...
Compiling ./installed_contracts/zeppelin/contracts/lifecycle/Destructible.sol...
Compiling ./installed_contracts/zeppelin/contracts/ownership/Ownable.sol...
Compiling ./installed_contracts/zeppelin/contracts/token/BasicToken.sol...
Compiling ./installed_contracts/zeppelin/contracts/token/ERC20.sol...
Compiling ./installed_contracts/zeppelin/contracts/token/ERC20Basic.sol...
Compiling ./installed_contracts/zeppelin/contracts/token/LimitedTransferToken.sol...
Compiling ./installed_contracts/zeppelin/contracts/token/StandardToken.sol...

Compilation warnings encountered:

/Users/adamdossa/Development/Ethereum/OxToken/installed_contracts/zeppelin/contracts/token/LimitedTransferToken.sol:46:47: : Unused local variable
  function transferableTokens(address holder, uint64 time) constant public returns (uint256) {
                                              ^---------^
,/Users/adamdossa/Development/Ethereum/OxToken/contracts/OxToken.sol:51:47: : Unused local variable
  function transferableTokens(address holder, uint64 time) constant public returns (uint256) {
                                              ^---------^

Coinbase Account:  0xadbb105458c21afea255a68d2389b3c0fac4196d


  Contract: OxToken
Token Address:  0x5c55117ad5b50791bb02244e0bf77fca1162695f
    ✓ 0. initialize contract (132ms)

  Contract: OxToken
    ✓ 1. start and end sale (263ms)

  Contract: OxToken
    ✓ 2. checks amounts and bonuses (423ms)

  Contract: OxToken
    ✓ 3. check transfers (324ms)

  Contract: OxToken
    ✓ 4. allocate owner tokens (161ms)


  5 passing (1s)
```

## Deployment

I have provided three scripts to ease deployment:  
deploy.js  
startSale.js  
allocateOwnerTokens.js

These files have further instructions, but see below for basic usage.

1. deploy.js: Run using `node scripts/deploy.js build/contracts/OxToken.json`. This will log out the new <contract_address>.
1. startSale.js: Run using `node scripts/startSale.js build/contracts/OxToken.json <contract_address>`. Replace <contract_address> with the address logged from 1.
1. allocateOwnerTokens.js: `node scripts/allocateOwnerTokens.js build/contracts/OxToken.json <contract_address>`. Replace <contract_address> with the address logged from 1. Note - this can only be run once the sale has completed.

Note - you will need some small amount of gas in your coinbase account to deploy contracts to mainnet.
