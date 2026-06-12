---
title: "installed apps disappear"
date: 2011-07-15
forum: General Help
---

### Post by linuxgerg on 2011-07-15
i have installed ubuntu 11.04 on a usb san disk (pen drive linux) with an easy installer
 
i boot and get the main window, go to synaptic package manager, do a reload of the repository and install gns3 (network simulation tool)
 
when i reload the app is gone
 
i do see that space is occupied on the san drive but after reboot this space isn't occupied anymore
 
is this specific to my type of pendrive install?
 
how can i save the apps even after a reboot?
 
can you point where to install software or does package manger do this, if so where?

---

### Post by ajgreeny on 2011-07-15
Did you actually install ubuntu or are you running a live USB system from the drive?

It is possible to make a "persistent live USB" which will retain all added packages after a reboot, and I think that is possible with other utilities than the ubuntu-startup-disk-creator, such as pendrive-linux, though the ubuntu application is the only one I have ever used.

---

### Post by linuxgerg on 2011-07-18
> **ajgreeny said:**
> Did you actually install ubuntu or are you running a live USB system from the drive?
 
It is possible to make a "persistent live USB" which will retain all added packages after a reboot, and I think that is possible with other utilities than the ubuntu-startup-disk-creator, such as pendrive-linux, though the ubuntu application is the only one I have ever used.
 
i now see that i didn't make the pendrive linux with the app installer persistent
 
is there any way to make it persistent after installation has completed?

---

### Post by dandnsmith on 2011-07-18
At one stage I think I did this as there was a version for which the persistance script didn't work.
You needed a casper-rw file on the pendrive, which gets (automatically) mounted as a loop filesystem.
I'd hate to try to explain it, as I did it back in April 2009, and I feel that things may be differently organised now (I haven't revisited the exercise, partly because of limited use, and partly because it was only an experiment, to see if I could do it).

---

### Post by linuxgerg on 2011-07-20
> **dandnsmith said:**
> At one stage I think I did this as there was a version for which the persistance script didn't work.
You needed a casper-rw file on the pendrive, which gets (automatically) mounted as a loop filesystem.
I'd hate to try to explain it, as I did it back in April 2009, and I feel that things may be differently organised now (I haven't revisited the exercise, partly because of limited use, and partly because it was only an experiment, to see if I could do it).

sound difficult :)

is there some tutorial on the web on how to do this? i can't find one

why wouldn't there be such an option? if you have enough free space on your usb device you should be able to imho to just turn on this feature right?

or do you really need a separate partition or something?

---

### Post by dandnsmith on 2011-07-20
Not a special partition, just a file of the correct size (all the rest, possibly) where you create an ext3 filesystem.
My memory problem concerns what you might need to populate it with, as I was specifically creating a larger version and copying the content across at one stage.
I got all the information from the pendrivelinux site, but some of it was enhanced by examining some specific script files.

---

