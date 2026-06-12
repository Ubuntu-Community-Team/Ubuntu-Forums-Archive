---
title: "no /boot/grub/menu.lst"
date: 2010-03-09
forum: General Help
---

### Post by dd1linux on 2010-03-09
When I start up, grub gives me about 8 choices, and I wanted to get rid of the old ones.  This is something I have done before, but there is no menu.lst under /boot/grub.  So where is it getting the options from?  How do I change it without a menu.lst there?  I am scared to simply write a new one, because if I get something wrong.  I will be screwed (because I cant backup the currrent one, because its not there!)

---

### Post by howefield on 2010-03-09
What version of grub are you using, sounds like grub2 ?

There is no menu.lst in grub2.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Method X on 2010-03-09
> **dd1linux said:**
> When I start up, grub gives me about 8 choices, and I wanted to get rid of the old ones.  This is something I have done before, but there is no menu.lst under /boot/grub.  So where is it getting the options from?  How do I change it without a menu.lst there?  I am scared to simply write a new one, because if I get something wrong.  I will be screwed (because I cant backup the currrent one, because its not there!)

Hi
I think you just updated your grub.
An lates grub versions uses file grub.cfg.

No menu.lst anymore ;)

---

### Post by dd1linux on 2010-03-09
Both of you were exactly correct, and I got my problem solved.  Thank you so much for the quick replies.

---

### Post by egalvan on 2010-03-09
> **dd1linux said:**
> , and I got my problem solved..

Putting the solution here would be of help to others who may have the same problem.

It's the Ubuntu Way.

---

### Post by JaRRoslav on 2010-03-09
Hello, I had this "problem" (I'd rather call it annoying thing), too, so I installed ubuntu-tweak and there is option to remove old kernels.

---

### Post by CouchMaster on 2010-03-13
edit this file as root - /etc/default/grub
then run as root 'update-grub'
and there you go!

---

### Post by Choragos on 2010-03-13
When Ubuntu updates the kernels, will your changes get overwritten?  I suppose that's what the /etc/default/grub file is for huh...

---

