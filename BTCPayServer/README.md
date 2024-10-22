## Install BTCPayServer on the RaspiBlitz

Run BTCPayServer on your RaspiBlitz using the already synced bitcoin blockchain and local LND node.
Benefit from the backup and security features of the RaspiBlitz and LND.  
No added synchronization is needed. 

Requirements:
* a domain name or dynamic DNS
* the ports 80, 443 and 9735 forwarded on the router to the RaspiBlitz LAN IP

Tested on:
* RaspiBlitz v1.3 
* RPi4 4GB (2GB RAM is sufficient)

### [Automated Script](https://github.com/openoms/bitcoin-tutorials/blob/master/BTCPayServer/btcpay_to_blitz.sh)

The BTCPay Server installation will be part of the next RaspiBlitz release.
To try it on your node follow the instructions: 
https://github.com/openoms/raspiblitz-extras#test-the-functions-coming-to-the-next-release

* BTCpayServer, NBXplorer and the .NET Core is confined to the user `btcpay`.
* The BTCPay data and store settings are stored on the HDD `/mnt/hdd/.btcpayserver` and recoverable on a reinstall / SDcard update.
* Sets up a Tor Hidden Service if Tor is active
* Gives an option to use only the Tor Hidden Service and a self-signed certificate to be used without a clearnet domain
* to change the BTCpay domain or update run the most recent script again

### Setting up BTCPayServer

* Go to your domain
* Register the first (administrator) account
* Create a Store
* In Store settings set up the derivation scheme (add an xpub from a secure/hardware wallet)
* Set up LN with the connection string:  
 `type=lnd-rest;server=https://127.0.0.1:8080/;macaroonfilepath=/home/btcpay/admin.macaroon;allowinsecure=true`

* Find more detailed info on https://docs.btcpayserver.org/getting-started/

---

### Getting help

The setup has multiple components and dependencies which can change when updated or modified by the maintainers.

* see the original guide this is based on: <https://gist.github.com/normandmickey/3f10fc077d15345fb469034e3697d0d0>  

* shared experiences: <https://github.com/rootzoll/raspiblitz/issues/214>

* if `Nginx` breaks:
`sudo nginx -t`
is a very useful debug tool. Runs a test and displays detailed info on which line in the configuration is problematic.

* Try to run the commands manually one-by-one, spot which is causing the problem and copy the output

* Open an issue [here](https://github.com/openoms/bitcoin-tutorials/issues) with the details of your harware and software environment (SBC model, RaspiBlitz version) and I will be happy to help to solve it.

* Join the BTCPay Server Community Chat on <https://chat.btcpayserver.org/>
