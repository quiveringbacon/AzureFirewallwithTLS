# Azure Firewall with TLS inspection

This creates a resource group, a hub vnet with an Azure firewall with TLS inspection enabled and a spoke vnet peered to the hub vnet. This creates a log analytics workspace and diagnostic settings for the firewall logs. Also creates Windows VM's in all those subnets with your public ip added to an NSG allowing RDP access. UDR's are in place routing all traffic to the firewall except for your public ip to allow RDP access directly to the VM's. NSG's are placed on the default subnets of each vnet allowing RDP access from your public ip. A keyvault is created and self-signed certificates are generated and put in the keyvault for the firewall to use and installed on the VM's. This also creates a logic app that will delete the resource group in 24hrs. You'll be prompted for the resource group name, location where you want the resources created, your public ip and username and password to use for the VM's.

The topology will look like this:
![image](https://github.com/quiveringbacon/AzureFirewallwithTLS/assets/128983862/8056ef32-5b92-4fc2-a4eb-3d0e51166b27)

You can run Terraform right from the Azure cloud shell by cloning this git repository with "git clone https://github.com/quiveringbacon/AzureVPNwithFW.git ./terraform".

Then, "cd terraform" then, "terraform init" and finally "terraform apply -auto-approve" to deploy.
