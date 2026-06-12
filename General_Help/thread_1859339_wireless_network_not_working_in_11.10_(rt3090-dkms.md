---
title: "wireless network not working in 11.10 (rt3090-dkms)"
date: 2011-10-13
forum: General Help
---

### Post by JCM_Pico on 2011-10-13
Hi there,

Went to check if the new ubuntu version worked fine in my Asus-UX30, since there was some issues with the wireless drivers.
I created a live cd (32bit) and give ubuntu a try... and it runed quite well, got wireless internet and everything running out of the box.
Then, I downloaded the ubuntu 64bit (memory is precious for me) and installed it. Now I got no wireless internet connection, got  drivers that I needed (rt3090-dkms) installed natively... and I don't know here to turn to...

Any help?

---

### Post by Steviepower on 2011-10-14
Same here, even tho I have this problem after an upgrade from 11.04 to 11.10, I don't have the problem while running on the 2.6 kernel instead of the new 3.0 one.

---

### Post by JCM_Pico on 2011-10-14
This is strange, after some hours without solving the problem any after many reboots I whent to sleep. When I wake up I turn on the computer and got wireless connection :confused:

So my only explanation is that some tiny creatures came at night and fixed my computer ....

---

### Post by cirelosborn on 2011-10-14
Unless some magic nargles come in and fix my sony vaio vpcm111ax tonight I'm going to go mad trying to fix this wireless issue with the 11.10 upgrade.  I had some rt2... and rt3... drivers blacklisted on 11.04 because the wireless would shut off when the netbook was unplugged.  Blacklisting worked but now, I've unblacklisted all of my wireless drivers and still nothing.  So, come on nargles daddy needs wireless!

---

### Post by JCM_Pico on 2011-10-14
My laptop uses rt3091 and I just let the install stay has it is and its working. Why don't you try to remove the blacklisted drivers

---

### Post by thunderbirdje on 2011-10-14
Had kind of the same problem, first I only could use the cable, after some reboots I could only connect through wireless, then none of them. 

It's clear it is solved now... 

Maybe you can try what I did? I noticed that when connecting the cable, it said that it was connected to a network 'XYZ' which is a network I used when I was travelling. That network what set with some special custom settings. Because I didn't need it anymore I just deleted that network. The list 'wired' was empty.

Then I selected from the network menu icon: 'Auto ethernet'. Because it was again the first time I connected, the network manager seems to save the new name of the network internally and I could surf again! The wireless network works as well now just by doing this.

Hope this can be helpful to someone else! ;)

---

### Post by kbenoit on 2011-10-17
I've got a similar problem, no wireless since I uograded to 11.10. I have no module loaded regarding 802.11, no module looking like "^rt.*". What modules/driver are you using with rt3090 ?

EDIT:
Well, I figured out the driver should be rt2800pci, which led me to see that just like cirelosborn, I had a few drivers blacklisted in /etc/modprobe.d/blacklist-wireless.conf . So I removed the entry with rt2800pci and everything works fine.

Kristian

---

