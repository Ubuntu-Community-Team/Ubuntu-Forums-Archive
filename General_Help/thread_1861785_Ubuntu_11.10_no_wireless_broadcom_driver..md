---
title: "Ubuntu 11.10 no wireless broadcom driver."
date: 2011-10-16
forum: General Help
---

### Post by SENTINEL5000 on 2011-10-16
Hi to all. I have a gateway mx6216 laptop that has broadcom drivers for Wireless internet. I installed ubuntu 11.04 and using an old driver I was able to make wireless work well. Problem is I upgraded my laptop to Ubuntu 11.10 and in the process it installed the new wireless adapter drivers.

But those drivers does not work on my laptop so I uninstalled them and tried to use the old driver I had in 11.04 and tho it installs I still cant get the wireless to work. Any ideas on how to fix my wireless? Thanks in advance!

---

### Post by sgtron on 2011-10-16
Try this fix:

the acer_wmi kernel module is interfering with the Broadcom 4313 driver. To fix it, add "blacklist acer_wmi" to the file /etc/modprobe.d/blacklist.conf and then reboot. 

Snipped from: [http://www.zdnet.co.uk/blogs/jamies-mostly-linux-stuff-10006480/ubuntu-1110-oneiric-ocelot-10024566/](http://www.zdnet.co.uk/blogs/jamies-mostly-linux-stuff-10006480/ubuntu-1110-oneiric-ocelot-10024566/)

---

### Post by SENTINEL5000 on 2011-10-16
Adding that line to the blacklist file did nothing. For some reason in synaptic it says I have the old driver installed which should work but it only wants to upgrade to the newer one which does not work. Is there a way to force the computer to use the old driver instead of the newer one?

---

### Post by rabilon on 2011-10-16
I've been running Ubuntu 10.04 with the broadcom driver for my Dell Inspiron 1545. I installed 11.10 today in a separate partition (dual boot). Before I installed, I checked that everything worked when using the 11.10 LiveCD. The broadcom driver installed and worked fine. But when I installed 11.10 the driver will not install. It says to check /var/log/jockey.log but I don't see anything useful there. What gives??

---

### Post by Get_It on 2011-10-16
I'm having the same problem on Xubuntu 11.10.

One thing that I find strange is that when I was following a tutorial for installing firmware-b43-installer with a wired connection I was able to connect to my wireless network. However, after rebooting and disconnecting the wired connection the wireless connection no longer worked.

Right now I don't have time to work on this but as soon as I check it again I'll give an update.

Best regards,

---

### Post by Groescht on 2011-10-16
Yeah, I am having the exact same problem as Rabilon.  Same computer and message.

---

### Post by garvinrick4 on 2011-10-16
Problems with > 3.0 kernels (# means in root) ($ does not need to be root)
 A problem has appeared with recent 3.X.X kernels where the wl.ko driver loads but is inoperable.  
The issue is related to the new bcma driver which is incompatible with this driver. 
The bcma driver is analogous to the old ssb driver and [COLOR=Red]bcma needs to be removed and/or blacklisted before wl  can function properly[/COLOR]:  
See if any relevant drivers are loaded: 
$ lsmod | grep 'b43 \| bcma \| wl'  
If any of these are installed, remove them ([COLOR=Red]as root[/COLOR]): 
# rmmod b43 
# rmmod bcma 
# rmmod wl  
Now load the new wl driver: 
# insmod wl.ko 
 wl.ko should now be functional.  
To blacklist the bcma driver and prevent it from loading in the future: 
# echo "blacklist bcma" > /etc/modprobe.d/blacklist.conf

[http://www.broadcom.com/docs/linux_sta/bcma.]("http://www.broadcom.com/docs/linux_sta/bcma.txt")

---

### Post by Get_It on 2011-10-20
I managed to fix the problem that I had by using the solution posted by wildmanne39 on [Wireless won't install firmware in 11.10, works fine prior]("http://ubuntuforums.org/showthread.php?t=1859446#7").

Best regards,

---

### Post by CharlieMav73 on 2011-10-21
I had this same issue so I just blacklisted both bcma and ssb as they were conflicting w/ b43xxx (which I also un-blacklisted) and then rebooted. Things worked fine, except I had to set the wifi network as "Infrastructure", rather than ad-hoc. I had the Broadcom driver installed and activated before beginning these steps. I followed the info on Broadcom's site.

Some steps:

1. Login as root - $ sudo -s
2. enter your root pw
3. browse to /etc/modprobe.d
4. gedit blacklist.conf
5. find the line that blacklists b43xxx and add a # in front of that line
6. add 2 entries - blacklist bcma & blacklist ssb
7. Save the blacklist.conf
8. reboot

Worked for me!

---

