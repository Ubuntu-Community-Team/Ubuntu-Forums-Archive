---
title: "Rythymbox + NAS"
date: 2010-04-27
forum: General Help
---

### Post by robafo on 2010-04-27
So I've done some searching on the forums, and I think I'm just getting myself more confused about this issue. I currently have a laptop running 9.10. I also have a 500GB western digial my book world NAS. I can see the hard drive, copy files, etc. by going to places/network and putting in the share address. I have about 50 GB of mp3 files on the drive that I would like to play from rythymbox, but if i don't want to import local copies of the files. I did some searching, and saw info about DAAP and Samba (i believe I'm attached to the hard drive as a samba share), but it's just confusing me more. What is the easiest way to play music over a home network?

---

### Post by doas777 on 2010-04-27
if your NAS supports DAAP, enable it. DAAP is a streaming server that you can access in Rythmbox from the right pane. mine appears at the bottom of the list on the right pane, and is advertised as a "Firefly" server. 
once you get daap going, post back and we'll try to get rythmbox to connect to it. 

BTW, samba (standard file sharing) will work for yourneeds, but first you must mount the share somwhere that rythmbox can access it. here is some info on that. please note, one of the few places you cannot mount the share to make it work is ~/.gvfs (the place where shares are mounted by default).

---

### Post by robafo on 2010-04-27
Thanks, I'll check on DAAP when I get home and reply. After a quick look, it seems that I can get Firefly installed on this particular NAS ([http://mybookworld.wikidot.com/guide-to-installing-firefly-svn1696](http://mybookworld.wikidot.com/guide-to-installing-firefly-svn1696)), but hopefully I won't have to go through all of that. Just looking at the manual for my drive, I don't see a DAAP option ([http://www.wdc.com/en/library/usb/2779-701026.pdf?wdc_lang=en](http://www.wdc.com/en/library/usb/2779-701026.pdf?wdc_lang=en)) It's an older drive, but I hope I won't need to tweak too much. I'll post back later.
 
Thanks!

---

### Post by doas777 on 2010-04-27
if firefly seems a little much, take a look at this guide for mounting your samba shares to your local filesystem. may be easier in the long run:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

