---
title: "[newbie] how to edit Gnu Grub boot menu list"
date: 2010-06-19
forum: General Help
---

### Post by nguyenxh on 2010-06-19
Hi,

I am a newbie of using Ubuntu. Time to learn and therefore some questions :)

I am installing ubuntu running parallel with my windows XP. When selecting ubuntu option, I have this:

GNU GRUB version 1.98 - 1ubuntu5

Line1: Ubuntu, Linux 2.6.32-22-generic
Line2: Ubuntu, Linux 2.6.32-22-generic (recovery mode)
Line3: Ubuntu, Linux 2.6.32-21-generic
Line4: Ubuntu, Linux 2.6.32-21-generic (recovery mode)
Line5: Microsoft Windows XP Professional (on /dev/sda1)

Yes, I know the reason I have line 4 and 5. Because after installing ubuntu, I performed an update therefore I got the new update to 2.6.32-22 generic. 

However, I would like to keep only the latest generic till now: 2.6.32-22. How can I REALLY remove the older generic for example: 2.6.32-31 in my boot list?

What can I use with recovery mode?

Thanks in advance.

---

### Post by nemiux on 2010-06-19
You could go to /boot/grub and there's a file menu.lst (as i remember) search for lines that doesn't begin with # and you will be able to remove those you don't need

---

### Post by elliotn on 2010-06-19
Isnt it grub.conf as menu.lst is for grub legacy, not sure if its .cfg or conf.

---

### Post by dino99 on 2010-06-19
> **nemiux said:**
> You could go to /boot/grub and there's a file menu.lst (as i remember) search for lines that doesn't begin with # and you will be able to remove those you don't need

better to say nothing than errors

---

### Post by dino99 on 2010-06-19
> **nguyenxh said:**
> Hi,

I am a newbie of using Ubuntu. Time to learn and therefore some questions :)

I am installing ubuntu running parallel with my windows XP. When selecting ubuntu option, I have this:

GNU GRUB version 1.98 - 1ubuntu5

Line1: Ubuntu, Linux 2.6.32-22-generic
Line2: Ubuntu, Linux 2.6.32-22-generic (recovery mode)
Line3: Ubuntu, Linux 2.6.32-21-generic
Line4: Ubuntu, Linux 2.6.32-21-generic (recovery mode)
Line5: Microsoft Windows XP Professional (on /dev/sda1)

Yes, I know the reason I have line 4 and 5. Because after installing ubuntu, I performed an update therefore I got the new update to 2.6.32-22 generic. 

However, I would like to keep only the latest generic till now: 2.6.32-22. How can I REALLY remove the older generic for example: 2.6.32-31 in my boot list?

What can I use with recovery mode?

Thanks in advance.

open synaptic (system admin synaptic) and right click on the package(s) you want to remove (select remove completly)

more info with the links below

---

### Post by nguyenxh on 2010-06-19
> **dino99 said:**
> open synaptic (system admin synaptic) and right click on the package(s) you want to remove (select remove completly)

more info with the links below

Hi dino99,

It works as I expected! Great! Thanks a lot! learnt a new lesson today. :guitar:

What is the difference between the normal one and the recovery one?

Thanks in advance

---

### Post by hardliner on 2011-02-09
> **dino99 said:**
> open synaptic (system admin synaptic) and right click on the package(s) you want to remove (select remove completly)

more info with the links below

For those of us that are new, any help on where do we go to remove these packages inside of Synaptic. There's 1390 packages.

---

### Post by stinkeye on 2011-02-09
In the terminal
```
uname -r
```
will give you your current kernel.


The easiest way for a new user is to download and install 
[**_[COLOR="DarkRed"]Ubuntu Tweak[/COLOR]_**]("http://ubuntu-tweak.com/")
For each kernel you'll have three files with the same version number you can remove.
You should keep 2 kernels.
Ubuntu Tweak doesn't show the current version, so you can remove all but the highest version 
shown in Ubuntu Tweak to leave you with 2 kernels.

---

