---
title: "How to install a DLNA server for Samsung Wave S8500 mobile?"
date: 2010-08-17
forum: General Help
---

### Post by niyam on 2010-08-17
I've got Ubuntu 9.04 Jaunty Jackalope. How may I install and configure a DLNA server on this laptop to share music, photos, and videos, with my Samsung Wave S8500 mobile, please?

---

### Post by stefangr1 on 2010-08-17
For my samsung TV I use mediatomb. I guess this should work for your phone as well (though it didn't work very well on my TV with any software, even with Samsung's own).

---

### Post by niyam on 2010-08-17
Thanks stefangr1 for the prompt reply. I followed your posts here:
[http://ubuntuforums.org/showthread.php?t=1198689&highlight=mediatomb+on+samsung](http://ubuntuforums.org/showthread.php?t=1198689&highlight=mediatomb+on+samsung)

and set up mediatomb exactly as described, including editing the config.xml and editing and adding lines, as explained. Restarted mediatomb, and added files. To be on the safe side, am only adding mp3 and jpg files to start with. On enabling "AllShare" on the Samsung Wave S8500 i do get it to scan the airwaves and list the mediatomb server. (had to switch off my firewall on the laptop to get it to show). On connecting to the mediatomb server from the mobile, it lists no files on the mediatomb server. What may I be doing wrong?
niyam

---

### Post by niyam on 2010-08-18
I've installed MediaTomb, and followed the edits and additions to the config.xml file as detailed earlier, both in /etc as well as in .mediatomb/ plus i've punctured my firewall to let the mobile through the right ports and services. All seems to go well. The mobile scans and immediately lists the 'MediaTomb' server. When i connect to it and browse it, it shows no files however. I've even added plain-jane JPG files and mp3 files, but no cigar.
Then, I installed tvmobili as well. It does not show up at all on my mobile, though i've got the relevant ports open. However, the 'settings' tab in tvmobili does show my samsung S8500 is sensed:
**Name: **Samsung User-Agent DLNADOC/1.50 SEC_HHP_GT-S8500/1.0
**Location: xxx.xxx.xxx.xx**x
**Class: **Samsung User-Agent DLNADOC/1.50 SEC_HHP_GT-S8500/1.0
 
**Name: **Samsung User-Agent DLNADOC/1.50
**Location: xxx.xxx.xxx.xxx**
**Class: **Samsung User-Agent DLNADOC/1.50

of course, the location has my correct IP address of the mobile.
how do i proceed next?
i've disabled tvmobili from being accessed over the wild internet, it's just being served internally on my wifi-lan.

on the 'settings' tab, 
**'External Port:** Not Yet Negotiated With Router/Firewall.' is displayed which i presume is available if i allow friends (hopefully) from connecting over the wild web out there.

what gives?

finally, i also tried commenting out the two additional lines that were added into config.xml. again, the server is sensed by the mobile, but the content is not listed and visible.


regards
niyam

---

### Post by gustavobaezz on 2010-09-27
Dear niyam

First of all sorry for my English if i make a mistake (I&#7743; Spanish):popcorn:

I am a new samsung wave user and as you I have been having problems with @##~½¬¬ dlna server (or better bada&#347; dlna client) but try ps3 media server.

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

If you dont want to follow those instructions only download ps3 media server, look for PMS.sh and execute it (remeber the execution bit in file properties to be able to execute it).

It doesn t do any installation... so you can copy the folder wherever  you want and simply execute it.
Simply it works perfect:guitar:

---

### Post by amaster on 2010-11-02
T_T
Pls Can you explain it more?
With PSM Server My s8500 don't see this server ><
> **gustavobaezz said:**
> Dear niyam

First of all sorry for my English if i make a mistake (I&#7743; Spanish):popcorn:

I am a new samsung wave user and as you I have been having problems with @##~½¬¬ dlna server (or better bada&#347; dlna client) but try ps3 media server.

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

If you dont want to follow those instructions only download ps3 media server, look for PMS.sh and execute it (remeber the execution bit in file properties to be able to execute it).

It doesn t do any installation... so you can copy the folder wherever  you want and simply execute it.
Simply it works perfect:guitar:

---

