# Ducat
Shell script to install a [Ducat Masternode](https://www.ducatcoin.io/) on a Linux server running Ubuntu 16.04. Use it on your own risk.
***

## Installation
```
wget -N https://raw.githubusercontent.com/zoldur/Ducat/master/ducat_install.sh
bash ducat_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:
1. Open the Ducat Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **3500** DC to **MN1**. You need to send all 3500 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**
6. Type the following command: **masternode outputs**
7. Go to **Masternodes** tab
8. Click **Create** and fill the details:
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
* Reward address: leave blank
* Reward %: leave blank
9. Click **OK** to add the masternode
11. Close and open the wallet again.
12. Go to **Masternodes** -> **My Master Nodes** tab
13. If you don't see your masternode, click **Update**
14. Unlock your wallet if it is encrypted
15. Select your masternode and click on **Start**
16. Login to your VPS and check your masternode status by running the following command. If you get **Status 9**, it means your masternode is active.
```
ducatd masternode status
```
***

## Usage:
```
ducatd masternode status
ducatd getinfo
```
Also, if you want to check/start/stop **Ducat**, run one of the following commands as **root**:

```
systemctl status Ducat #To check if Ducat service is running
systemctl start Ducat #To start Ducat service
systemctl stop Ducat #To stop Ducat service
systemctl is-enabled Ducat #To check if Ducat service is enabled on boot
```
***

## Running multile nodes on the same server:

As it takes, run the script and follow the instructions:
```
wget -N https://raw.githubusercontent.com/zoldur/Ducat/master/ducat_add.sh
chmod +x ducat_add.sh
./ducat_add.sh mn2
```
***

## Masternode update:
In order to update your Ducat Masternode to version 1.1.2, please run the following commands:
```
cd /tmp
wget -N https://github.com/zoldur/Ducat/releases/download/v1.1.2.0/ducat.tar.gz
tar xvzf ducat.tar.gz
systemctl stop Ducat
mv ducatd /usr/local/bin
systemctl start Ducat
ducatd getinfo
```
Open your desktop wallet and restart your node(s).
***

## Donations

Any donation is highly appreciated

**BTC**: 3MQLEcHXVvxpmwbB811qiC1c6g21ZKa7Jh
**ETH**: 0x26B9dDa0616FE0759273D651e77Fe7dd7751E01E
**LTC**: LNZpK4rCd1JVSB3rGKTAnTkudV9So9zexB
