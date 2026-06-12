---
title: "Persistent persistent Persistent Going Nuts Here"
date: 2011-11-16
forum: General Help
---

### Post by fnyahoo on 2011-11-16
I have to use unetbootin,

i have to create persistent usb ubunt 10.04

tried it a couple times, it boots normal, but changes or installed packages dissapear after reboot. going crazy here. 

what is the trick with unetbootin persistent option? why it doesnt work???

---

### Post by dandnsmith on 2011-11-16
You haven't given any detail, apart from Ubuntu version.
Could it be that you've exceeded the space, or made changes too many times?

If the first, try [this page](https://wiki.ubuntu.com/LiveUsbPendrivePersistent), to see if it helps.

---

### Post by efflandt on 2011-11-16
I have not used unetbootin.  You don't have an existing Ubuntu system that could run Startup Disk Creator?  Even with that and persistent data, certain things that happen during boot (kernels, video drivers, etc.) cannot be installed or updated because it boots from a fixed squashfs file system before the persistent data is mounted.  So only installed programs that run after boot would work (and system settings like timezone, etc.).

---

### Post by fnyahoo on 2011-11-16
ok i found the solution, 

- i created a casper-rw partition seperate from home-rw partition.
- installed ubuntu live usb through unetbootin, after installation finished, 
- edit the syslinux.cfg file from different OS because if you start it from the live usb you just created you can't overwrite that file. 
- then starte it regularly from usb and when unetbootin screen comes and showing options press tab at Default and at the end of the code add persistent starting with space. 

this worked for me. everything that i make even the settings stays the same, packages stays everything stays it is amazing. 

what i m trying to do basically is by using unetbootin in the same flash drive have two things 

1- persistent ubuntu
2- (not persistent) Backtrack Live 

so in seperate partitions in the usb drive i individually created live Backtrack first then the Persistent Ubuntu. 

If anybody knows a better of creating both OSs with given specifications in the same usb flash drive, please do let me know. 

I know you can have many Live cd s in the same usb but i needed ubuntu persistent and actually work as persistent. 

this was the solution that worked for me.

---

