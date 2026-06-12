---
title: "iPhone syncing with 3.0"
date: 2009-12-03
forum: General Help
---

### Post by emshains on 2009-12-03
I am using ubuntu 9.10 32 bit on Athlon 64 X2 5000+ @ 3,0ghz, Asus m2n-sli n560, 1gb of ddr2 ram and a 8600gt.
I found a way to sync iphones from linux ([http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)), it works for some people, but not for me. 
I got the iphone to mount, although I didn’t get any feedback from usbmuxd when using tail -f. But, gtkpod doesn’t really sync anything. I have made the hash, I have compiled the libgpod successfully, and all it does is copy some files in the F** folders, but then they are awkwardly named, something with libgpod****.mp3. And, after I tried to sync my 8gb 3g, I got a full disk of seemingly unreadable music- it was readable from the disc, but even after the “Updating library” screen, there are no songs I tried to sync. I can delete the songs. At first. GTKpod deletes the files but doesn’t delete the database entries, you can find them on the “ipod” list, but they aren’t playable. I also tried to compile gtkpod from the latest source, but to no avail. I didn't install both gtkpod and libgpod using "sudo make install", I installed it with "sudo checkinstall & sudo dpkg -i [package]". 

Oh well, at least I tried to do it natively. Now, I found my old XP installation CD, blew off the dust and tried virtualbox. I am using 3.1 and iTunes 8.0. First of all, shared folders didn't work. Nevertheless, I used samba shares. iTunes detects my iPhone, no problems there. But when I try to sync 800 songs or so, after around 50-60 songs copied, it freezes, then drops 3 messages of something similar to this " Error: failed to sync, device timed out." The iPhone is still showing the "Sync in Progress" screen, iTunes also seems to be still trying to sync something, when I press cancel or eject, it hangs up for 5 minutes. Sometimes, when it looses the connection with the phone, it hangs there for around 5 minutes and then locks up the system altogether, both guest and host. I've tried several cables, all of them replicate these results. At the moment, I am trying to sync it in 35 steps, a playlist consisting of 20-30 songs at a time. And even here, it has frozen whilst updating a track (it updates tracks before it copies new ones to the phone). 

And does anybody know how to turn OFF the annoying camera recognition ? When it opens nautilus and pops up a window asking me what I want to do with the recently found camera ? 
Could anyone point out to me, where and what am I doing wrong ? And I am terribly sorry about my english.

---

### Post by emshains on 2009-12-03
Is this in the wrong section of ubuntuforums ?

---

