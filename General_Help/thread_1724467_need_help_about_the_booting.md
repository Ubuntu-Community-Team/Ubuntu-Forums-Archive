---
title: "need help about the booting"
date: 2011-04-08
forum: General Help
---

### Post by wxuyec on 2011-04-08
[SIZE=4]my system is ubuntu 10.04. I don't know why recently when I boot my laptop,
after I input my password in the gdm interface, the screen will be black for about
30 seconds, and the LED light for the hdd is always on. It keep reading hard disk.
does anybody meet this problem? is it about ureadahead?

Thank you in advance.[/SIZE]

---

### Post by sanguinoso on 2011-04-08
Does the system boot correctly after hanging for 30 seconds or are you saying it fails?

---

### Post by Rubi1200 on 2011-04-08
What are the computer specifications, especially RAM and graphics card?

---

### Post by wxuyec on 2011-04-08
> **sanguinoso said:**
> Does the system boot correctly after hanging for 30 seconds or are you saying it fails?

yes, the system can boot correctly.

---

### Post by wxuyec on 2011-04-08
> **Rubi1200 said:**
> What are the computer specifications, especially RAM and graphics card?

I think this is the graphics card:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

cpu:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz
stepping        : 10
cpu MHz         : 800.000
cache size      : 4096 KB

as for the RAM I just know it is 1.5G.
are these information enough?

---

### Post by Rubi1200 on 2011-04-08
Thanks for posting the information.

Okay, so let's see if we can rule out the graphics as being an issue.

When the computer starts and you see the GRUB menu, when the entry for Ubuntu is highlighted press "e" to edit.

Navigate using the arrow keys and find the line that ends with quiet splash.

Add this, i915.modeset=1, so the line looks like this:

> quiet splash i915.modeset=1 
Note the space after splash and before the next parameter.

Then, "Ctrl" + "x" to boot.

If this helps, we can make it more permanent afterwards.

---

### Post by wxuyec on 2011-04-08
> **Rubi1200 said:**
> Thanks for posting the information.

Okay, so let's see if we can rule out the graphics as being an issue.

When the computer starts and you see the GRUB menu, when the entry for Ubuntu is highlighted press "e" to edit.

Navigate using the arrow keys and find the line that ends with quiet splash.

Add this, i915.modeset=1, so the line looks like this:

 
Note the space after splash and before the next parameter.

Then, "Ctrl" + "x" to boot.

If this helps, we can make it more permanent afterwards.

thank you, i will try it. i try to use the bootchart to analyze what happened. 
but i found the log files are so difficult to understand. here I attach them below.
I don't know whether it will help.
the extension name for the two attachments should be .tgz. I changed them to
.tar because .tgz files are not supported as attachments here.

---

### Post by wxuyec on 2011-04-08
> **Rubi1200 said:**
> Thanks for posting the information.

Okay, so let's see if we can rule out the graphics as being an issue.

When the computer starts and you see the GRUB menu, when the entry for Ubuntu is highlighted press "e" to edit.

Navigate using the arrow keys and find the line that ends with quiet splash.

Add this, i915.modeset=1, so the line looks like this:

 
Note the space after splash and before the next parameter.

Then, "Ctrl" + "x" to boot.

If this helps, we can make it more permanent afterwards.


Thanks, It seems it works. now the time for booting cut of about 30 seconds.
tomorrow i will check it once again. thank you.
and i have add that in the /etc/default/grub.

---

### Post by Rubi1200 on 2011-04-09
Okay, good that it worked for you.

Let me know if you need more help with anything.

---

