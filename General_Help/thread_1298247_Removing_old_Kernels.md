---
title: "Removing old Kernels"
date: 2009-10-22
forum: General Help
---

### Post by teward on 2009-10-22
I've got the following kernels listed under Grub (before I get to Other Operating Systems):

(ubuntu 9.04's version)[B]-16
[/B](ubuntu 9.04's version)**-15**
(ubuntu 9.04's version)[B]-11

[/B]How do I get rid of the -15 and -11 kernels so that I can only load the most recent kernel?

---

### Post by winotree on 2009-10-22
Select for complete removal using Synaptic Package Manager.  ;)

---

### Post by teward on 2009-10-22
What should I be selecting under Synaptic Package Manager?  (NOTE: I'm not an advanced Ubuntu user, so you'll have to help me identify the packages)

---

### Post by phillw on 2009-10-22
> **TrekCaptainUSA said:**
> What should I be selecting under Synaptic Package Manager?  (NOTE: I'm not an advanced Ubuntu user, so you'll have to help me identify the packages)


This thread should help ...

[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

It also warns you what NOT to do !!

Take it slow !!

Another thread is here ...

[http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html](http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html)

Have a read of both - Choose which method you prefer.


Phill.

---

### Post by phillw on 2009-10-22
> **TrekCaptainUSA said:**
> What should I be selecting under Synaptic Package Manager?  (NOTE: I'm not an advanced Ubuntu user, so you'll have to help me identify the packages)

On My 9.04 system

```
phillw@piglet:~$ uname -a 
```

Returns

```
Linux piglet 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

```

So, if yours returns the same. Keep 28-16  (The one you're currently using !!) and also 28-15 (The last one, just in case).
28-14, 28-13, 28-12, 28-11 etc can all be removed completely (You'll find 2 entries for each in synaptic package manager if you search for **kernel**

If you find that yout then need to clean up your grub file, so they don't still get listed the following thread shows you how.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

Remember - your version numbers will be different than the example used - keep your current one & the one just before it !!!

Hope that helps,

Phill.

---

### Post by oldfred on 2009-10-22
If you just want to see the most current 2 you can edit menu.lst, I modified mine two show 2.

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

Even easier is to download SUM startup manager from synaptic. It has a variety of settings to update menu.lst.  The kernels do not take a lot of space so housecleaning is not vital unless you are real low on space.

---

### Post by lswartz on 2009-10-22
> **phillw said:**
> On My 9.04 system

```
phillw@piglet:~$ uname -a 
```

Returns

```
Linux piglet 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

```

So, if yours returns the same. Keep 28-16  (The one you're currently using !!) and also 28-15 (The last one, just in case).
28-14, 28-13, 28-12, 28-11 etc can all be removed completely (You'll find 2 entries for each in synaptic package manager if you search for **kernel**

If you find that yout then need to clean up your grub file, so they don't still get listed the following thread shows you how.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

Remember - your version numbers will be different than the example used - keep your current one & the one just before it !!!

Hope that helps,

Phill.

Thanks. That link for editing grub worked great for me on 1 computer as version 11 no longer shows in the package manager. On my laptop, I can't save the edited file menu.lst as I don't have permission & am not sure what I did different. At least it is only a minor thing that shows on boot. My netbook works just fine.

---

### Post by teward on 2009-10-22
> **phillw said:**
> This thread should help ...

[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

It also warns you what NOT to do !!

Take it slow !!

Another thread is here ...

[http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html](http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html)

Have a read of both - Choose which method you prefer.


Phill.

Your first link worked fine.  Got rid of the oldest version, kept the <version>-15 kernel just in case.

Thanks for the help!

TrekCaptainUSA

---

### Post by phillw on 2009-10-23
> **lswartz said:**
> Thanks. That link for editing grub worked great for me on 1 computer as version 11 no longer shows in the package manager. On my laptop, I can't save the edited file menu.lst as I don't have permission & am not sure what I did different. At least it is only a minor thing that shows on boot. My netbook works just fine.


Most odd,

```
[INDENT]gksu gedit /boot/grub/menu.lst
 [/INDENT]
```Should give you temporary super-user access (aka GOD).

don't forget the gksu before the gedit - else, you will not have privalidges to save the edited file.

One for others to ponder :P

Phill.

---

