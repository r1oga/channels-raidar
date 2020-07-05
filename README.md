# Channels Raidar

Monitoring of [Raiden Network](https://raiden.network/) Payment Channels.

## Contracts

|Name|Address|ABI|Network|Description|
|--|--|--|--|--|
|TokenNetwork|[`0x3EA2a1fED7FdEf300DA19E97092Ce8FdF8bf66A3`](https://goerli.etherscan.io/address/0x3EA2a1fED7FdEf300DA19E97092Ce8FdF8bf66A3)|[tttNetwork.json](./packages/contracts/src/abi/tttNetwork.json)|Goerli|Raiden Network's TokenNetwork contract for the TTT ERC-20 token
|CustomToken|[`0x59105441977ecD9d805A4f5b060E34676F50F806`](https://goerli.etherscan.io/address/0x59105441977ecd9d805a4f5b060e34676f50f806)|[tttErc20.json](./packages/contracts/src/abi/tttErc20.json)|Goerli|ERC20 Token Contract|

## Requirements
### [Initial](https://gist.github.com/r1oga/3d2749210a994749b57a39695fdf81e9)
- [x] Observe and list the `ChannelOpened`, `ChannelClosed` and `ChannelSettled` events emitted by the smart contract
- [x] Keep a list of the open raiden channels
- [ ] List should update as new events are observed
- [x] Write either in TypeScript or JavaScript
- [x] Use any of the following frameworks: ~~Vue.js~~, React, ~~Angular~~
- [ ] Build using a testable architecture
- [x] Manage state
- [ ] Provide tests

### Additional
- [x] Query smart contract state history using a [The Graph](https://thegraph.com/)'s [subgraph](https://thegraph.com/explorer/subgraph/r1oga/raiden-channels)
- [x] Filter by channel state (open, closed, settled)
- [ ] Filter by channel's participant address

## Available Scripts
Owing to this dependency on Yarn Workspaces, Create Eth App can't be used with npm.
### React App

#### `yarn react-app:start`

Runs the React app in development mode.  
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

<!-- #### `yarn react-app:test`

Runs the React test watcher in an interactive mode.<br>
By default, runs tests related to files changed since the last commit.

[Read more about testing React.](https://facebook.github.io/create-react-app/docs/running-tests) -->

<!-- #### `yarn react-app:build`

Builds the React app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the React documentation on [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

#### `yarn react-app:eject`

**Note: this is a one-way operation. Once you `react-app:eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` the React app at any time. This command will
remove the single build dependency from your React package.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right
into the `react-app` package so you have full control over them. All of the commands except `react-app:eject` will still work,
but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `react-app:eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it. -->

### Subgraph

[The Graph](https://thegraph.com/) is a tool for for indexing events emitted on the Ethereum blockchain. It provides you with an easy-to-use GraphQL API.  
To learn more, check out the [The Graph documentation](https://thegraph.com/docs).
#### Caveat
> By default query responses are **limited to 100 items per collection**. If you want to receive more, you can go up to 1000 items per collection and beyond that you can paginate.
See [thegraph faq](https://thegraph.com/docs/quick-start#faq)

#### `yarn subgraph:codegen`

Generates AssemblyScript types for smart contract ABIs and the subgraph schema.

#### `yarn subgraph:build`

Compiles the subgraph to WebAssembly.

#### `yarn subgraph:auth`

Before deploying your subgraph, you need to sign up on the
[Graph Explorer](https://thegraph.com/explorer/). There, you will be given an access token. Drop it in the command
below:

```sh
GRAPH_ACCESS_TOKEN=your-access-token-here yarn subgraph:auth
```

#### `yarn subgraph:deploy`

Deploys the subgraph to the official Graph Node.  
Replace `r1oga/channels-raiden` in the package.json script with your subgraph's name.  
You may also want to [read more about the hosted service](https://thegraph.com/docs/quick-start#hosted-service).

## Local Smart Contracts development
For development purposes, I had to be able to trigger events manually.
As I don't own any [CustomTokens]((https://goerli.etherscan.io/address/0x59105441977ecd9d805a4f5b060e34676f50f806)), I had to deploy my own contracts locally ([TokenNetwork](./packages/contracts/contracts/TokenNetwork.sol) and [SecretRegistry](./packages/contracts/contracts/SecretRegistry.sol)) and send transactions manually.  

In `packages/contracts`:
- ` yarn install`: will install OpenZeppelin SDK
- [commands](https://docs.openzeppelin.com/cli/2.8/commands):
  - `npx oz compile`: will compile contracts in [packages/contracts/contracts](./packages/contracts/contracts) and store ABIs in [/abis](./packages/contracts/src/abis)
  - `npx oz deploy`
  - `npx oz send-tx`

```
packages/contracts $ yarn install # will install OpenZeppeling SDK
packages/contracts $ npx oz compile # Compile contracts
```
## Ressources

- [Open Zeppelin SDK]https://openzeppelin.com/sdk/): the Ultimate Smart Contract Toolkit
- [Create Eth App](https://github.com/paulrberg/create-eth-app) by [PaulRBerg](https://github.com/paulrberg)
- [Rimble UI](https://rimble.consensys.design/): open-source React component library for dApps
- [Easy Peasy](https://easy-peasy.now.sh/): Vegetarian friendly state for React 
