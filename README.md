# SeleryAction
> OpenSelery Template for Simple Github Action Integration

[![](https://img.shields.io/gitter/room/protontypes/openselery)](https://gitter.im/protontypes/openselery)        
[![Actions Status](https://github.com/protontypes/seleryexample/workflows/openselery/badge.svg)](https://github.com/protontypes/seleryexample/actions) 
[![stability-experimental](https://img.shields.io/badge/stability-experimental-orange.svg)](https://github.com/emersion/stability-badges#experimental)
![Balance](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/wiki/protontypes/seleryexample/openselery/balance_badge.json&style=flat&logo=bitcoin)  ![Balance](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/wiki/protontypes/seleryexample/openselery/native_balance_badge.json&style=flat&logo=bitcoin)
[![Donate with bitcoin](https://badgen.net/badge/Donate/3PVdiyLPR7MgaeFRJLW9mfuESZS2aAPX9w/orange?icon=bitcoin)](https://raw.githubusercontent.com/wiki/protontypes/openselery/seleryaction/wallet_qrcode.png)  


A project template that is showing on how to integrated Bitcoin payouts with [OpenSelery](https://github.com/protontypes/openselery) into Github Action workflows:     

* Software defined developers payout fully transparent to the bones for your Github project.
* Fully customizeable payout weights.
* Transparent payout history.
* Dependencies scanning for most languages to include all developers. 	
* Only the sender needs an Coinbase account in the first instance.	
* Investor creates a transparent payout in your Project CI logs and Artifacts.	
* Payout will be triggered on merge after pull request. 

## Github Action Integration

1. The [Gitub](https://github.com/settings/tokens) and [Libraries.io](https://libraries.io/api) tokens are easy to obtain. Simulate payouts without the [coinbase token](https://www.coinbase.com/settings/api) to find the right settings. Set `include_dependencies = False for testing SeleryAction without a Libraries.io token.

2. Create a dedicated Coinbase account with limited amounts. OpenSelery is based on the APIs of The Libraries.io, Github and Coinbase. To provide service you need to create tokens in the corresponding accounts. Setting `simulation = false` will require your Coinbase tokens. Configure the [access control settings](https://github.com/protontypes/openselery/wiki/Coinbase-Settings) of the automated Coinbase account.

3. Never transfer or store large values with automated cryptocurrency wallets. Use [recurring automated buys](https://blog.coinbase.com/easier-recurring-buys-and-sells-on-coinbase-9a3cd7ea934e) to recharge you wallet on a regular base. 

4. Transfer some money to this wallet for testing. See the [price list](https://help.coinbase.com/en/coinbase/trading-and-funding/pricing-and-fees/fees.html) for transferring money to the Coinbase account.

5. Add the token of Libraries.io and Coinbase to your [secrets](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets). You run in simulation mode without the Coinbase token.

6. You can integrate OpenSelery in your CI by copying the `openselery.yml` file into your `.github/actions/` destination project directory. Check and modify the setting before running your CI Pipeline:

  ```
  cat .github/actions/openselery.yml 
  ```
7. Set the simulation parameter to `False` if you want pay developers or `True` to try out OpenSelery on your project.

8. Depending on the `openselery.yml` a payout will be triggered. The default setting runs OpenSelery with every new version of the destination project. 

9. Protect your master branch in the Github Setting under `Branches`. Activate the `Restrict who can push to matching branches` option. 

10. To enable runner diagnostic logging, set the following secret in the repository that contains the workflow.
This also changes the workflow behavior so that Github API calls are more stable:
```
ACTIONS_RUNNER_DEBUG to true. 
```
