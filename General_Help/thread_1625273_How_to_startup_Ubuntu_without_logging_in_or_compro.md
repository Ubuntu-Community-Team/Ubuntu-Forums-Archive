---
title: "How to startup Ubuntu without logging in or compromising security"
date: 2010-11-18
forum: General Help
---

### Post by GregoryMA on 2010-11-18
There are many posts out there complaining about the so-called bug which happens when you set Ubuntu (running Gnome) to login automatically and you are prompted to unlock the keyring.  This is not a bug but rather a security feature.  It is prompted by Network Manager.  It is possible to stop this by disabling the keyring and I have found many posts explaining how to do this, however, this is hardly an ideal solution.  This post explains how to startup Ubuntu without being prompted to login or unlock the keyring and without disabling the keyring.

First, it is necessary to set your computer to login automatically.  Go to System->Administration->Login Screen.  Click Unlock and give your password when prompted.  Select "Log in as <username> automatically", making sure that <username> is the account you want the computer to login automatically to.

After you have done this your computer should automatically login but Network Manager will now demand that the keyring be unlocked.  To get around this you need to edit the network connections.  This needs to be done for each network which you want to allow Network Manager to connect to without authentication individually.  Click System->Preferences->Network Connections (or right-click on the Network Manager icon in the panel and select Edit Connections).  Go to the Wireless tab and select the network which you want to allow Network Manager to connect to without authentication.  Now click Edit.  You will then be prompted to give your password.  Once you do a new window will open.  At the bottom of the window there is a button called "Available to all users".  Select this button and click Apply.  Now when you startup and Network Manager connects to this network it will not prompt you to unlock the keyring.  Repeat this process for any network you want to automatically login to.

---

