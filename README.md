# CraneChat (demo-chat)

An E2E encrypted chat with token gated group chats built on Oasis Sapphire with ROFL.

**!! Disclaimer !!**
This is a demo application and should not be used in production.

## How It Works

CraneChat is a decentralized chat application that provides:

*   **Token Gated Group Chats:** Create groups that require members to hold specific token amounts on supported chains to join.
*   **Direct Messaging:** Send encrypted messages directly to other users.
*   **E2E Encryption:** All messages are encrypted using Oasis Sapphire's confidential smart contracts.
*   **ROFL Integration:** Automated token balance verification using ROFL (Remote Offchain Fault-tolerant Logic).

The application consists of:

*   Smart contracts deployed on Oasis Sapphire.
*   A ROFL application for off-chain token balance verification (see details on the Price Oracle Prototype below).
*   A Next.js frontend with Wagmi for web3 integration.

## Directory Structure

*   `/` (root): Smart contracts (Hardhat project)
*   `app/`: Next.js frontend
*   `rofl/`: Contains the ROFL application components. The Price Oracle Prototype described below is an example of such a component.

## ROFL Integration: Price Oracle Prototype Example

CraneChat leverages ROFL for critical off-chain computations, like token balance verification. The following describes a ROFL Price Oracle prototype that showcases the capabilities and features of ROFL applications that can be built and integrated. This prototype can serve as a reference or a foundational component.

This prototype implements a comprehensive price oracle with the following features:

*   **Configuration Management:** Supports environment variables and CLI arguments.
*   **CoinGecko API Client:** Includes error handling and validation for reliable data fetching.
*   **Data Parsing:** Robust JSON parsing with price validation logic.
*   **Sapphire Interaction:** Handles full transaction signing and submission to the Oasis Sapphire network.
*   **Main Loop/Scheduler:** Allows for configurable intervals for price updates.
*   **Logging:** Comprehensive logging throughout the application.

### Key Advantages of the ROFL Price Oracle Prototype

*   **Speed & Ease of Use:**
    *   **One command setup:** `./quick-start.sh` (detailed below).
    *   **Docker support:** `make docker-run`.
    *   **Built-in verification:** `--verify-only` flag.
    *   **Environment-based config:** No hardcoded values.
*   **Production-Ready Features:**
    *   Comprehensive error handling.
    *   Gas estimation with buffer.
    *   Transaction confirmation waiting.
    *   Connection verification.
    *   Wallet balance checking.
    *   Price validation (sanity checks).
*   **Developer Experience:**
    *   Full test suite included.
    *   CLI interface with help.
    *   Makefile for common tasks.
    *   Docker containerization.
    *   Monitoring setup (Grafana).

### ROFL Price Oracle: Quick Start (3 steps)

These steps are for setting up and running the standalone Price Oracle prototype.

1.  **Initialize Project:** Copy the prototype files into your desired directory (e.g., `rofl/price-oracle/`) and run `cargo init` within that directory.
2.  **Configure Environment:** Create a `.env` file (you can copy from a `.env.template` if provided with the prototype) and fill in your contract address and private key.
3.  **Run:** Execute `./quick-start.sh`. This script typically handles dependency installation, compilation, and running the oracle.

### Technical Highlights of the Price Oracle Prototype

*   **Pre-built contract ABI:** No need to generate during setup.
*   **Ethers.rs integration:** Utilizes a production-ready Ethereum client library.
*   **Automatic gas estimation:** Simplifies deployment and operation.
*   **Built-in monitoring:** Provides insights into the oracle's activity.
*   **Docker deployment:** Enables easy deployment across different environments.

This Price Oracle prototype provides a solid, tested foundation for interacting with APIs, managing transactions, and handling errors, which can accelerate the development of ROFL-based components for projects like CraneChat.

## CraneChat Application Setup

### Install dependencies:

```bash
pnpm install
cd app
pnpm install
```

### Configure environment variables:

```bash
cp .env.template .env
```
(And fill in the necessary values in `.env`)

## Running CraneChat

### Start the frontend development server:

```bash
cd app
pnpm dev
```

### For local ROFL development (specific to CraneChat's own ROFL logic):

If CraneChat's integrated ROFL application (potentially distinct from or simpler than the Price Oracle prototype) has its own setup, refer to `rofl/README.md` for instructions on running that specific service.

### Deploy contracts:

```bash
npx hardhat deploy --network sapphire-localnet
```

### To populate test groups (optional):

```bash
npx hardhat populate --network sapphire-localnet --contract <CONTRACT_ADDRESS>
```

## About CraneChat

An E2E encrypted chat with token gated group chats built on Oasis Sapphire with ROFL.

## Topics

demo, ethereum, dapp, blockchain, evm, oasis, sapphire, rofl, metamask, web3, chat, price-oracle
