
# Solidity Exception Handling

This Solidity smart contract demonstrates the use of `require()`, `assert()`, and `revert()` statements.
It includes three functions: `deposit`, `withdraw`, and `transfer`, each showcasing these statements.

## Smart Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ExceptionHandling {

    uint public balance;

    constructor() {
        balance = 100; // Initial balance
    }

    function deposit(uint amount) public {
        require(amount > 0, "Amount must be greater than zero");
        balance += amount;
    }

    function withdraw(uint amount) public {
        require(amount <= balance, "Insufficient balance");
        balance -= amount;
        assert(balance >= 0);
    }

    function transfer(uint amount, address to) public {
        require(amount <= balance, "Insufficient balance");
        if (to == address(0)) {
            revert("Invalid address");
        }
        balance -= amount;
        assert(balance >= 0);
    }
}
```
