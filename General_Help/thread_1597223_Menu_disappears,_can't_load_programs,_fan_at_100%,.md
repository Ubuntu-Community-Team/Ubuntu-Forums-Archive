---
title: "Menu disappears, can't load programs, fan at 100%, etc"
date: 2010-10-15
forum: General Help
---

### Post by Scoobin on 2010-10-15
I've just installed Lubuntu 10.10 to an Asus A2400H laptop. It has a Celeron 2.6 Ghz CPU and 512mb RAM. In the past I have installed Ubuntu and more recently Xubuntu 9.10 and 10.04. This time round I wanted to try out Lubuntu to get more speed out of this laptop but it's giving me crazy problems.

When I run the Live CD all seems to work well and quick and there are no problems I can see. Then having installed it -- no errors during install -- when it boots up the fan goes at 100%, the only items on the menu are log off and something else of no use, but neither work. I can't load any of the main programs, but I can get to terminal and the update manager works, although it works extremely slowly. 

I typed the 'top' command from the terminal and it says CPU usage is only 35% and only half the memory is in use, and no swap file.

I have tried a reinstall and it's exactly the same. I've done the 'check disk for errors' and given the CD lens a clean because sometimes this has caused problems in the past, but it doesn't seem to be the case here given there are no errors during install (I watched the whole install... all 50 minutes of it).

I have previously istalled LXDE on this laptop side-by-side with Xubuntu and it did have some fan issues and bugs but still worked for the most part, so I would have thought just having the one system would create less conflict.

Can anyone shed some light on this?

---

### Post by spowel4 on 2010-10-15
I'm having exactly the same problem, on a Compaq NC8230.  No answers yet.

---

### Post by Scoobin on 2010-10-17
Funnily enough, cleaning the CDROM 2-3 more times with a cleaning disc and cleaning alcohol did the trick. I had a couple different problems once I got it installed though: one being an issue where web browsers wouldn't load because the permissions were stuffed (I saw a thread for this elsewhere), and another being Chromium wouldn't play flash because it apparently lacked the plugin yet the plugin is supposedly built in.

I got around these problems though. For web browser issue, I didn't manage to fix it with chmod etc so I deleted the user and created a new one and it worked. NB: 1# you must create a secondary user to use while you are removing the first one. 2# Note that you will lose all data in your home folder (if any) unless you first back it up.

For the Chromium Flash problem, I just used Synaptic to find the flash plugin and downloaded it and then it was working.

---

