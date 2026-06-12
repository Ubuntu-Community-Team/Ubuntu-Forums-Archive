---
title: "ubuntu live: cannot execute binary file"
date: 2012-04-02
forum: General Help
---

### Post by Necromancer3 on 2012-04-02
hi!

i'm using Ubuntu live CD, 64bit from a USB stick.
im trying to run the luac executable with no success. (downloaded from luabinaries)

at first i couldn't run it since i've got "permission denied", and found out that i cannot change the permissions since its not on linux files system. ive dealt with that using the root (sudo -s) and "source luac50"
but now it spits:
bash: source: luac50: cannot execute binary file

---

### Post by dcstar on 2012-04-03
> **Necromancer3 said:**
> hi!

i'm using Ubuntu live CD, 64bit from a USB stick.
im trying to run the luac executable with no success. (downloaded from luabinaries)
.........

And you did download the 64-bit version?

---

### Post by Necromancer3 on 2012-04-03
i surely hope so, its the ubuntu-11.10-desktop-amd64.iso


Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Vaphell on 2012-04-03
and what does *file luac50* say?

---

### Post by Necromancer3 on 2012-04-03
luac50: ELF 64-bit LSB executable, IA-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.4.0, not stripped

---

### Post by jerome1232 on 2012-04-03
If I recal correctly IA-64 is intels first attempt at making a 64 bit only architecture, amd's x86_64 pretty much killed it off.

aka you got the wrong architecture for your processor. IA-64 does not equal x86_64.

---

### Post by Necromancer3 on 2012-04-04
what should i download then?
got an intel core i5 processor, and i need the file to be compiled on a 64bit platform.

---

### Post by Vaphell on 2012-04-04
ia is itanium which was a failed server arch from intel
just go after amd64/x86_64

[http://kent.dl.sourceforge.net/project/luabinaries/5.0.3/Executables/lua5_0_3_Linux26g4_64_bin.tar.gz](http://kent.dl.sourceforge.net/project/luabinaries/5.0.3/Executables/lua5_0_3_Linux26g4_64_bin.tar.gz)

luac50:  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.0, not stripped

---

### Post by Necromancer3 on 2012-04-04
same thing:

source luac50
bash: source: luac50: cannot execute binary file

file luac50
luac50: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.0, not stripped

whats wrong?

---

### Post by fiatveritas on 2012-04-04
If you're having trouble running a bin file you need to change the permission on the file so you can run the program. The way to do this by going into the directory that has the file and typing: ```
chmod +x application.bin
./application.bin
``` In addition, if you're running Ubuntu Live you might have trouble installing programs on the live Ubuntu because Ubuntu needs to save the programs somewhere and if you don't have enough space on your USB (assuming you're running off USB drvie) then you won't be able to install new programs.

---

### Post by fiatveritas on 2012-04-04
Here's another point: usually Ubuntu.com has good iso files and I use the [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") on Windows (yes, Windows. Although, now that I'm mediocre at using Ubuntu I make my live USBs off Startup Disk Creator in Ubuntu) to make my live USB drives. This should help you out--I hope.

---

### Post by jerome1232 on 2012-04-04
> **fiatveritas said:**
>  then you won't be able to install new programs.

Not entirely true, they can be saved in ram, I've installed programs using a live cd in the past (testdisk, luks, lvm2, etc... with no hitch.

---

### Post by fiatveritas on 2012-04-04
> **jerome1232 said:**
> Not entirely true, they can be saved in ram, I've installed programs using a live cd in the past (testdisk, luks, lvm2, etc... with no hitch.
I was alluding to when I installed Java on my USB because the Java Environment is too big for RAM (on my netbook that doesn't have a lot of RAM).

---

### Post by Necromancer3 on 2012-04-04
its all good to know, although i already looked it up before posting here. if you'd read my first post you'd know that.

i'll summarize it: 
i need to compile a text file (lua code) with luac50 on a 64bit platform.

im running ubuntu 64bit from a USB stick, downloaded executable from luabenaries. first when i tried to run it it said i dont have permission, abit searching with google and i fount its because its not a linux file system, and i cant change the permssion using chmod.
ive dealt with that using root in the terminal (sudo -s), but now it spits "cannot execute binary file"

both the executable and the linux are now x86_64, but it still doesn't run.
any suggestions?

---

### Post by jerome1232 on 2012-04-04
Try it with sudo -i, so that your getting an environment as if you logged in via the root account (-s doesn't something slightly different)

I'm shooting in the dark at this point, but i think lua is complaining about not being able to execute some other binary.

---

### Post by Necromancer3 on 2012-04-06
same result with the sudo -i  :frown:

---

### Post by Necromancer3 on 2012-04-10
bump

help anyone?

---

