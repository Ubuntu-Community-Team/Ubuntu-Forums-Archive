---
title: "Printer Won't Print but Print Job Goes to Queue"
date: 2009-12-09
forum: General Help
---

### Post by Uadebisi on 2009-12-09
Hi,

After spending countless hours & 10 pages of thread posts, I may have resolved my other issues. If you want to learn more & read 94 posts, knock yourself out ;)...
 [http://ubuntuforums.org/showthread.php?t=1349165&page=10](http://ubuntuforums.org/showthread.php?t=1349165&page=10)

However, to keep this simple I thought it was time to open another thread as my original problems seem to be fixed. Basically, after running Ubuntu successfully for a couple of days on a dual boot w/ Windows, I removed Windows & the problems snowballed. Starting with an inability to boot, where I would get the message "no bootable device" on start-up.  After much time & effort by all involved, I am able to boot normally into my fresh Ubuntu install as removing Windows & growing the partition with my existing Ubuntu install proved unsuccessful. While on the phone w/ a Linux expert, we learned that there was a problem with the USB port &/or the printer that is plugged in to such a port, as when I unplugged the printer, I was again able to boot normally without errors or the Gateway splash screen sticking...yea, that was another problem. 

So, I reinstalled the printer and viola! I was able to boot normally with the printer plugged in. But, I cannot print! When I print, the print job goes to the queue, the machine revs up as if it's going to print, the printer icon appears near the speaker at the top of the screen, then the print job disappears from the print job menu & the little icon goes away. Result...nothing prints! 

Any thoughts? Thanks!

---

### Post by Uadebisi on 2009-12-09
Here is an update...I let the system try to diagnose the problem but it couldn't. It did however print a veeery long log. Here is some info from the log that I thought looked pertinent...

['\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
                   '\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-systray requires Qt4 GUI and DBus support. Exiting.\x1b[0m',
                   '\x1b[35;01mwarning: Unable to connect to dbus. Is hp-systray running?\x1b[0m',

**UPDATE**- As I am still trying to diagnose the problems, I decided to plug my printer into my old Windows machine, that also has the HP printer installed. Just wanted to make sure the printer & usb cables were okay, & they worked fine. So, I plugged the printer back into my machine with Ubuntu installed & just for hoorahs, I tried to print a test page again. Guess what....it printed!!! 

Can someone please explain what the heck is going on here? My last two remaining problems seem fixed (the machine boots into Ububtu even with the printer installed & it prints). But considering all of the problems I have had and that there are still a couple of unanswered questions as to why the last couple of problems are now seemingly fixed, I am wondering what's next?

[B]UPDATE- Well, here's what's next...
[http://ubuntuforums.org/showthread.php?t=1350959](http://ubuntuforums.org/showthread.php?t=1350959)[/B]

---

### Post by bodhi.zazen on 2009-12-11
What printer is it and is it compatible with Linux ?

---

### Post by Uadebisi on 2009-12-11
bodhi,

THANK YOU!!! You don't know how much I appreciate your help!

The printer is an HP 1020 Laser Jet. It worked fine when dual booted with Windows, providing I installed a plugin from HP, as suggested. Actually, although I realize it may have been difficult to follow along, the printer has been working fine, as is explained in my UPDATE in my last post. 

However, I do not fully understand why it works now. All of this can be further explained here:

[http://ubuntuforums.org/showthread.php?t=1349165&page=10](http://ubuntuforums.org/showthread.php?t=1349165&page=10)

I look forward to your reply & please check this newer problem out here:

 [http://ubuntuforums.org/showthread.php?t=1350959](http://ubuntuforums.org/showthread.php?t=1350959)

---

### Post by Uadebisi on 2009-12-11
bodhi-zazen,

You still there? :(

---

