---
title: "bcmwl5....help"
date: 2006-06-06
forum: General Help
---

### Post by serendipity576 on 2006-06-06
Hi, 
   Well I upgraded to Dapper and I can't figure out how to get my wireless working.  I know that I need this driver for my Dell 1390 card, however when i do "iwconfig" it comes out with this:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

So.....unlike some people, I can't even SEE my wireless card in iwconfig or networking window GUI.  People have told me to try bcmxxfwcutter, something like that, but isn't that the wrong driver?  And the following is what I get when I modprobe it.

modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.15-23-386/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.15-23-386/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.15-23-386/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted

Any help at all on this?  I just keep hitting these brick walls it feels like.  ](*,)

---

### Post by xXx 0wn3d xXx on 2006-06-06
Read [ this howto. ](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by serendipity576 on 2006-06-06
But it says I need to be able to see the wireless card in Ubuntu, and I can't, so I thought this howto would not work for me.  Anyone out there with a Dell 1390 know?

---

### Post by xXx 0wn3d xXx on 2006-06-06
Type:
> lspci
in terminal and see if Ubuntu is detecting your wireless card. Try installing the firmware for your card.

---

### Post by serendipity576 on 2006-06-06
0000:09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

There's what I get for lspci.  Looks like it doesn't know it?  By firmware(yeah I'm retarded I know), what do you mean?  Thanks for everything.

Clay

---

### Post by xXx 0wn3d xXx on 2006-06-06
[QUOTE=serendipity576]0000:09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

There's what I get for lspci.  Looks like it doesn't know it?  By firmware(yeah I'm retarded I know), what do you mean?  Thanks for everything.

Clay[/QUOTE]
Look on your computer distributor's website for drivers for your wifi card. Then take then and get the b***.sys and .inf files. (I can't remember the exact name) and then extract the needed files. Here's an easier method:

1. in terminal type:
> wget [http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.1-0ubuntu1_all.deb](http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.1-0ubuntu1_all.deb)

and then
> sudo dpkg -i bcm43xx-firmware_1.1-0ubuntu1_all.deb

You should then be able to follow the tutorial I posted above.

---

### Post by serendipity576 on 2006-06-06
I downloaded the package and it said it installed successfully.  Then I opened a terminal and typed the above command and here's what it spit out.

dpkg: error processing bcm43xx-firmware_1.1-Oubuntu_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bcm43xx-firmware_1.1-Oubuntu_all.deb


So, not sure what to do next.  Sorry for so much trouble...:???:

---

### Post by xXx 0wn3d xXx on 2006-06-06
[QUOTE=serendipity576]I downloaded the package and it said it installed successfully.  Then I opened a terminal and typed the above command and here's what it spit out.

dpkg: error processing bcm43xx-firmware_1.1-Oubuntu_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bcm43xx-firmware_1.1-Oubuntu_all.deb


So, not sure what to do next.  Sorry for so much trouble...:???:[/QUOTE]
Make sure that your in the right directory. If it's on your Desktop:
> cd Desktop
then 
> sudo dpkg -i nameoffile
I hope that helps.

---

### Post by serendipity576 on 2006-06-06
well I followed that how to and everything seemed to go ok, but no wireless.  I have a driver named bcmwl5.inf, and bcmwl5.sys on my desktop and I also put wl_apsta.o on my desktop according to the how to and that's the one I used in the following directions.  What should I do now, try the other driver, uninstall the other one if so? 

Also, in my firmware folder is bcmxx., a lot of those type of files, and then they show up again in the /lib/firmware/2.6.15-23-386.  So I'm not sure what move to make next, but I feel like I'm getting close.....thanks for any more help, you've been very patient.  :) 

Clay

---

### Post by serendipity576 on 2006-06-07
Anyone have any ideas/guesses on this one.  I know everyone's got to be getting sick of dealing with wireless posts, but here  I am, :-k

---

