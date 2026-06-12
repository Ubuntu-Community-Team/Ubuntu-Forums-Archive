---
title: "Stuck in Command line"
date: 2011-05-02
forum: General Help
---

### Post by XGC VII on 2011-05-02
I'm stuck in command line with Ubuntu 10.10. I was trying to remove the splash screen. Instead I removed the GUI altogether. Not what I wanted at all. What I need to know is how to undo it.

I know I did something in plymouth (or however it's spelt) that I thought would remove the splash screen. I didn't though and now I'm kinda stuck. I tried to use the command prompt to get back but everything I've tried just seems to not do anything of any importance.

---

### Post by Hedgehog1 on 2011-05-03
Take heart - you are not the first to do this!

I think your best plan of attack is to Purge and Reinstall Grub 2 from the LiveCD/LiveUSB. Here is the HowTo:   [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Be sure the LiveCD/LiveUSB is the same version as your install (10.10).


***The Hedge***

:KS

---

### Post by XGC VII on 2011-05-03
Okay. If someone else doesn't have a solution to it by tomorrow I guess I will have to. I have to make a LiveUSB on my other machine at home and I won't be home until tomorrow. Thanks.

---

### Post by Hedgehog1 on 2011-05-03
Your situation of malfunctioning/missing hardware make maintenance of your system very difficult.

However - it is what it is.

Please give us the exact text you are seeing, and we will try to get you booted up so you can make repairs from Ubuntu.

***The Hedge***

:KS

---

### Post by RoflHaxBbq on 2011-05-03
Reinstall is the best option.

Sorry.

---

### Post by FerretWithASpork on 2011-05-03
Sounds like the OP is booting, but only into a terminal with no graphics.

Were you following any sort of tutorial? If you ran commands to uninstall anything, or changed any files, just go back and reverse whatever changes you made and reinstall anything you took out.

I had something similar happen to me earlier today. I was trying to switch video drivers and ended up with no video drivers so I could only get into terminal; had to reinstall the drivers and then it all worked again.

---

