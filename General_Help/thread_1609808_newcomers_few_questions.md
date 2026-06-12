---
title: "newcomers few questions"
date: 2010-10-30
forum: General Help
---

### Post by coreyscx on 2010-10-30
first off, im loving ubuntu, i changed to ubuntu completly..nomore windows for several reasons, but ofcourse being a newbie, im wondering a coupel things like where the program files are, also..what does the "sudo" command mean? does it just give you admin rights?? what are proprietary drivers, and can i emulate most games under wine? thanks guys :)

---

### Post by Eddison on 2010-10-30
Hi dude,

I'm a bit of a newbie myself- 8 months. After a while you begin to see how microsoft has an agenda NOT to help you but get you to employ microsoft engineers, software companies etc etc. Its just a big big scam, but it looks good huh? Try this guide; [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
I recommend reading this or similar. It will save you allot of frustration, as Ubuntu is very different. There are no program files as such. Sudo is a command which gives you privileges to alter sensitive programs- but this is a whloe subject in itself. Grab some coffee, cake, and read this little guide. A real time saver.
There are more guides here; [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Eddison

---

### Post by matsuzine on 2010-10-30
Hey, not a direct answer to your question but a suggestion...  There is a great podcast called 'Going Linux'.  It's aimed at helping newer linux users learn more about their systems.  I'm an avid listener, and I learn new stuff from them all the time -- sometimes just a great piece of software that I didn't know about.  Check it out...

[http://goinglinux.com/](http://goinglinux.com/)

---

### Post by madmax75 on 2010-10-31
> **coreyscx said:**
> first off, im loving ubuntu, i changed to ubuntu completly..nomore windows for several reasons, but ofcourse being a newbie, im wondering a coupel things like where the program files are, also..what does the "sudo" command mean? does it just give you admin rights?? what are proprietary drivers, and can i emulate most games under wine? thanks guys :)

Program files are usually in /bin and /usr/bin I believe, but you should not mess around with these directories. System settings are usually in /etc, your personal program settings are usually under your home directory as hidden dot files (for example, .mozilla). You can hide and unhide these in your Nautilus file manager window by pressing ctrl+h.

So there is'nt really a "central" place where program files are. The package manager is responsible for taking care of programs and where their files get installed at.

"Sudo" gives you temporary root (=admin) rights to do certain risky tasks, like installing programs, doing system maintenance and so on.

Proprietary drivers are closed-source code drivers. Ubuntu uses open source drivers as a default, but there is also an option to use the closed-source drivers provided by the makers of different hardware. If you can't get good performance with open source drivers, you might want to install the closed drivers that the hardware makers have produced. Usually you might want to install proprietary drivers to get your video card to work properly and so on.

Wine can run some Windows software (not just games but apps too), but it is not a magical solution to run all Windows software. You can also install a virtual computing environment (like VirtualBox or Qemu) and run Windows (and it's programs) in that.

---

### Post by Verbeck on 2010-10-31
to find where a program is located run *whereis programname* from a terminal window. it would give a link to the executable.

sudo gives temporary root/admin rights, read up [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info

and proprietary drivers are close source drivers. they usually give better performance than the open source ones, but for ethical reasons, some people doesn't use it

the list of tested apps in wine can be listed at [http://appdb.winehq.org/](http://appdb.winehq.org/)
if an app has platinum rating, it usually works without any problems

hope this helps

---

### Post by Vigh on 2010-10-31
so totally hilarious, guess what happened, my father who has been a microsoft user his entire life, well last night his computer crashed from a virus, and he has finally had the last straw with windows, he asked me to switch him to linux, not a single windows computer in the household now! W00T YEAH! all the best with your linux experimentation, hope all turns out well for you

---

