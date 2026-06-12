---
title: "Wireless Management asks for password on startup"
date: 2009-09-16
forum: General Help
---

### Post by Slaskie on 2009-09-16
Every time I log in to Kubuntu, I get a message saying The application 'KDE Daemon' has requested to open the wallet 'kdewallet'. Please enter the password for this wallet below. (Screenshot attached) Without entering the password, Network Manager will not connect to my preferred wireless network. I would like the Network Manager to automatically connect and input the WEP key for my wireless network, instead of my having to enter my computer's password every time before it connects. How can I make my computer automatically connect without me having to enter my computer's password?

---

### Post by P4man on 2009-09-17
do you have autologin for KDe enabled? If you do, its normal that wallet asks your password. The only way to disable that, afaik, is either turning off auto login, or  setting an empty password on your wallet, but that will result in ALL passwords stored in the wallet to be in a plain, unencrypted text file, that anyone could read.

---

### Post by ianmillington on 2009-09-17
Unfortunately (as you will note from the kubuntu forum) the default network manager in Kubuntu does not work very well. The answer is simple.

Run sudo apt-get install wicd

This will remove network manager and install wicd which is far better. Hit alt+F2 and type wicd, select the icon and run it.

If you have wireless security, select your desired connection to reveal the advanced settings part, type in your password and you should be good to go. Done.

---

### Post by BjoernVDM on 2009-09-18
Been using Kubuntu for years now, just installed WICD. It is a much better NetworkManager and solves the headaches I had with the KDE Component.

Highly recommended for every KDE4 user.



Addition to above: you can of course install WICD with your favorite package manager too. KDE Networkmanagement packages will be deinstalled then. Also, personally I had to restart the computer for WICD to start working correctly. 

One more note, WPA/WEP Passwords are entered under "Advanced Settings" for a WLAN, accessed by pressing the tiny ">" Button next to the WLAN Name.

---

### Post by LaughingBubba on 2009-09-18
[solved]
I've always hated to effectively login TWICE just so's I can connect to my encrypted wireless network at home.

It means I can't leave my browser open when I shutdown, as when the desktop restarts along with my browser, it can't access the network until I've authenticated with the default wallet.  

BUT I've found a way around that particular problem :P

What you need to is :

- bring up the KDE Wallet Configuration window (right click on the wallet icon in the systray)

- enable the Different wallet for local passwords option and create a new wallet for local passwords (kdeconfig1)

- Then click on the access control tab and delete any networkmanager entries from the list (walletconfig2) and click ok

- Then you need to left click on the wallet icon in systray to bring up the wallet manager 

- click your default wallet (ie not the one you just created for locals) to view the password folders

- Then right on the network management folder and select the delete folder option

...

- Log out and back in again and when your desktop starts, network manager will ask you to open your wallet for _local_ passwords at which time you'll click on the 'allow always' button and thereafter ... voila! you will be automatically connected to your wireless network. (at least it worked for me)

NB: You still need to enter a password to access the other encrypted passwords in your default wallet, but at least you don't have to worry about network access.

Hope this helps.

Cheers

---

### Post by bergfly on 2010-08-07
We need mod points here, mainly to hand out to Laughingbubba. Thanks mate, that works a charm. Wish stuff like this was in the help files, because clearly the whole point of having a different local wallet was for things like this. Big up on  you for working it out.

---

