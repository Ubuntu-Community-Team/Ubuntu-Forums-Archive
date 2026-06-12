---
title: "installing ubuntu on very old pc ?"
date: 2010-05-31
forum: General Help
---

### Post by mike2507 on 2010-05-31
i would like to instal ubuntu on a very old pc 
the specs are : 
amd athlon 1.4 ghz processor
256 mb ram
3d prohet 4000xt 64 mb grahpics card
20gb hdd

what version of ubuntu should i use

---

### Post by Autodave on 2010-05-31
> **mike2507 said:**
> i would like to instal ubuntu on a very old pc 
the specs are : 
amd athlon 1.4 ghz processor
256 mb ram
3d prohet 4000xt 64 mb grahpics card
20gb hdd

what version of ubuntu should i use

Ubuntu 9.04 and 9.10 will both work: I had them running on a lesser machine w/o any problems.  In fact, I would think that 10.4 would run also.

---

### Post by amite on 2010-05-31
check this one : [http://www.desktoplinux.com/news/NS5855706811.html](http://www.desktoplinux.com/news/NS5855706811.html)

---

### Post by moster on 2010-05-31
> **Autodave said:**
> Ubuntu 9.04 and 9.10 will both work: I had them running on a lesser machine w/o any problems.  In fact, I would think that 10.4 would run also.

Exactly. I try it on some old dirt amd sepron 750 mhz and everything worked. It was visibly slower then mine but I could not believe that everything worked including nvidia I think geforce 2 vga.

---

### Post by Rasa1111 on 2010-05-31
Hi Mike~

I have installed Ubuntu on similar machines, with varying results.
9.10 should work ok, but if not~ check out Lubuntu or Xubuntu. 
They both do well on older, slower machines.

good luck mate

---

### Post by yeats on 2010-05-31
You may want to use the [alternate install disk]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate") if the live CD doesn't run.

---

### Post by sanderj on 2010-05-31
> **mike2507 said:**
> i would like to instal ubuntu on a very old pc 
the specs are : 
amd athlon 1.4 ghz processor
256 mb ram
3d prohet 4000xt 64 mb grahpics card
20gb hdd

what version of ubuntu should i use

A nice machine for Lubuntu.

And if you upgrade the memory to at least 512 MB, a normal Ubuntu / Kubuntu will run too.

---

### Post by quadproc on 2010-05-31
> **mike2507 said:**
> i would like to instal ubuntu on a very old pc 
...
what version of ubuntu should i use
There are some other choices besides Ubuntu as well.  I put Puppy Linux onto a 256 MB P3 machine and it works well.  Another possibility is DSL but unfortunately DSL has not been supported for more than a year so it may be a dead end; too bad because it is sweet on a small system.

One thing to know about Puppy Linux: it runs in single user mode and that user, of course, is root.  This means that you can do anything to anything at any time; there is no "guard" to keep you from doing something dangerous.  But if you keep this in mind then it should work well.

quadproc

---

### Post by yeats on 2010-05-31
+1 for Puppy.  The [newest version]("http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm"), called "Lucid Puppy" or "lupu" is actually Ubuntu-based.

---

### Post by mike2507 on 2010-05-31
damn, to much choises for a linux noob

what i forget to tell in my first post was that the original os ( windows) does not work anymore, it's missing some vital files ,after the bios nothing happens ( lots of errorcodes )so i want to do a fresh instal with ubuntu and completly erase the old os 

for my first ubuntu expirience i like it to be easy 
something like insert cd and click next button ( the rest will come later )

---

### Post by yeats on 2010-05-31
> for my first ubuntu expirience i like it to be easy 
something like insert cd and click next button ( the rest will come later )

Ubuntu (in all its flavors) is very easy to install.  Puppy is less user-friendly, but still relatively straightforward.  I would start with the default Ubuntu CD and see if it loads up for you.

---

### Post by Rasa1111 on 2010-05-31
> **mike2507 said:**
> damn, to much choises for a linux noob

what i forget to tell in my first post was that the original os ( windows) does not work anymore, it's missing some vital files , so i want to do a fresh instal with ubuntu and completly erase the old os 

for my first ubuntu expirience i like it to be easy 
something like insert cd and click next button ( the rest will come later )

Then definitely give Lubuntu a try. :)

 I really wouldntt recommend puppy linux to a newb.

---

### Post by Autodave on 2010-05-31
> **mike2507 said:**
> damn, to much choises for a linux noob

what i forget to tell in my first post was that the original os ( windows) does not work anymore, it's missing some vital files ,after the bios nothing happens ( lots of errorcodes )so i want to do a fresh instal with ubuntu and completly erase the old os 

for my first ubuntu expirience i like it to be easy 
something like insert cd and click next button ( the rest will come later )

They are all going to install about the same way and with similar effort.  Pick one and have fun with it.  After you see it running, you might want to look at a different distro which you can install right alongside the other one and compare tham to see which one to keep.  Or, keep them both. :-)

---

### Post by Rasa1111 on 2010-05-31
Or~

 you could just make a copy of a few different ones~
ie~ Ubuntu, Lubuntu, Xubuntu~
and just try them from the disc before installing anything.

---

### Post by mike2507 on 2010-05-31
i downloaded the default cd , but when i boot up the pc it asks for "boot from ATAPI cd rom"( which i think is the windows install/restore cd and don't have )

can i bypass this and boot directly from the live cd ?

---

### Post by Autodave on 2010-05-31
> **mike2507 said:**
> i downloaded the default cd , but when i boot up the pc it asks for "boot from ATAPI cd rom"( which i think is the windows install/restore cd and don't have )

can i bypass this and boot directly from the live cd ?


I believe that your ATAPI cd is what you want: just let it go ahead.  When it asks to boot from CD, allow it to.  That should get it started.

---

### Post by sanderj on 2010-05-31
> **mike2507 said:**
> i downloaded the default cd , but when i boot up the pc it asks for "boot from ATAPI cd rom"( which i think is the windows install/restore cd and don't have )

can i bypass this and boot directly from the live cd ?

Two things to check:

1) make sure the CD is written correctly. First, easy check: put the CD in the drive of working computer (Windows or Linux), and look at the contents: it should show some files and some directories.

2) make sure your CDROM is the first in the boot order list of your BIOS. See [https://help.ubuntu.com/9.10/installation-guide/i386/pre-install-bios-setup.html#boot-dev-select](https://help.ubuntu.com/9.10/installation-guide/i386/pre-install-bios-setup.html#boot-dev-select)

---

### Post by mike2507 on 2010-05-31
eureka, succes, it works 
i had to change the first boot device in bios 

 al i have to do now is figure out how to connect to the internet using a wireless d-link dwa 140 ( usb adapter)

thanks to everybody for the help so far

---

