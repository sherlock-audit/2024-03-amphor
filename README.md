
# Amphor contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
mainnet and polygon zkEVM
___

### Q: Which ERC20 tokens do you expect will interact with the smart contracts? 
weth, usdc, usdt, wbtc
___

### Q: Which ERC721 tokens do you expect will interact with the smart contracts? 
none
___

### Q: Do you plan to support ERC1155?
no
___

### Q: Which ERC777 tokens do you expect will interact with the smart contracts? 
none
___

### Q: Are there any FEE-ON-TRANSFER tokens interacting with the smart contracts?

no
___

### Q: Are there any REBASING tokens interacting with the smart contracts?

no
___

### Q: Are the admins of the protocols your contracts integrate with (if any) TRUSTED or RESTRICTED?
TRUSTED
___

### Q: Is the admin/owner of the protocol/contracts TRUSTED or RESTRICTED?
TRUSTED
___

### Q: Are there any additional protocol roles? If yes, please explain in detail:
only owner role for vault and zapper: 
- can pause/unpause contract, open/close/settle vault,
- setFees, setMaxDrawdown


 add remove vault and router to zapper, withdraw tokens lost in the contract
 


___

### Q: Is the code/contract expected to comply with any EIPs? Are there specific assumptions around adhering to those EIPs that Watsons should be aware of?
EIP4626
EIP7540 (partially) see https://ethereum-magicians.org/t/eip-7540-asynchronous-erc-4626-tokenized-vaults/16153/15
We settle the requestDeposit/redeem ourself during the open/settle functions and we let users claim there shares/assets using a claimDeposit, claimRedeem functions instead of deposit/redeem
EIP165
___

### Q: Please list any known issues/acceptable risks that should not result in a valid finding.
We will boostrap the vault to avoid inflation attack so please take this into consideration. 
For weth vault it would be 1 weth.
For usdc vault it would be 1000 usdc.

___

### Q: Please provide links to previous audits (if any).
Only for the first version of our contracts so:
- without the requestDeposit/requestRedeem

https://github.com/AmphorProtocol/synthetic-private/blob/main/audits/Bailsec_final_report.pdf
https://github.com/AmphorProtocol/synthetic-private/blob/main/audits/Salus_final_report.pdf
___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, input validation expectations, etc)?
For the zapper, we get quote through an api call to 1inch.
___

### Q: In case of external protocol integrations, are the risks of external contracts pausing or executing an emergency withdrawal acceptable? If not, Watsons will submit issues related to these situations that can harm your protocol's functionality.
No
___

### Q: Do you expect to use any of the following tokens with non-standard behaviour with the smart contracts?
non
___

### Q: Add links to relevant protocol resources
currently only for first version of our contracts but will be updated in the next following days: https://defivaults.gitbook.io/amphor
___



# Audit scope


[asynchronous-vault @ c4f7a9b8f3d3d9aba0e43eaae38ef9b556023b0e](https://github.com/AmphorProtocol/asynchronous-vault/tree/c4f7a9b8f3d3d9aba0e43eaae38ef9b556023b0e)
- [asynchronous-vault/src/AsyncSynthVault.sol](asynchronous-vault/src/AsyncSynthVault.sol)
- [asynchronous-vault/src/SyncSynthVault.sol](asynchronous-vault/src/SyncSynthVault.sol)
- [asynchronous-vault/src/VaultZapper.sol](asynchronous-vault/src/VaultZapper.sol)
- [asynchronous-vault/src/interfaces/ERC7540Receiver.sol](asynchronous-vault/src/interfaces/ERC7540Receiver.sol)
- [asynchronous-vault/src/interfaces/IERC165.sol](asynchronous-vault/src/interfaces/IERC165.sol)
- [asynchronous-vault/src/interfaces/IERC7540.sol](asynchronous-vault/src/interfaces/IERC7540.sol)


