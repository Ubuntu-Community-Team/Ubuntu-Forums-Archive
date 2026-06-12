---
title: "Software installation problem"
date: 2011-03-28
forum: General Help
---

### Post by Rohan Mallya on 2011-03-28
Hello,

I recently installed the Ubuntu 10.10 Os and my internet connection was not turned on. I relaised it was important for some downloads of language packs and all to take place. Please help me out on how to install the softwares now and also when i try to download W.I.N.E From the app store, it says the version is not suppourted for my computer.
My COmputer spec. are:

500 GB HDD drive+500 GB external HDD
2 GB RAM
1 gb graphic card

---

### Post by Dutch70 on 2011-03-28
You can install Wine and other programs from "Software Center".
I'm not on Ubuntu right now, but I believe it's under applications. 

You will need an Internet connection.

---

### Post by Omar11 on 2011-03-28
First thing: I don't have the netbook edition(I have the desktop) 2nd, You might need to buy a device for your laptop like a netbook adapter to get the internet connection (wirelessly) working.
3rd: To get wine(The windows program loader, not the drink), you first open a terminal and type in ```
sudo add-apt-repository ppa:ubuntu wine/ppa
``` And something like this should show up
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```
After that, type in ```
sudo spt-get update
```
after you press enter and a bunch of words show up... type in ```
sudo apt-get install wine1.3
```
or ```
sudo apt-get install wine1.2
```
the other way for wine is go to **Applications->Ubuntu Software Centre->Edit->Software sources->add->ppa:ubuntu-wine/ppa**
then click add source and go search wine in ubuntu software centre and download it.
[SIZE="4"]**WARNING**you might have to update by update manager for the second way to get wine at**System->Administration->update manager** and click check, and if something comes, if nothing comes, then install wine from ubuntu software centre, if something does come, then click update.[/SIZE] hope this helps! :)

---

### Post by Omar11 on 2011-03-28
this should work if I'm not wrong, I got wine the first way and it works well. (comes with Notepad! :D)

---

