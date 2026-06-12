---
title: "EMERGENCY: Ubuntu won't start"
date: 2011-03-02
forum: General Help
---

### Post by Cheryl J. Jones on 2011-03-02
Hi, I've had ubuntu just one week and are very pleased with it (when it work).
When i start my computer I can Choose to run ¨Ubuntu, with Linux 2.6.35-25-generic¨ or ¨Ubuntu, with Linux 2.6.35-25-generic (recovery mode.)¨ I've tried both but all i come to is a commando line wee it stands many operations and falings. The commando line runs until the, i don't now what to call it but in the end it stands 
¨(initframfs)¨ and that the /sbin/init is missing. Please help me and don't do it to advanced ?

---

### Post by rvchari on 2011-03-02
> **Cheryl J. Jones said:**
> Hi, I've had ubuntu just one week and are very pleased with it (when it work).
When i start my computer I can Choose to run ¨Ubuntu, with Linux 2.6.35-25-generic¨ or ¨Ubuntu, with Linux 2.6.35-25-generic (recovery mode.)¨ I've tried both but all i come to is a commando line wee it stands many operations and falings. The commando line runs until the, i don't now what to call it but in the end it stands 
¨(initframfs)¨ and that the /sbin/init is missing. Please help me and don't do it to advanced ?

just shut down computer and restart. let it boot into the default settings. your initramfs problem should be resolved. if not then try for recovery mode. this will take a lot of time to get into a stage where the screen displays options. choose the one "boot normally" and you will land at $ prompt. use your log in and password and after that type startx
you should get back your gui.

i get into trouble like this a lot. i follow this what i told you. when no other options work, use live cd and run fsck to check your disk.

---

### Post by Fryie on 2011-03-02
I had a similar problem once, so maybe this will help, if the above suggestion doesn't work:

1. From another computer (or another OS on the same computer) download a linux distribution and burn it to a CD/USB drive/whatever ("Live CD"). Follow the instructions on the website of the distribution. Notice: For some reason I had problems accessing my hard disk using an Ubuntu Live CD. I suggest using a smaller distribution in any case, e.g. I tried [Slax]("http://www.slax.org").
2. Boot your computer from the Live CD (you might have to change the boot order in your BIOS)
3. Find out where your hard drive is (e.g. /dev/sda1) and **make sure it's unmounted!**
4. Bring up a terminal and type "sudo e2fsck -C0 -p -f -v /dev/sda1" (replace with the address of your hard drive)

See if this works

---

