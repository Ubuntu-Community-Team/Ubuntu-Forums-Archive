---
title: "Black screen on attempted install"
date: 2012-04-07
forum: General Help
---

### Post by Hobomank on 2012-04-07
I am using a dell optiplex-260 with 1gb ram and 40gb hdd
I cannot install any flavor of ubuntu. other distros, like puppy linux and DSL(damn small linux) will boot live. when I place the cd in my computer I see the graphical ubuntu logo loading and then whenever it gets to the screen where i select my language the screen goes black, before it does so I cannot recall exactly but I think it says "checking NTDS server" and below that "checking bluetooth" with two dots beside each one. then this screen disappears and I am left with a blsack screen and the occasional glitchy presence that resembles a gui box.
 
I tried deleting the partition in puppylinux with gparted for a clean install only to be met with similar results. Then finally I performed an entire systems wipe(I didnt have much data on there anyway). then i tried a system wipe with > sudo dd if=/dev/zero of=/dev/sda bs=1M while in puppy linux.
 
Im running out of options, is it possible that I permanently damaged my HDD with the system wipe and partition removal?

---

### Post by Hobomank on 2012-04-07
> **Hobomank said:**
> I am using a dell optiplex-260 with 1gb ram and 40gb hdd
I cannot install any flavor of ubuntu. other distros, like puppy linux and DSL(damn small linux) will boot live. when I place the cd in my computer I see the graphical ubuntu logo loading and then whenever it gets to the screen where i select my language the screen goes black, before it does so I cannot recall exactly but I think it says "checking NTDS server" and below that "checking bluetooth" with two dots beside each one. then this screen disappears and I am left with a blsack screen and the occasional glitchy presence that resembles a gui box.
 
I tried deleting the partition in puppylinux with gparted for a clean install only to be met with similar results. Then finally I performed an entire systems wipe(I didnt have much data on there anyway). then i tried a system wipe with while in puppy linux.
 
Im running out of options, is it possible that I permanently damaged my HDD with the system wipe and partition removal?
 
Did i forget to include anything?  I apologize if i did. this only PC I have :(

---

### Post by CottonCandy on 2012-04-07
When you boot the Ubuntu live CD and click "Try Ubuntu" does it load the desktop session? 

If the CD is not working properly, maybe you just need to burn a new Ubuntu CD. Make sure you check the md5sum/sha256sum of the .iso file and burn the CD at the slowest speed possible. 
[How To MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")  [How To SHA256SUM]("https://help.ubuntu.com/community/HowToSHA256SUM")

---

