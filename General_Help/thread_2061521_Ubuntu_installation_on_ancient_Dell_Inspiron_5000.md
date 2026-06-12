---
title: "Ubuntu installation on ancient Dell Inspiron 5000"
date: 2012-09-22
forum: General Help
---

### Post by dragonfly41 on 2012-09-22
Following failure of a family Acer laptop (it didn't survive usage by kids)  I'd like to bring an ancient but robust Dell Inspiron 5000 notebook out of retirement for educational use.   Edubuntu is the preferred distro.

Currently the Dell notebook has Windows Server 2000 and Windows 2000 Professional Client installed on different partitions with a couple of other data partitions.  So I hope that it has enough steam power to take Edubuntu.  I would clear out the windows software.   Possibly adding a different (larger) drive if the notebook will take it (current drive is  only 10 GB).

One problem is that internet port connection is through Xircom cardbus.

What flavour of Ubuntu / Edubuntu should I try?

And is there a Ubuntu driver for Xircom Cardbus Ethernet II 10/100 for network connection?

---

### Post by jerrrys on 2012-09-22
Got some hits [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Xircom+Cardbus&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") on xircom

---

### Post by sienile on 2012-09-22
Isn't Edubuntu its own variant?

As far as the driver... Xircom does not make Linux drivers, but they link to a [sourceforge project]("http://pcmcia-cs.sourceforge.net/") that may support your card. Only problem is the project says it only supports 2.4 and older kernels. I found this model numbers on the list: *Xircom CBE2-100BTX, RBE-100BTX, R2BE-100BTX*. CBE2-100 is the model of the card you listed... not sure if CBE2-100BTX is compatible or not.

I found a post on another forum asking for help with the card, but mentioning how he got it running. Hope it helps. Points of interest in bold.
> I have RH7.0+updates running on a DELL Inspiron 3800 notebook. 
As the networking card I have Xircom 10/100 CBE2-100 networking 
card (no modem). The card is recognized by linux and it actually 
works (uses **tulip_cb driver**) BUT when trasferring files it becomes 
extremely slow. I substitute the PCMCIA card with a 3Com card and 
it is blazingly fast. I read about problems with Xircom cards but 
could not find a solution. I ported the **pcmcia-3.1.22 package** and 
started using that but that did not solve the problem either. Any 
suggestions would be appreciated. 

---

### Post by dragonfly41 on 2012-09-23
Thanks for the information.  My tests so far ..

[LIST]
[*]Ubuntu 10.10 live CD does _not_ run on the notebook.
[/LIST]

[LIST]
[*]Puppy 5.2.8 live CD does run .. but without connection through Xircom CBE2-100.
[/LIST]

[LIST]
[*]Lubuntu 12.04 live CD does run .. but without connection through Xircom  CBE2-100.
[/LIST]
Although Xircom does not have linux drivers, in  Puppy 5.2.8 network wizard - when trying to set up network connection - two options are given:

eth0 and windows

eth0 - reports:

[COLOR=Blue]interface: eth0
type: wired
driver: xircom_cb
bus: pci[/COLOR]

But no internet connection was made.
The network wizard optionally asks for windows drivers and refers to "ndiswrapper" which led me to look up this site ..

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php)

but no hits for xircom at all.

I have found the windows download for Xircom CBE2-100 adapter.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=&DwnldID=3231&ProductID=851](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=&DwnldID=3231&ProductID=851)

I'll keep trying.  The last hurdle is establishing network connection.  
Unfortunately in this old notebook the only port  is via Xircom CB2-100 Ethernet adapter.

---

### Post by dragonfly41 on 2012-09-25
I've tried installing Lubuntu-12.04-desktop-i386.iso on my old Dell Inspiron 5000e - a notebook mentioned above.

Firstly I tried Lubuntu 12.04 Live CD and that seemed to work ok. although the notebook has low memory - 300 MB.   I will increase this later if I find suitable memory cards.

Lubuntu 12.04 worked - other than my Xircom adapter  not making internet connection.   I'm hoping to solve that problem separately with an upgraded NetworkManager (discussed in another thread). Apparently carrier is not detected by early NetworkManager (0.8.1).

I started the installation by choosing the option to upgrade existing Ubuntu 10.10 installation in a internal dual boot disk which I had installed:-

/dev/sda5 ---- root partition
/dev/sda5 ---- home partition

Near the end of the Lubuntu installation a message popped up "disconnected, you are now offline" and shortly after another message "system program problem detected".

The symptoms seen were a bit odd.   A rotating (loading) icon followed the mouse cursor around the screen and acted as a drawing pen leaving ghost trail on the screen - as though a sketch pad as the mouse cursor moves around.

I was able to use keyboard to launch programs such as leafpad and get into terminal and launch sudo commands etc..   But the installed os cannot be used in this state.

I did note that when starting the Lubuntu installation there was an early reference on the screen to Lubuntu ... "ubuntu generic i686".   Since I'm using the Lubuntu i386 distro why is there reference to i686?

Is Lubuntu 12.04 suitable for use on this old (but rugged) notebook?

If I now use Lubuntu 12.04 Live CD to inspect the installed (but not working) os what system log files should I pull out to find what is this "system program problem detected"?

---

### Post by dragonfly41 on 2012-09-26
Concluding ...

I successfully installed Ubuntu 11.04 which detected the reduced hardware spec and fell back to classic mode .. but still worked.

No internet connection was detected at the beginning of installation where the three prerequisites are listed.[INDENT]has at least 4.4 GB
is plugged into power
is connected to internet
[/INDENT]I put this down to the xircom adapter and carried on with installation.

When I rebooted the desktop was working but no internet connection.

Next I followed the advice here .. 

[http://ubuntuforums.org/showthread.php?t=1981329](http://ubuntuforums.org/showthread.php?t=1981329)

particularly AnnMartin's posts #3 and #4

> I think the root-cause might be, that maybe the XIRCOM-Driver does not support "carrier detection" which seems to be required by NetWork Manager 0.9.4 (see [https://bugzilla.redhat.com/show_bug.cgi?id=816719](https://bugzilla.redhat.com/show_bug.cgi?id=816719) which also shows the same error-messages: NetworkManager[838]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
NetworkManager[838]: <warn> (p5p1): couldn't get carrier state: (-1) unknown))Referred to this advice ..

[http://www.liberiangeek.net/2010/08/disable-network-manager-ubuntu-10-04-lucid-lynx-configure-network-interface-traditionally/](http://www.liberiangeek.net/2010/08/disable-network-manager-ubuntu-10-04-lucid-lynx-configure-network-interface-traditionally/)

I manually setup connection, rebooted and this worked.

------------------------------------------------------

The conclusion I now note is that xircom does need manual network configuration .. bypassing NetworkManager.

This manual setup of network connection does not work in Live CD mode (because there is no persistence of network configuration files) and required a full installation of Ubuntu and then edit of network configuration files.

I booted up another working laptop (without xircom) to grab the actual network configuration settings to place in the Dell notebook configuration files.

[https://help.ubuntu.com/8.04/serverguide/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/network-configuration.html)

---

