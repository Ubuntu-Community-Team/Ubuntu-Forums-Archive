---
title: "Updated....and lost ALL internet. Why?"
date: 2011-06-01
forum: General Help
---

### Post by Redding on 2011-06-01
Hello, updated to the latest version several weeks back. Everything  loaded fine and system works fine.....except for the internet (wireless  AND wired).

I'm still real new at Linux so I just stopped and switched back over to  Windows (dual-boot) out of frustration. Figured I'd finally tackle my  problem today. Internet and everything worked perfectly before upgrade  and now......NOTHING. I hooked laptop (computer running Linux) up to  hard line on main computer.....still no internet. What gives??

Help!

---

### Post by ruffEdgz on 2011-06-01
What version of Ubuntu do you have installed?
```

cat /etc/*-release

```
What type of wireless card do you use?
```

lspci -nn | grep "Network controller"

```
Thanks

---

### Post by Redding on 2011-06-01
Ruff


-Ubuntu 11.04 is the version

-"Wireless Card" result...... Broadcom Corporation BCM4311 802.11a/b/g

---

### Post by Redding on 2011-06-03
Hello, 
Is there anyone out there that could possibly help me, please? I'm soooo tired of Windows. I had fallen in love with my Linux and then had to go and screw it all up.

Please help.

---

### Post by linuxinstalledfromhdd on 2011-06-03
The latest version upgrade process didn't seem to go so well for some people. It may be a good idea to simply roll it back to 10.10 for now, at least until they can get all the bugs out of the upgrade process, or you can install a fresh copy of 11.04

Here are some guides to hopefully get you back in business in no time.

10.10 (this is the one that I am using.. no issues.. or problems either) 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

11.04

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

And I recommend you use a USB Flash Drive to install your system from.  Works faster that way.

---

### Post by Redding on 2011-06-03
Hello, 
Thanks for the reply. I actually WAS using 10.10 since I installed Linux and had NO problems whatsoever. I saw that there was an update and thought to myself, "Oooooh shiny things" and jumped right in. I wouldn't mind a bit going back to 10.10.

Now, that being said, is there a way to just revert back? Or do I have to start all over and lose my settings? I guess it wouldn't matter, considering I think I lost them all anyway when I upgraded, but it would be nice to just turn back time. 

Thanks again for the help so far.

---

### Post by linuxinstalledfromhdd on 2011-06-03
> **Redding said:**
> Hello, 
Thanks for the reply. I actually WAS using 10.10 since I installed Linux and had NO problems whatsoever. I saw that there was an update and thought to myself, "Oooooh shiny things" and jumped right in. I wouldn't mind a bit going back to 10.10..

Well I bought a brand new laser printer a couple of weeks before 11.04 came out.  A really nice expensive one.  And I didn't expect it to work with Ubuntu 10.10, but lo and behold it worked perfectly.  Then did a fresh install of 11.04 from a disc. Guess what?  My printer did not work perfectly anymore. And when I printed with it, it would spit endless empty pages out until I physically had to unplug the unit to make it stop.   I wasn't really that impressed with Unity, but it is of course much nicer looking than that old netbook remix they had a while ago. 

I'm really happy with 10.10. I will upgrade to the next LTS probably at that point because this is more than enough. 

I don't know of a easy way for you to roll back.   I didn't want to bother with potiental errors and what not, so I just wiped the system clean and reinstalled. I have a cloud backup that I used to put all my stuff temporarily while I did it too.  No problem. :)

I don't mind helping other people with little issues and stuff.. But I just format, rerun a little script file and I am back in business in like 15 minutes.

---

