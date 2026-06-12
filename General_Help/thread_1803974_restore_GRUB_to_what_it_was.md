---
title: "restore GRUB to what it was"
date: 2011-07-14
forum: General Help
---

### Post by Kubischbuntu on 2011-07-14
Hi,

I know the title looks like a very common question but this is not what it seems. Here is the story:
I was running Kubuntu 10.4 on this machine and didn't do the upgrade to 10.10 when it became available because it didn't offer anything I wanted at the time. Then along came 11.4 and this I wanted. However since I had skipped a release I couldn't just upgrade. So I ended up doing a fresh install of 11.4 in a different partition ending up with 2 KUBUNTU systems in a dual boot setup. (you can never have too much KUBUNTU) So far so good. 
I used 11.4 for quite a while until recently I found something that didn't work there but used to work in 10.4. Easy I thought - I booted into 10.4 and sure enough it still worked there. While I was there it told me that there were a million updates outstanding so I went ahead and applied them ... this is where things went somewhat haywire. The updates installed the old 10.4 version of GRUB again. This has the unfortunate side-effect that I now cant control GRUB from 11.4 anymore AND it doesn't list new kernels that get implemented in 11.4. 
SO after this long back story (sorry about that) - my question is - how can I get my native 11.4 version of GRUB back?
Thanx!

---

### Post by Quackers on 2011-07-14
Ok, boot into the new 11.04 installation and open a terminal and run ```
 sudo grub-install /dev/sda
```
NOTE The above assumes that you have installed 11.04 to /dev/sda and that /dev/sda is your bootable hard drive in bios. Change "dev/sda" if necessary.

---

### Post by Bucky Ball on 2011-07-14
Open a terminal in 10.04:

sudo update-grub

That will get you back a menu list at boot. Once you get that far, if you want 11.04 to run grub again (for whatever reason) boot into 11.04 and install this:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Run it and it will install the 11.04 grub to the MBR again. That easy. ;)

* Just noticed Quackers fix; that might be more straightforward ...

---

### Post by Quackers on 2011-07-14
That looks like a useful tool Bucky Ball. I've not used it as I have become practised doing it the old way :-)  Many mistakes have been made with grub on my system :-)

---

### Post by Kubischbuntu on 2011-07-14
Thanx guys that solved it - quick and easy!

---

### Post by Quackers on 2011-07-14
Nice one :-)

---

### Post by Bucky Ball on 2011-07-14
Good work. ;)

---

