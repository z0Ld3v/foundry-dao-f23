# MyGovernor DAO

MyGovernor is a simple Decentralized Autonomous Organization (DAO) built using the OpenZeppelin Governor contracts. It allows token holders to create and vote on proposals, which can then be executed if they reach a certain quorum and pass the voting process.

## Features

- Token-based voting: Token holders can vote on proposals based on their token balance.
- Customizable settings: Voting delay, voting period, and proposal threshold can be adjusted.
- Quorum requirement: A minimum quorum (4% of total token supply) is required for a proposal to pass.
- Timelock control: Approved proposals are sent to a timelock contract for execution after a delay.

## Contract Details

The `MyGovernor` contract inherits from the following OpenZeppelin contracts:

- `Governor`: The base Governor contract that provides the core functionality for creating and managing proposals.
- `GovernorSettings`: Allows customization of various settings like voting delay, voting period, and proposal threshold.
- `GovernorCountingSimple`: Provides simple vote counting mechanism where each account has one vote.
- `GovernorVotes`: Enables token-based voting where voting power is determined by token balance.
- `GovernorVotesQuorumFraction`: Enforces a minimum quorum of 4% of the total token supply for a proposal to pass.
- `GovernorTimelockControl`: Integrates with a timelock contract to enforce a delay before executing approved proposals.

The contract constructor takes two parameters:
- `_token`: The address of the token contract that will be used for voting.
- `_timelock`: The address of the timelock contract that will handle the execution of approved proposals.

## Usage

1. Deploy the `MyGovernor` contract, passing the address of the token contract and the timelock contract.
2. Token holders can create new proposals by calling the `propose` function, specifying the target addresses, values, function calldata, and description.
3. Proposals enter a voting period after a specified voting delay (currently set to 1 block).
4. During the voting period (currently set to 1 week), token holders can vote on the proposal using the `castVote` function.
5. If the proposal reaches the required quorum (4% of total token supply) and has more votes in favor than against, it is considered successful.
6. Successful proposals are sent to the timelock contract for execution after a specified delay.

Note: The `MyGovernor` contract assumes the existence of a compatible token contract that implements the `IVotes` interface for token-based voting. Make sure to deploy and configure the token contract before deploying the `MyGovernor` contract.

## License

This contract is released under the MIT License.# foundry-dao-f23
