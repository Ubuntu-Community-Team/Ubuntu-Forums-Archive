---
title: "Ubuntu Terminal screen on startup"
date: 2011-05-02
forum: General Help
---

### Post by dannyboyalpha on 2011-05-02
I recently upgraded to Ubuntu 11.04, and I installed it via the Update Manager and restarted as normal. But, as I went on my dual boot OS selection screen and selected Ubuntu, this message appeared:

init: udevtrigger main process ( 398 ) terminated with status 1
init: udevtrigger post-stop process (404) terminated with status 1
init: udevmonitor main process (397) killed by TERM signal
The disk drive for / is not yet ready or is not present
Continue to wait; or Press S to skip mounting or M for manual

I'm afraid to do anything after this screen...

Anyone know what this is and how it can be solved?

---

### Post by dprofili518 on 2011-05-11
The problem seems to be that Linux is not recognizing the hard drive correctly. 

To do this, you have to manually mount it and partition it.

To determine the hard drive path, type this into the terminal:

sudo lshw -C disk

This should give drive information.

To partition it using command-line, you have to use fdisk.

sudo fdisk /dev/sdb 

[FONT=Verdana]Follow the instructions in the terminal. 

This should work. If nothing happens, post a reply with any error messages that appear.


[/FONT]

---

