---
title: "Is my hard drive failing?"
date: 2011-08-17
forum: General Help
---

### Post by stinkeye on 2011-08-17
Running 11.04 Unity with nvidia gfx.
9 out of 10 boots it hangs at the plymouth screen.

Besides this I have issues with having to unplug and replug both the mouse and usb headset to get them to work, when it does boot.

If I boot into recovery mode and select **reboot into file system check**
it starts every time with no usb issues.
Once booted I don't notice anything else that might indicate a failing hard drive.
I also have XP installed on the same drive and haven't noticed anything abnormal when I play games on windows.

I set the boot process up to do a file system check at every boot.
Adds about 10 secs to the boot time but at lest it doesn't hang.

My qestion is as in the thread title....
**Is my hard drive failing?**
:confused:

---

### Post by aeiah on 2011-08-17
probably not, no. if plymouth is just hanging, maybe there's a race condition somewhere, and this gets alleviated by running a disk check?

see what your /var/log/messages say, and see if there's any SMART error reports for your drive (maybe using [gsmartcontrol ]("http://gsmartcontrol.berlios.de/home/index.php/en/Home"))

---

### Post by stinkeye on 2011-08-17
Thanks for the info.
By a race condition, do you mean something in the boot process is starting out of order?
I think I'll just leave it with the longer boot time as 
I don't think it's something I can easily solve.
I usually switch the computer on when I get home from work and
then go and make a coffee anyway. ;)

---

