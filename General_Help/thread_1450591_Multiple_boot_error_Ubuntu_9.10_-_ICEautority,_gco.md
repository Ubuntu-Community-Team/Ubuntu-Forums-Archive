---
title: "Multiple boot error Ubuntu 9.10 - ICEautority, gconf, Nautilus"
date: 2010-04-09
forum: General Help
---

### Post by jlahn on 2010-04-09
Hi all,

yesterday I did a clean install of Ubuntu 9.10. Everything worked fine for several restarts, including after installing a Vista VM in Virtualbox. Yet since this morning, I cannot boot Linux any longer. I do not know if this could be related to my last install, which was Think Pad Fan Control according to [http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control).

The error messages showing up while (unsucessfully) booting are the following

> 
1. Could not update ICEauthority file /home/xxx/.ICEauthority
> 
2. There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 ended with status 256)
> 
3. Nautilus could not create the following required folders /home/xxx/Desktop, /home/xxx/.nautilus
Hopefully I typed everything correctly...:) I fear I do not even know more than the wiki would tell me about the different items.

I am currently booting from the live CD and have tried googling all the error codes, but the threads seem all to relate to different situations and I am too much of a Linux newbie to understand how they could be related and how I might fix my problem without having to loose all my installation work from yesterday. :confused: 

Do any of you have the knowledge and time to tell me? Any help would be greatly appreciated! Thanks a lot in advance.:)

---

### Post by ibuclaw on 2010-04-09
Do you have a separate /home partition?

If you do, sounds like it isn't automounting correctly.

If you don't - then it is probably a permissions issue on the seldom files/folders.

Regards

---

### Post by jlahn on 2010-04-09
Thanks, ibuclaw, for your quick reply. :)

Ah, but no, I do have only one partition.

In that case, how do I go about fixing the permissions? And from where - do I do it from the Live CD?

---

### Post by jlahn on 2010-04-10
Ok, I learned  that I can boot in the recovery mode. Now I am sitting before the text prompt, feeling pretty illiterate even after reading *man chmod. *And my term paper waiting on my computer to be written. ](*,)
Is this the right path? Can anyone tell me what to do exactly to try to fix the three errors above? :) Thanks a lot.

---

### Post by jlahn on 2010-04-11
Desperate to work on my computer again, I basically tried everything I found in these two threads

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

[http://ubuntuforums.org/showthread.php?t=1373476](http://ubuntuforums.org/showthread.php?t=1373476)

Apparently, it seems to be an error many encountered and some resolved. I do not really know what I'm doing, and what to do next, so I have to kindly ask you for your help again :-)

**First** I tried, from the recovery root shell

> sudo chmod a+rwx /tmpIt changed absulotely nothing in the next boot attempt.


**Then** I tried 

> sudo chmod 775 home/xxx/
sudo apt-get remove nautilus
rm /home/jannik/.ICEauhtority 
No such file or directory.
sudo shutdown -r now

sudo apt-get install nautilus
sudo shutdown -r nowNow, the error messages (see first post) have vanished, but I do not get any desktop, just the mouse.


As suggested in the bug thread, I then tried[CENTER]*Alt+Ctrl +T*
[/CENTER]
 to get a terminal in order to get a DE with [CENTER]*sudo gnome-panel*
[/CENTER]
but I received no reaction whatsoever, and the computer does nothing even after waiting.

What is worse, since I could have tried another suggestion from the thread, namely 
[CENTER]*sudo chmod 775 /etc/gconf.xml.system*
[LEFT]is that now upon rebooting I cannot get GRUB to stop and offer me the recovery mode anymore, it simply does not respond to hitting ESC anymore. 

This might be unrelated, but I really do not know what to do now and how to get into my system anymore. Can anyone please help me to get it running again? 

Thanks a lot for your efforts, 

Jannik

Edit: In one of the threads it is suggested to disable autologin - just how do I do so (provided I get into the recovery shell again)?


Note: 
Other people seem to have been more succesful (see the bug thread), but I do not want to cross-post. So if one of the admins want to transfer this question to a more appropriate / fitting thread, I would really appreciate it. :)
[/LEFT]
[/CENTER]

---

