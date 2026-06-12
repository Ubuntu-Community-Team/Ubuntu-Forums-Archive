---
title: "Wireless Internet connectivity help"
date: 2006-03-18
forum: General Help
---

### Post by michaeljoe on 2006-03-18
Hi. I’m a newbie to Linux.  I’ve got Breezy 5.10 installed.  Now I’m trying to connect to internet.  I’ve done a lot of research on the forums here but haven’t been able to resolve this.  Hopefully someone can help.  I’d really like to ditch Windows!  Here’s my setup.

Primary PC is running Win XP, DSL with a Netgear wireless router. 

Secondary PC is running Win XP as well.  I’m connected to internet via a Netgear WG111 USB wireless adapter.  That setup runs fine.

So,  I installed Breezy on the secondary machine on another partition.  During installation a message indicating an issue with DHCP came up.  I elected to “setup network later”.  After some poking around in Breezy, I found some Network settings, device manager, etc.  The device manager recognizes the WG111 (since it appears in the device list, right?).  I believe I need a Linux driver for the WG111 (from what I’ve read).  

Am I on the right track?  Any suggestions on where to go from here?  

Thanks for your help,

Mike

---

### Post by Steve1961 on 2006-03-18
[QUOTE=michaeljoe]Hi. I’m a newbie to Linux.  I’ve got Breezy 5.10 installed.  Now I’m trying to connect to internet.  I’ve done a lot of research on the forums here but haven’t been able to resolve this.  Hopefully someone can help.  I’d really like to ditch Windows!  Here’s my setup.

Primary PC is running Win XP, DSL with a Netgear wireless router. 

Secondary PC is running Win XP as well.  I’m connected to internet via a Netgear WG111 USB wireless adapter.  That setup runs fine.

So,  I installed Breezy on the secondary machine on another partition.  During installation a message indicating an issue with DHCP came up.  I elected to “setup network later”.  After some poking around in Breezy, I found some Network settings, device manager, etc.  The device manager recognizes the WG111 (since it appears in the device list, right?).  I believe I need a Linux driver for the WG111 (from what I’ve read).  

Am I on the right track?  Any suggestions on where to go from here?  

Thanks for your help,

Mike[/QUOTE]

The wireless adapter is listed as working with ndiswrapper [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N")

There's also a how to for setting up your card here:

[https://wiki.ubuntu.com/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://wiki.ubuntu.com/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)

You should be able to install ndiswrapper from the ubuntu cd.

---

### Post by michaeljoe on 2006-03-19
Thanks much for the links.  I got ndiswrapper installed, and downloaded a driver for the WG111 adapter.  Still having problems though .  I'm getting 'invalid driver' and "device not found" when I try to access the adapter.

I'll keep digging.

m

---

### Post by michaeljoe on 2006-03-19
looks like I have an invalid driver.  I'm attempting to re-install the driver from the Netgear Install CD (using ndiswrapper).  when i try to install via the terminal, it says driver already installed.  use - e to remove.  when i try that, it says driver not installed. see below.  how do I get around this?
==================================================
mike@ubuntu:~/drivers$ ls
ndisgtk_0.5-1ubuntu1_all.deb  ndiswrapper-utils_1.1-4ubuntu2_i386.deb  netwg111.inf
mike@ubuntu:~/drivers$ ndiswrapper -l
Installed ndis drivers: netwg111        invalid driver!
mike@ubuntu:~/drivers$ ndiswrapper -i netwg111.inf
netwg111 is already installed. Use -e to remove it
mike@ubuntu:~/drivers$ ndiswrapper -e netwg111.inf
Driver netwg111.inf is not installed. Use -l to list installed drivers
mike@ubuntu:~/drivers$ ndiswrapper -l
Installed ndis drivers: netwg111        invalid driver!
mike@ubuntu:~/drivers$

thanks for any help!

---

### Post by zapcojake on 2006-03-19
you can install ndisgtk which is a graphical tool for the wrapper and it will kind of walk you through it.

---

### Post by michaeljoe on 2006-03-19
thanks for the advice all.  I am replying to this via the internet and Ubuntu!  I ended up uninstalling the driver in the GUI (ndisgtk ?), and reinstalling the driver from the install CD (Netgear WG111).  Only thing I did different this time was select the driver from a folder on the cd named NDIS5.  For whatever reason, that did the trick.  I'm not sure if it was the different driver, or if just got the order of everything right that time.

anyhoo, thanks again!

Mike

---

