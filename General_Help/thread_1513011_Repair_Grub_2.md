---
title: "Repair Grub 2"
date: 2010-06-18
forum: General Help
---

### Post by EngDrewman on 2010-06-18
The boot sector somehow got messed up on a friends computer while updating. I used to know how to do it with the old version, but now that they've updated it and changed everything :rolleyes:, how do you repair the boot sector from a live-CD with Grub 2?

---

### Post by wilee-nilee on 2010-06-18
To vague of a description post the boot script in my sig with the code tags.

Also include what happens when computer is booted and if anything can be booted. Having a grub update which might actually be a upgrade could have left a unfinished upgrade and both grub files in the os. I s this a dual boot is this a wubi, do you see where I'm going here?

---

### Post by EngDrewman on 2010-06-18
When you turn on the computer, after the bios loads it says "operating system missing"

Ubuntu is the only OS on the computer, and I think it is 8.10. (I say I think because I'm email-supporting my friend right now, so I don't have the ability to just uname -r)

---

### Post by wilee-nilee on 2010-06-18
It sounds like a grub legacy to grub2 upgrade that was no finished but this is just speculation. Here is one link that might be helpful.
[http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/](http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/)

The key part is if the new grub2 is working that the last command is run after the boot into the OS after the switch.
```
sudo upgrade-from-grub-legacy
```

Here is a grub2 wiki as well.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)
#11 is the reload from a live cd section.
Don't miss this line in the instructions.
> 
Two methods are presented; both require booting from a LiveCD Ubuntu 9.10, Karmic Koala or later.

So it may be just doing a reload and mount of the partition and once in running the finish command if they have upgraded to grub2.

I am just speculating with all of this, the best thing would be for them to post if possible.

---

### Post by EngDrewman on 2010-06-19
Thanks! I will send that to my friend and see if that does the trick.

---

### Post by progone on 2010-07-29
I found by going into CMOS and changing the order of the IDE drives helps if you seem to be locked out of Ubuntu.  

Right now, I'm in for the first time in days. Hopefully I can figure out how to get Grub2 up and running like it used too.

---

