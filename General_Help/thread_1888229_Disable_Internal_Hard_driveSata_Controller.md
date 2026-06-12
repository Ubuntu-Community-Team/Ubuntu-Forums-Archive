---
title: "Disable Internal Hard drive/Sata Controller"
date: 2011-11-28
forum: General Help
---

### Post by tristar on 2011-11-28
Hi,

I wanted to know if there is any way a Hard drive /SATA Controller can be disabled on my Maverick.. I have 5 different hard drives and it's a pain to unplug them everytime. I have various other OS and would hate to have to rebuild MBR everytime I want to boot from a specific OS.

I have checked various forums and there are always wise cracks about disconnecting the hard drive. So please suggest an option where the Hard disk or particular Sata Controller is not detected at all, rather Ubuntu should not see this Hard drive at all and a way to reverse this. unfortunately I'd hate to change it at the BIOS either since it has a very crazy RAID kinda setup.

I'm a noob to Ubuntu even though I have been using it since Dapper. Please suggest a best option.

Thanks in advance !

---

### Post by efflandt on 2011-11-28
Not sure how you could make drives not be seen, but if you just want to spin down inactive drives **hdparm** has settings to to that either immediately (-y or -Y option) or after a period of inactivity (capital -S option).  In the latter case it will wake up if accessed and then snooze again after inactive for the set time.  You have to use sudo for hdparm.

In my case I have Windows mbr on sda with Win7, and Maverick on sd4 with grub on its partition (which could be booted directly by marking its partition as boot).  But I currently boot everything from 11.10's grub on sdb (SSD drive).  So BIOS is currently set to boot sdb.

There was some Win7 update (maybe a service pack) that would not install unless Windows knew it could boot itself, and one Dell app stores data in what it thinks is an unused part of the mbr (which stepped on grub2). So I just leave sda with the Windows mbr and the partition it boots from marked as boot.

---

### Post by tristar on 2011-11-30
Thank you for your reply. Is there any specific point where the hard drive is initialized or the controller is detected. eg: You can disable the SATA controller in BIOS however the problem is my BIOS controls 3 sets of 2 SATA Controllers and Disabling that would not work.

It's a crazy setup so I can't afford to disturb the current setup. Strangely I had Maverick and was working fine (not sure what I did) with not detecting the drives however I ran into ALSA issues and thought I might as well download the latest version and ran into this issue :(

---

