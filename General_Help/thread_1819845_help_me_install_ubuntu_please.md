---
title: "help me install ubuntu please"
date: 2011-08-06
forum: General Help
---

### Post by dartz003 on 2011-08-06
i am trying to dual boot the latest version of ubuntu. but i cannot even begin to install it let alon dual boot ....

i downloaded ubuntu and made it in the usb version thing. 
have my laptop (toshiba satalite l355-s7902 with default spec) boot from USB. 
get to some kind of ubuntu screen that give me the obtion to boot from USB, or install, test memory, boot from first hard disk, advnace option, help.

i tried both boot from USB, and install and get the same kind of error.... well all those choices produce the same error 

the screen turn black and went throught god know how many lines of words ... 
got so flash.... all i got are these lines : 

begin: preconfiguring networking... ... /scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces/ nonexistence directory
cp: can't create '/root/var/log/': Is a directory done.
mount: mounting/sys on roo/sys failed: no such file or directory
mount: mounting/proc on / root/proc/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init
no init found. Try passing init= bootarg.
BusyBox v1.17.1(ubuntu 1:1.17-10ubuntu) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) "<<<"i can type stuff in here, assuming for the commands stuff">>>

and please help me to dual boot ubuntu with my machine with windows 7 installed. 

ubuntu worked on my laptop with wubi, but i want to actually install ubuntu :D

---

### Post by maxar6 on 2011-08-06
Try installing ubuntu from CD lot more success since USB is still beta on most computers.

---

### Post by cdavid13 on 2011-08-06
So is that the 11.04 your trying to install?

---

### Post by dartz003 on 2011-08-06
yes it is 11.04. @ max, i will try with the CD installation now, but please help me with the USB if ossible since there is a good chance the CD don't work, and it seem ot be a trend that computers r less often to have cd drive now

---

### Post by cdavid13 on 2011-08-06
When I installed it if you go to the partitions and you can change the size of the partitions you select how you want to format the space the was a option at the beging when you select the button on the far left something along the lines of edit paritions or for the mounting point select the back slash "/" this be the root

---

### Post by dartz003 on 2011-08-06
the dvd ins worked, thanks guys. but i still want to know what happened to my usb installation. @ david, my installation never got there, i only got the the screen with a few options, but regardless which 1 i choose, i got a black screen with tons of words running through it.. and ended up with the lines i mention above

---

### Post by cdavid13 on 2011-08-06
also the partition should have the "use as" set for "Ext4 journaling file system" or atleast that is what worked for me. 
Hope this helps

---

### Post by cdavid13 on 2011-08-06
also the partition should have the "use as" set for "Ext4 journaling file system" or atleast that is what worked for me. 
Hope this helps

---

### Post by lastcrusader on 2011-08-24
> **dartz003 said:**
> the dvd ins worked, thanks guys. but i still want to know what happened to my usb installation. @ david, my installation never got there, i only got the the screen with a few options, but regardless which 1 i choose, i got a black screen with tons of words running through it.. and ended up with the lines i mention above
 
I'm in that same boat, but I don't have an optical drive available. I can choose from between different options, but can't seem to get beyond the (initramfs) prompt under BusyBox. I'm trying to dual boot an HP machine with Windows 7 already installed.

---

### Post by dave01945 on 2011-08-24
what program did you use to make the usb i've used a couple before and the only one that consistently works has been unetbootin it is available for windows, linux and mac osx

---

### Post by westie457 on 2011-08-24
@dartz003 and @lastcrusader

Which program did you use to create the LiveUSB because to me it looks like the pair of you have somehow gotten a bad copy either of the original ISO or just a badly created startup Disc. It is also possible that you both have faulty usb sticks.

---

