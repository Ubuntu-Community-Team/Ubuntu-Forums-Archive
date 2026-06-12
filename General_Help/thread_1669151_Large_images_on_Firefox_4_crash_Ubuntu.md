---
title: "Large images on Firefox 4 crash Ubuntu"
date: 2011-01-17
forum: General Help
---

### Post by joao82 on 2011-01-17
Hi,
I don't know if this problem is related to Firefox or Ubuntu but I can't find any answers for similar situations.
The thing is, when I open/view a large image on Firefox 4( for example in any image board site) sometimes the whole system freezes. The only way the get out of this crash is turning the power off.
Now, I normally wouldn't worry too much, this being a beta browser running from an untar-ed folder. The big issue is that when I re-boot the browser's profile folder saved on another partition has damaged files and Ubuntu now only has read-only permissions for that entire FAT32 partition. So then I have to dual-boot to Windows, check the drive for errors, fix them and reboot back to Ubuntu... uff.
And this happens everyday, around 10% of the times that I open an image larger than my screen on Firefox 4 (any beta) running in 10.10.
I've opened the same image on Windows using the same profile folder, and the browser didn't crash. Neither the OS.
Does this happen to more people? Is it a Firefox or an Ubuntu issue?

Anyway, I would like to know if there is a way to check for errors while on Ubuntu... but because it opens the partition as read-only from boot I really can't do anything with it.

thanks in advance

---

### Post by lovinglinux on 2011-01-17
There was a similar thread posted about a week ago, but I can't find it right now and I don't remember the solution. However, I think that is caused by video driver issues or memory issues.

---

### Post by lithopsian on 2011-01-17
You are using a Firefox 4 beta version?  It may have some graphics acceleration features running.  These are often still buggy and you may be hitting something like that when you use a lot of memory.  Try downloading the beta 9 release which is slightly more stable.  Also change the layers.accel preferences to force all acceleration off and see if that helps.

If you really want to delve into it all, go to the Firefox forums and you can go crazy.  At the end of the day there aren't too many huge gains to be made from acceleration on Linux at the moment and it can cause problems.  You could download the Grafx Bot add-on and try to run that.  If it consistently crashes then you are hitting an acceleration bug.

---

### Post by joao82 on 2011-01-17
Ok. I don't think I'm using any third party or non-free video drivers but I'll check into that.
Oh, I'm already using beta 9. It updates faster than my sig hehe
I'll definitely turn the acceleration off.
Thanks

---

### Post by utkjamie on 2011-06-08
I've been having this problem over the past week or so running Firefox 4 under Debian Squeeze. It isn't consistent, but I can load a single large image in Firefox 4 and it locks up my entire computer--which can be disastrous with the EXT4 filesystem, since it often means some data loss. 

While FF4 is choking on single images, I can load the same image in Chrome and then multiple other tabs with large images and there are no problems whatsoever. Maybe this is a memory issue or a video driver issue, but whatever it is, it seems to be the fault of Firefox since Chrome doesn't have the problem.

---

