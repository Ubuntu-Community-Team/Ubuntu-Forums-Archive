---
title: "Having issues booting from 11.04 Desktop CD SATA link down event detected."
date: 2012-09-20
forum: General Help
---

### Post by j1zm4k on 2012-09-20
Hello, 

I'm somewhat new here.  My main goal is to dual boot Windows 7 and Ubuntu 11.04.  I went ahead and created the necessary partitions and Ubuntu 11.04 Desktop boot CD.  

However whenever I boot from CD I see the following:

5.889803] cdrom: Uniform CD-ROM driver Revision 3.20
5.889913] sr 1:0:0:0 Attached scsi CD-ROM sr0
5.890000] sr 1:0:0:0 Attached scsi generic sg1 type 5
6.208702] ata5: SATA link down (SStatus 0 SControl 300)

Could this be an issue with SATA settings within the BIOS?

My laptop I just recently bought, is a Lenovo ThinkPad T530.  I also was able to replicate this problem using boot from USB.  Any additional information/help to fix this would be greatly appreciated.

Thank you!

---

### Post by Bucky Ball on 2012-09-20
Welcome to Ubuntu and the forums. 

My first tip would be forget 11.04. Support ends in about a month. Go for 12.04 LTS (long-term support) which was released in April 2012 and is supported until April 2017. Running pretty well for most and will become more and most stable as time goes on. LTS releases now have five years support, everything else eighteen months.

Tips: Install Win first if not already installed. Use only what you need for Win and leave the rest as free space. Choose 'Something Else' when you get to the partitioning part of the Ubuntu install and do the rest of the partitioning then. Best to create an extended partition using the free space and put the Ubuntu partitions in there on logical drives. If you don't understand just say ... This link should help out:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

;) 

If you want to share data between the two OSs you are going to need to create an NTFS partition (Win can not read or write EXT4 partitions, which is what Ubuntu currently uses).

---

### Post by j1zm4k on 2012-09-20
Hi Bucky,

Thank you for your reply, the main issue that I have with 12.04 LTS is that the classic gnome 12.04 is nothing like gnome 2 in previous distributions.  I really enjoyed the old distro's and prefer the older gnome 2 feel.  I find installing themes and adding customization has become very cumbersome with 12.04     

I previously installed 12.04 but Unity also turned me off from using that version.  I uninstalled Unity and tried using the classic version but there is no longer any gnome 2 support.  

I'm somewhat scrambling to get everything installed before October before the repositories are taken down.  Any assistance to correct this problem would be more than appreciated.

Thank you

---

### Post by Bucky Ball on 2012-09-20
Gave up on Gnome awhile ago and not a Unity fan myself. I've used Xubuntu/Xfce for ages. You could install 12.04 LTS, install xfce4 immediately, log out, choose 'xfce session' from the Sessions popup menu and log back in to try it out. Or try Xubuntu from the LiveCD. You can install regular Ubuntu apps into that no problem. Lubuntu is interesting, too (lxde for the desktop environment in another Ubuntu flavour).

Maybe its time to experiment? Trust me, I totally get why fix it if it's not broken, but security updates will also cease in October, which may or may not be an issue to you. ;)

---

### Post by j1zm4k on 2012-09-20
Hi Bucky,

Awesome suggestion for Xubuntu.  I'll go ahead and try that distro as I can also install Gnome 2.

Thank you!!!

---

