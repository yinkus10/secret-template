# Secret Contracts Starter Pack

This is a template to build secret contracts in Rust to run in
[Secret Network](https://github.com/enigmampc/SecretNetwork).
To understand the framework better, please read the overview in the
[cosmwasm repo](https://github.com/CosmWasm/cosmwasm/blob/master/README.md),
and dig into the [cosmwasm docs](https://www.cosmwasm.com).
This assumes you understand the theory and just want to get coding.

## Creating a new repo from template

Assuming you have a recent version of rust and cargo installed (via [rustup](https://rustup.rs/)),
then the following should get you a new repo to start a contract:

First, install
[cargo-generate](https://github.com/ashleygwilliams/cargo-generate).
Unless you did that before, run this line now:

```sh
cargo install cargo-generate --features vendored-openssl
```

Now, use it to create your new contract.
Go to the folder in which you want to place it and run:

```sh
cargo generate --git https://github.com/enigmampc/secret-template.git --name YOUR_NAME_HERE
```

You will now have a new folder called `YOUR_NAME_HERE` (I hope you changed that to something else)
containing a simple working contract and build system that you can customize.

Don't forget to change the `name` and the `authors` fields in the `Cargo.toml` file.

## Create a Repo

After generating, you have a initialized local git repo, but no commits, and no remote.
Go to a server (eg. github) and create a new upstream repo (called `YOUR-GIT-URL` below).
Then run the following:

```sh
# this is needed to create a valid Cargo.lock file (see below)
cargo check
git checkout -b master # in case you generate from non-master
git add .
git commit -m 'Initial Commit'
git remote add origin YOUR-GIT-URL
git push -u origin master
```

## Using your project

Once you have your custom repo, you should check out [Developing](./Developing.md) to explain
more on how to run tests and develop code. Or go through the
[online tutorial](https://www.cosmwasm.com/docs/getting-started/intro) to get a better feel
of how to develop.

[Publishing](./Publishing.md) contains useful information on how to publish your contract
to the world, once you are ready to deploy it on a running blockchain. And
[Importing](./Importing.md) contains information about pulling in other contracts or crates
that have been published.

You can also find lots of useful recipes in the `Makefile` which you can use
if you have `make` installed (very recommended. at least check them out).

Please replace this README file with information about your specific project. You can keep
the `Developing.md` and `Publishing.md` files as useful referenced, but please set some
proper description in the README.

## Gitpod

Can't run your local secret environment because you're on M1, or too lazy to install docker? We got your back!

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/scrtlabs/GitpodLocalSecret)

### Usage

The environment will automatically start with localsecret, and it exposes the ports for application development.
Specifically -

* 26657 - RPC
* 1317 - LCD/Rest Gateway
* 9090 - GRPC
* 9091 - GRPC-Web
* 5000 - LocalSecret faucet

To connect, prepend the port number with the gitpod url. e.g. if my workspace is at `https://scrtlabs-gitpoddevenv-shqyv12iyrv.ws-eu54.gitpod.io` then I would be able
to connect to the LCD service at `https://1317-scrtlabs-gitpoddevenv-shqyv12iyrv.ws-eu54.gitpod.io`.

To configure SecretCLI you'll want to use:
```
secretcli config node `https://26657-scrtlabs-gitpoddevenv-your-workspace-url.gitpod.io`
secretcli config chain-id secret-testnet-1
```

We also recommend for ease of use while testing
```
secretcli config keyring-backend test
secretcli config output json
```

This environment also comes with all the dependencies you need to develop Secret Contracts, and SecretCLI.

To make the most out of the environment, you can switch between two views:

* LocalSecret will provide the logs from the running secretd node, which can be helpful when testing and debugging contracts.
* Terminal can allow you to execute secretcli commands or clone a repository.

Switching between the views can be done here:

![image](https://user-images.githubusercontent.com/16579705/182580806-f43563ed-ab36-4403-89b3-435d7e7fc4da.png)