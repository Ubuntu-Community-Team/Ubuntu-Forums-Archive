---
title: "Puppy Linux and Ubuntu dual boot help please"
date: 2011-04-02
forum: General Help
---

### Post by trollger on 2011-04-02
Hi every one.

I currently have Ubuntu 10.04 installed and I am trying  to install Puppy Linux (Dual Boot).

I believe Puppy is successfully installed but it does not appear in the GRUB Menu. :(

By the way I installed puppy on the second partition(ext3) of my first  hard drive(Windows is on the first and Ubuntu takes up my entire second  drive)

I have searched for tutorials related to GRUB and they keep referring to a file called menu.ls or something like that which I can't seem to find. :confused:

Anyway, I'm sure this is a simple fix I just don't know how to add Puppy to the GRUB boot menu. Help would be much appreciated. :D 

Thank you for reading.

---

### Post by rbc on 2011-04-02
Assuming you're using grub2, did you update grub after you installed Puppy?

Open terminal and type:
sudo update-grub

By the way, you do that command while using Ubuntu, not Puppy

---

### Post by trollger on 2011-04-02
Ok I did that and now I have a menu.lst file :)

Now for step 2 what do I add to it?

[EDIT] 
I saw your edit and I did do it in Ubuntu.

Also you said assuming I have Grub 2 how would I figure out what GRUB Version I have
 [/EDIT]

---

### Post by rbc on 2011-04-04
If you’ve updated Ubuntu from a release prior to 9.10 then you’re probably using grub legacy, unless you went out of your way to install grub2. If you’ve done a clean install after 9.10 then you’ll probably have grub2. Open terminal and type:
grub-install –v
The result will be some number. 0.9x will be grub legacy. If you have grub2, then the result will be 1.9x.
If you have grub2, then the previously provided command SHOULD HAVE added Puppy to the grub entries. If you have grub legacy, then you need to manually add Puppy to the menu.lst file. Is that file blank? I ask that because grub2 doesn't use the menu.lst file

---

### Post by trollger on 2011-04-15
Hey everyone sorry I never posted back, I fixed the problem
First off I was using GRUB Legacy (eg version 0.x) 
I simply ran 

```

sudo apt-get install grub2 && update-grub

```It found all my partitions and operating systems automatically.

Thanks for all the help.

---

