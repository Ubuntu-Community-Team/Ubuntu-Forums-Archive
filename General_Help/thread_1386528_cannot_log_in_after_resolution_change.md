---
title: "cannot log in after resolution change"
date: 2010-01-20
forum: General Help
---

### Post by winchendonsprings on 2010-01-20
I just installed ubuntu 9.10 32-bit on my parents computer. My dad was having this weird problem where it would only randomly allow him to log in every few tries. Let's say every 1 out of 12 tries.

I believe I have figured what is keeping him from logging in. Only on his user is there an issue with logging in. Only on his desktop have I turned the screen resolution down. From 1152 to 1024.

The usual sequence goes like this - 
- I choose his user
- I enter his correct password
- It appears to be logging in, half the log in sound happens and the splash screen runs for 6 or so seconds
- The splash screen flickers between a 1152 and 1024 resolution
- Reverts back to the log in screen, his desktop is never visible.

any ideas on how to fix this? The computer in question is a Compaq Presario circa 2000-2001 if that makes any difference. I have not looked into the video card make yet

---

### Post by djchandler on 2010-01-20
> **winchendonsprings said:**
> I just installed ubuntu 9.10 32-bit on my parents computer. My dad was having this weird problem where it would only randomly allow him to log in every few tries. Let's say every 1 out of 12 tries.

I believe I have figured what is keeping him from logging in. Only on his user is there an issue with logging in. Only on his desktop have I turned the screen resolution down. From 1152 to 1024.

The usual sequence goes like this - 
- I choose his user
- I enter his correct password
- It appears to be logging in, half the log in sound happens and the splash screen runs for 6 or so seconds
- The splash screen flickers between a 1152 and 1024 resolution
- Reverts back to the log in screen, his desktop is never visible.

any ideas on how to fix this? The computer in question is a Compaq Presario circa 2000-2001 if that makes any difference. I have not looked into the video card make yet

Try this. I had a similar problem using the proprietary Nvidia driver with 9.04. I had to edit the display settings as root/su. Some settings with the Nvidia control panel can only be saved as root due to where those files are being stored. It kept defaulting to a screen resolution as high as possible, regardless of the fact I wanted 1280x960 instead of the 1280x1024 it kept giving me. Once I did that, no troubles since except the screensaver doesn't work now, but I'm not really worrying about that. This is on a desktop with an Nvidia MX 400 gpu running Mythbuntu 9.04 that has subsequntly been updated to 9.10.

[http://ubuntuforums.org/showthread.php?p=8145792#post8145792](http://ubuntuforums.org/showthread.php?p=8145792#post8145792)

9.10 pushes the envelope, IMHO being a beta for the 10.04 LTS to be released this spring. You may want to step back to 8.04 LTS until then or switch to Debian Lenny (5.x) for a more stable experience.

If all else fails, log in under another account, get root, and back-up Dad's home directory. If you can't copy externally, move his files somewhere else on the disk. As root, make a directory in the main directory and change its permissions so anybody has read and write privileges and copy his home directory to it. Make sure you change the permissions on his files too. Delete his account, and create a new account for Dad. Then he can copy them back to his home directory under the new account.

If you can't change the resolution settings globally as root, the latter could be your only recourse.

---

### Post by winchendonsprings on 2010-01-20
Thanks, It does by default use the highest resolution it sees fit, I'm sure. I dont even know if it has a nvidia card in it, but if it does I bet getting those drivers will fix it. It's funny you mention that about the nvidia proprietary drivers not letting you save your resolution settings without root to the save folder. Because a few months ago It took me awhile to realize that for the computer I'm on now.

The strange thing is that the 1 out of 12 times that my dad logs in and it works, you'd never know there was a problem. The splash screen loads as it should and gives way to his desktop with the smaller 1024 resolution.

If that doesn't do the trick I will revert back to 8.04

---

