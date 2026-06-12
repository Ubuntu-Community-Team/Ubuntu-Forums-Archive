---
title: "Black screen on boot [ gnome desktop , software center removed ]"
date: 2012-10-03
forum: General Help
---

### Post by hrgh on 2012-10-03
I had problem with software center that I couldn't install any app (* the app not found in your source )
so I decided to reinstall software center to reset software source to my default Iran server which I already missed from list
I force uninstalled using force purge command software center and it unistalled software center and gnome desktop  and other packages
Then I tried to install deepin software center 
```
sudo add-apt-repository ppa:noobslab/deepin-sc
sudo apt-get update
sudo apt-get install deepin-software-center
```and installed but when I tried to run it, nothing happend and it was about all softwares no software opened even terminal
I did restart my pc and now it show me a black screen on ubuntu login screen seems problem with xorg
I couldnt recover it because I hav no network in command line in recovery mode boot ubuntu ( my net connects using Android tethering which dont works in command line )
plz somebody help me

---

### Post by cway00 on 2012-10-03
> **hrgh said:**
> I had problem with software center that I couldn't install any app (* the app not found in your source )
so I decided to reinstall software center to reset software source to my default Iran server which I already missed from list
I force uninstalled using force purge command software center and it unistalled software center and gnome desktop  and other packages
Then I tried to install deepin software center 
```
sudo add-apt-repository ppa:noobslab/deepin-sc
sudo apt-get update
sudo apt-get install deepin-software-center
```and installed but when I tried to run it, nothing happend and it was about all softwares no software opened even terminal
I did restart my pc and now it show me a black screen on ubuntu login screen seems problem with xorg
I couldnt recover it because I hav no network in command line in recovery mode boot ubuntu ( my net connects using Android tethering which dont works in command line )
plz somebody help me

following the guide in the link below to solve this issue
 ```
http://ubuntuforums.org/showthread.php?t=2065784
```
and if it does not work try this 
```
http://ubuntuforums.org/showthread.php?t=2065847
```
especially the second guide ..

---

### Post by ajgreeny on 2012-10-03
I am assuming that this is a ubuntu installation on partitions, not installed using the windows installer wubi.

Login If you can at the black screen you see when you start up the computer by typing your username, hitting enter, then typing your password, which will not show on screen.

Once logged in under your username, use the command ```
sudo apt-get install ubuntu-desktop
``` (or xubuntu-desktop, lubuntu-desktop, kubuntu-desktop, if it is really one of those.)  That will add back everything now missing that was installed originally and may solve your problem.

---

### Post by hrgh on 2012-10-03
```
following the guide in the link below to solve this issue
```
no one of these links were about my problem therer s no problem with grub when I choose ubuntu It shows me login screen less than 1 second then black screen :(

[ajgreeny]("http://ubuntuforums.org/member.php?u=27747")
there is no way to access command line but using recovery mode in grub boot and choosing
 root     Drop to root shell
I loged in as root and used your command 
sudo apt-get install ubuntu-desktop
and it says :
```
Not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt
...
```

In the recover mode screen there is a sentence which says Read only mode:(

and other problem for fixing package is no network problem as I said I hav android tethering network which is unavailable in recovery mode ( Network is unreachable ):(

---

### Post by cway00 on 2012-10-03
> **hrgh said:**
> ```
following the guide in the link below to solve this issue
```no one of these links were about my problem therer s no problem with grub when I choose ubuntu It shows me login screen less than 1 second then black screen :(

[ajgreeny]("http://ubuntuforums.org/member.php?u=27747")
there is no way to access command line but using recovery mode in grub boot and choosing
 root     Drop to root shell
I loged in as root and used your command 
sudo apt-get install ubuntu-desktop
and it says :
```
Not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt
...
```In the recover mode screen there is a sentence which says Read only mode:(

and other problem for fixing package is no network problem as I said I hav android tethering network which is unavailable in recovery mode ( Network is unreachable ):(

Seems like your harddisk is failing ..try doing a disk diagnostics or replace harddisk if hard disk is old

---

### Post by hrgh on 2012-10-03
no problem with harddisk
I have windows on it and works fine
I think problem is missing gnome desktop which I removed it
Or maybe with deepin software center

---

### Post by hrgh on 2012-10-03
I used clean option in recovery menu and it mounted everything
I used 
Sudo apt-get ubuntu-desktop
and it want to download packages 
but
now problem is with network I don't know how to enable it ( Android tethering in command line )

---

### Post by raja.genupula on 2012-10-03
> **hrgh said:**
> ```
following the guide in the link below to solve this issue
```no one of these links were about my problem therer s no problem with grub when I choose ubuntu It shows me login screen less than 1 second then black screen :(

[ajgreeny]("http://ubuntuforums.org/member.php?u=27747")
there is no way to access command line but using recovery mode in grub boot and choosing
 root     Drop to root shell
I loged in as root and used your command 
sudo apt-get install ubuntu-desktop
and it says :
```
Not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt
...
```In the recover mode screen there is a sentence which says Read only mode:(

and other problem for fixing package is no network problem as I said I hav android tethering network which is unavailable in recovery mode ( Network is unreachable ):(

When you have stopped apt-get in middle then you will get things like this 

```
sudo rm -rf /var/lib/dpkg/lock
```

will do fine .

---

### Post by hrgh on 2012-10-03
Using following steps I installed ubuntu desktop and software center but I have still black screen problem
1. mounting hdd using clean option in recovery mode
2. drop to root shell
3. enabling usb tethering for network
dhclient usb0
4.sudo apt-get install software center
5.sudo apt-get install ubuntu-desktop

but same problem black screen
What's problem here ? :-(

---

### Post by hrgh on 2012-10-03
if somebody try to unistall software center from synaptic software center or terminal and tells me all the packages names will unistall it can help me to fix problem

I want u to just tryin it for me ( not really remove software center )

---

### Post by raja.genupula on 2012-10-03
> **hrgh said:**
> if somebody try to unistall software center from synaptic software center or terminal and tells me all the packages names will unistall it can help me to fix problem

I want u to just tryin it for me ( not really remove software center )


```
raja@badfox:~/Documents$ sudo apt-get remove software-center
[sudo] password for raja: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following packages will be REMOVED:
  software-center ubuntu-desktop[/B]
0 upgraded, 0 newly installed, 2 to remove and 16 not upgraded.
After this operation, 4,417 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by hrgh on 2012-10-03
thanks man :-* 
both installed but same problem :-(

---

### Post by cway00 on 2012-10-03
> **hrgh said:**
> thanks man :-* 
both installed but same problem :-(

Try these steps


 1. LiveCD  boots into a blank screen.
 When you see the boot menu when you boot LiveCD, hit F6 and select the “nomodeset” option.


 2. Boots into a blank screen after install.
 Reboot and keep your finger on the “SHIFT” key till you get the grub  menu. Highlight the first entry and replace “quiet splash” with  “nomodeset” .  Hit CTRL + X to continue booting. Once logged in install  the latest Graphics drivers. *System -> Administration -> Additional Drivers*


[I]hope this works
[/I]

---

### Post by hrgh on 2012-10-04
> **cway00 said:**
> Try these steps


 1. LiveCD  boots into a blank screen.
 When you see the boot menu when you boot LiveCD, hit F6 and select the “nomodeset” option.


 2. Boots into a blank screen after install.
 Reboot and keep your finger on the “SHIFT” key till you get the grub  menu. Highlight the first entry and replace “quiet splash” with  “nomodeset” .  Hit CTRL + X to continue booting. Once logged in install  the latest Graphics drivers. *System -> Administration -> Additional Drivers*


[I]hope this works
[/I]

thanks
I reinstalled nvidia-current and many other packages
once it showed a text in boot , 
could not write bytes...
checking battery status....

I fixed it
but still monitor turns off and on in before login screen it shows mouse pointer for a while and again black screen 
it blinks
:-(

---

### Post by hrgh on 2012-10-05
any solution ?

---

### Post by cway00 on 2012-10-06
> **hrgh said:**
> any solution ?

try booting from the First CD before directl installing it on your computer s that you might get acquinted to the process of tweaking Ubuntu ..If it thus boots ..then you will know how to start solving your problem

---

