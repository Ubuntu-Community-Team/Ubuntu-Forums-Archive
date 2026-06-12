---
title: "Computer locks up, slows way down"
date: 2011-07-09
forum: General Help
---

### Post by linux_trojan on 2011-07-09
About a week after installing 11.04, I started noticing that my computer basically locks up after leaving it for many hours.  When I come back, I cant get any programs to respond.  I click on Firefox and it takes about one minute for it to finally respond. If I try to launch Konsole, it locks up too.  But suddenly all programs start responding at the same time, after about one minute. 

This is very frustrating and I just feel the problem is zeitgeist.  Of course I am not sure because I cant even run System Monitor to check the problem since I cant run any apps for about a minute.  By the time I run System Monitor everything is working again.  Any suggestions?

---

### Post by dabl on 2011-07-09
Next time you are ready to leave the system running and do something else, pop open a terminal window and run "top".  Then just leave it.

When you come back and the system is unresponsive, take a look at the top window and see what process is hogging the CPU.  That will tell you the place to start troubleshooting.

---

### Post by linux_trojan on 2011-07-09
I just ran top and I notice that Nautilus is using up 11.2% of the RAM and Firefox is using up 7.3%.  I have 4 GB of RAM.  Is this normal?  It didnt do this at first.  I use alot of message board for Ubuntu, Gambas, C programming.  Could I have been hacked from those forums?

---

### Post by dabl on 2011-07-10
The nautilus figure seems way high, but I would not think that RAM usage was the cause of the "freeze" symptoms.  When you looked at top, was the RAM almost totally used (over 95%)?  Was swap being used?

Usually such "freeze" symptoms are a result of _CPU_ resources being maximized, rather than memory.  Try it again, and next time see what the top user of CPU resources is.  Also look for xorg and see what percent of the CPU it is using.

Hacking from web forums is a most unlikely source of the problem you are seeing.  If it turns out not to be a video issue, you can run netstat and look for unusual networking workload.

---

### Post by linux_trojan on 2011-07-10
I came home after my computer was on for like 7 hours and this is what top tells me

%CPU-----% Mem-----Command
27-------------1-------------plugin-containe
20-------------6.4-----------firefox-bin
14-------------1.6-----------Xorg
13-------------19.2----------Nautilus

Ram is about 50% of the 4 GB and only 1 Gig of the 8 Gigs is used for swap.


What do you think?

---

### Post by dabl on 2011-07-12
I do not recognize that "plugin-container" process (I'm a Debian/KDE kinda user), but that is your main offender in CPU usage.  Obviously you can kill the process, but you need to research it, and its purpose, and search for bug reports about it, on your version of Ubuntu.

Firefox is famous for using CPU resources, so 20% for FF is probably normal.  I use chromium-browser and it is much lighter on the CPU.

Xorg and Nautilus look normal.

---

### Post by linux_trojan on 2011-07-12
I was on another website forum that logs you off automatically then goes to its main page where it plays a live video.  I was in the forum when I left but on the main page when I came back home, I think plugin-container was associated with that coz it used way less resources when I changed pages.

I think the problem is Firefox.  Its funny, at first everyone said, switch from Internet Explorer to Mozilla, its lighter; then switch to Firefox and Firefox gets bloated, now its Chrome.  Gosh when does it end?

I guess I will just export my bookmarks to Chrome coz I dont like bloated web browsers.

---

