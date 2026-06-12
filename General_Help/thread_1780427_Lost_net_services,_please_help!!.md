---
title: "Lost net services, please help!!"
date: 2011-06-12
forum: General Help
---

### Post by Ubu4moi on 2011-06-12
Hi. I'm running 10.10 and I uninstalled some files through synaptic and it also removed a lot of other packages which messed up my whole system. I lost the connection to the Internet and also the taskbar. I don't know how to re-install those lost packages because I have no net connection. How can I fix this??
This is what I removed:

Completely removed the following packages:
apt-xapian-index
libboost-python-dev
python-xapian

Removed the following packages: (synaptic removed this on its own)
apport
apport-gtk
aptdaemon
apturl
apturl-common
command-not-found
computer-janitor
computer-janitor-gtk
gdebi
gdebi-core
gnome-codec-install
jockey-common
jockey-gtk
language-selector
language-selector-common
network-manager
network-manager-gnome
python-apport
python-apt
python-aptdaemon
python-aptdaemon-gtk
python-debian
python-software-properties
software-properties-gtk
ubuntu-dev-tools
ubuntu-system-service
unattended-upgrades
update-manager
update-manager-core
update-notifier
update-notifier-common
zeitgeist-fts-extension

Is there a way to re-build the installation or re-install the packages from a CD? Please help.

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **Ubu4moi said:**
> Hi. I uninstalled some files through synaptic and it also removed a lot of other packages which messed up my whole system. I lost the connection to the Internet and also the taskbar. I don't know how to re-install those lost packages because I have no net connection. How can I fix this??
This is what I removed:

Completely removed the following packages:
apt-xapian-index
libboost-python-dev
python-xapian

Removed the following packages: (synaptic removed this on its own)
apport
apport-gtk
aptdaemon
apturl
apturl-common
command-not-found
computer-janitor
computer-janitor-gtk
gdebi
gdebi-core
gnome-codec-install
jockey-common
jockey-gtk
language-selector
language-selector-common
network-manager
network-manager-gnome
python-apport
python-apt
python-aptdaemon
python-aptdaemon-gtk
python-debian
python-software-properties
software-properties-gtk
ubuntu-dev-tools
ubuntu-system-service
unattended-upgrades
update-manager
update-manager-core
update-notifier
update-notifier-common
zeitgeist-fts-extension

Please help.

Put the disc you used to install Ubuntu back into your drive, and open synaptic package manager.  

In terminal:

sudo synaptic

Settings >> Repositories >>  Click the checkbox "CD-Rom" to enable the disc.   >> hit reload.


Now go back to terminal and enter:

sudo apt-get install ubuntu-desktop

---

### Post by Ubu4moi on 2011-06-12
I updated to this version from 8.04. Would the lates version work? Because a have updated the system a few times.

---

### Post by Wim Sturkenboom on 2011-06-12
Does not look like you actually lost the 'net services'. So I would start with some googling to get the network up.

[linux network configuration command line](http://www.google.co.za/#hl=en&source=hp&q=linux+network+configuration+command+line&oq=linux+network+configuration&aq=2&aqi=g6g-v4&aql=&gs_sm=e&gs_upl=3288l8849l0l27l27l0l7l7l0l425l4009l4.7.6.2.1&fp=b83f38866210b3c7&biw=1280&bih=607)
[linux wifi configuration command line](http://www.google.co.za/#hl=en&q=linux+wifi+configuration+command+line&oq=linux+wifi+configuration+command+line&aq=f&aqi=&aql=&gs_sm=s&gs_upl=47216l51412l0l11l11l0l0l0l8l518l3368l0.4.2.0.3.2&fp=b83f38866210b3c7&biw=1280&bih=607)

There was a thread not to long ago here on ubuntuforums where someone posted instructions how to get the wifi going from the commandline but I can't find it back :(

How are you connected?
Can you post output of ifconfig and lspci (between [noparse]```
 and 
```[/noparse]) ?

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **Ubu4moi said:**
> I updated to this version from 8.04. Would the lates version work? Because a have updated the system a few times.

Is this a server?  Did you do a backup recently of your system?  Remastersys? Anything? 

Everyone has to have a rescue disc.  That's like a rule. Or should be. :) 

Here is a guide to get 10.10 on there, so you can resize that 8.04, install 10.10,  and do a data migration:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

8.04 isn't even supported anymore sadly.

---

### Post by Ubu4moi on 2011-06-12
I tried sudo apt-get install ubuntu-desktop but it tries to download. In synaptic I also lost a few features and repository only allows me to add web addresses. I added the cd in 'edit' but is not installing from the cd.

---

### Post by idoitprone on 2011-06-12
next time your in this situation. learn to connect to the internet with the command line




if it ethernet then all you have to is 
```
ifconfig eth0 up
dhcpcd eth0
```

i copy paste from my old post

```
ifconfig
```
make sure you wireless interface is up.
if not

```
ifconfig wlan0 up
```
I am using wlan0 since it a common wireless interface. Other may be wlan1 or ath0 or whatever.

```
iwlist wlan0 scan
```
find the your internet essid

Code:
```
iwconfig wlan0 essid "your essid" key "dawm if i know its a secret"
```
if your wifi is unprotected, you do not need to enter a key like me
if you have a wpa key, skip the iwconfig step and you will have to use wpa_supplicant instead
here is a link and it will get more annoying to set up since you have to edit files with the command line
[https://wiki.archlinux.org/index.php/WPA_supplicant](https://wiki.archlinux.org/index.php/WPA_supplicant)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)


```
dhcpcd wlan0

```
here some random links to show I am not insane lol
[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/https://bbs.archlinux.org/viewtopic.php?id=44784](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/https://bbs.archlinux.org/viewtopic.php?id=44784)
[http://www.linuxforums.org/forum/ubuntu-linux/126364-how-connect-wireless-network-ubuntu.htmlbtw](http://www.linuxforums.org/forum/ubuntu-linux/126364-how-connect-wireless-network-ubuntu.htmlbtw) dhclient and dhcpcd basically does the same thing

install packages manually

```
sudo apt-get install [packname]
```

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **Ubu4moi said:**
> I tried sudo apt-get install ubuntu-desktop but it tries to download. In synaptic I also lost a few features and repository only allows me to add web addresses. I added the cd in 'edit' but is not installing from the cd.
Did you disable the other repositories and use only the CD?

---

### Post by Ubu4moi on 2011-06-12
Nothing works. Looks like it's missing a lot of important files. Thanks for all the info. Maybe I will just install anew and copy all my files to the new installation.

---

### Post by Wim Sturkenboom on 2011-06-12
> **idoitprone said:**
> next time your in this situation. learn to connect to the internet with the command line
And the latter was the one that I was basically looking for ;)

Thanks

---

