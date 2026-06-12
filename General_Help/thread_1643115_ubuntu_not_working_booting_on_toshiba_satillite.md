---
title: "ubuntu not working booting on toshiba satillite"
date: 2010-12-11
forum: General Help
---

### Post by robotic1990 on 2010-12-11
ubuntu live cd is not booting on toshiba satellite r630.
just freezes

i tried updating but nothing helped.....


please help.........

---

### Post by Rubi1200 on 2010-12-11
Hi and welcome to the forums :)

What graphics card do you have and how much RAM is installed?

This part makes no sense:
> i tried updating but nothing helped.....
What did you try updating?

---

### Post by robotic1990 on 2010-12-12
ram 4gb and intel hd graphics...

I tried updating the bios and was successful but that did not help...

it is not booting up.
the setup after selection just freezes.

---

### Post by Rubi1200 on 2010-12-12
To get the LiveCD to work, try the following procedure:

Put the LiveCD in and boot up after setting BIOS to boot from the CD/DVD drive;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop.

If you already have Ubuntu installed, let me know as the procedure to boot is different.

---

### Post by robotic1990 on 2010-12-25
cant i install ubuntu directly from my pendrive using unetbootin or something else

---

### Post by Rubi1200 on 2010-12-25
> **robotic1990 said:**
> cant i install ubuntu directly from my pendrive using unetbootin or something else
Yes you can. 

But if the freezes are graphics related then it probably won't make much difference which medium you use.

The instructions I posted before about boot parameters also apply when working with a LiveUSB.

---

