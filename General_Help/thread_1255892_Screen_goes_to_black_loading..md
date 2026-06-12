---
title: "Screen goes to black loading."
date: 2009-09-02
forum: General Help
---

### Post by backmask on 2009-09-02
I just installed Ubuntu Studio (Hardy) on my MacBook. I partitioned the hard drive to run Studio on the larger portion of the hard drive, while I continue to run Mepis on the smaller part. I'm booting from the master boot record, so when I turn the computer on I get a choice of whether to boot into Ubuntu or into Mepis. 

The first time I selected "Ubuntu Studio" from the list, it went past the loading screen, then gave me a series of colorful static before getting stuck at a black screen. The second time I try, Ubuntu loads up perfectly! I make sure the jack sound server works, then I update the system. The update goes fine, and tells me to restart.

Then, while restarting the computer again, it does the same thing. Goes past the loading, then fizzes and after a while goes to black. I try again, and this time the menu gives more options for kernels to load: the updated kernel as well as the old kernel. I try to load the newly installed kernel: same deal. What gives?

---

### Post by backmask on 2009-09-03
Update: 
I can log on just fine by going into recovery mode, and then starting the system from there. I don't see much difference between that and a normal boot, except that when you start the system from recovery mode, you don't go past any fancy loading screens. So I'm going to try loading it with the graphics. I've found the lines in  /boot/grub/menu.lst that I need to edit (just remove "Quiet Splash"), but I don't know how to gain permissions to make that change. Do I have to log in to Root? I don't even remember setting up root during the install. If I log in to "sudo", can I make the change? How do you even log into sudo?

---

### Post by sully101 on 2009-09-03
I may be wrong but in recovery mode you will be logged in as root. Just to clarify "sudo" is a command that a normal user would use to gain root priveleges.

If you can get a command line then use vim to edit the files you need to.

---

### Post by backmask on 2009-09-03
The user's guide to Ubuntu that I was reading made it sound like there was no way to log into root at all in Ubuntu, only small ways to borrow root permissions.

Anyway, I figured it out by trolling around guides on the internet. sudo gedit /boot/grub/menu.lst got me into the file I needed, with the permissions to edit it. I like the scrolling white-on-black text anyway, now that the splash screen is gone.

I've never heard of vim, what is it?

---

