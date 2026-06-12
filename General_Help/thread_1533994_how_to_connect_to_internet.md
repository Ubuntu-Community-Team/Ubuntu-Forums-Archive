---
title: "how to connect to internet"
date: 2010-07-18
forum: General Help
---

### Post by emopoops on 2010-07-18
how to xconnect to the internet i have vista i instaled with wubi and my internet connection is no avaiblble. i cannot see anny avaible networks and i obvously can acess them on vista now,
 i have laptop, the 2 main things in the connect icon menu are disabled.
 help please i need internet conection
 edits:
i have wireless card: Broadcom BCM94311MCG
 and someone states i need to actually use
 ndiswrapper, but i dont know HOW I USE ndiswrapper with my computer/how i download/what i do/ what i do aboutthe wireless ccard and all this driver thigns i have been reading about.

---

### Post by watupgroupie on 2010-07-18
What brand is your laptop? I had issues with my Dell XPS laptop and it's wireless card. Make sure to check if there is proprietary drivers available.

---

### Post by petrus250 on 2010-07-18
> **emopoops said:**
> how to xconnect to the internet i have vista i instaled with wubi and my internet connection is no avaiblble. i cannot see anny avaible networks and i obvously can acess them on vista now,
 i have laptop, the 2 main things in the connect icon menu are disabled.
 help please i need internet conection
This is most likely due to drivers, but it may a bug concerning your hardware, fund out your specs and google it.
Hope this helps

---

### Post by emopoops on 2010-07-18
compaq presario c700
 i have no idea what a wireless card is. usally i can just connect to the internet in vista by viewing the avaible wireless connections.

---

### Post by jschall1 on 2010-07-18
You have a Broadcom BCM94311MCG
From what I've read, you need to use ndiswrapper to get the drivers working.

---

### Post by watupgroupie on 2010-07-18
I have a Broadcom wireless card too. There are proprietary drivers supplied for the card on the Ubuntu live cd. 

Go into your Software Sources under System and then Administration. Check off the box at the bottom that says Cdrom with Ubuntu 10.04 'Lucid Lynx'. Now enter Hardware Drivers under the Administration menu as well. Make sure you have the Ubuntu disk in your drive. It will automatically search for drivers that match your hardware and should install it. It might be online too, this is the way I did it though.

---

### Post by emopoops on 2010-07-18
dont have the disk, i installed wubi.
can someone tell me what i do with ndiswrapper?

---

### Post by emopoops on 2010-07-18
this thread i dont understand but  think its really relevant perhaps someone could help me understand what to do from this thread:
[http://ohioloco.ubuntuforums.org/showthread.php?p=3975998](http://ohioloco.ubuntuforums.org/showthread.php?p=3975998)

 i know thats for a different ubuntu number and i have the wubi 10. whatever latest one.

---

### Post by Megaptera on 2010-07-19
I know this talks about Karmic and Dell but it's a Broadcom fix that you might like to try - it works in 10.04 as well:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Don't forget to reboot afterwards.

---

### Post by emopoops on 2010-07-19
i really dont know what to do with this.
 first of all, i cannot connect to the internet with a wired connection. and this is just a mess will i ever be able to get internet on the ubuntu os?

---

### Post by watupgroupie on 2010-07-19
You can't connect with a wired either? That's really odd, is it something to do with your network?

---

### Post by emopoops on 2010-07-19
lol, u think its something with my network. no i am on a laptop and the modem imrecieving from is hooked up to the desktop computer.

---

### Post by watupgroupie on 2010-07-19
I've just never had a problem when using a wired connection before if my wireless fails me. So basically you have no internet access from your laptop with Ubuntu on it?

---

### Post by emopoops on 2010-07-19
u got it! itried to test my **** out but they werent sorrking with the  ubuntu

---

