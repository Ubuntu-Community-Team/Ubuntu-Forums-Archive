---
title: "BURG/GRUB install error"
date: 2010-03-18
forum: General Help
---

### Post by Da CalebMan on 2010-03-18
Hey guys, Now I know the minute you look at this title, you're gonna think, "Oh, no. Another idiot newbie that's messed his PC up..." And it's true. I've really messed up. And I mean really. Please help me though :(.

Here's the story. I tried to download BURG, as instructed by this site ([OMG UBUNTU]("http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html"))

I thought that the process might be too dangerous, so I removed all the packages that had were part of Grub2. GRUB however I left installed. After a reboot, The PC comes up to a menu that looks just like this:

```
BURG version 1.98+20100309-1

Minimal BASH line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_
```

I tried typing 'boot', but it said, "no loaded kernel."
What on earth have I done to my PC! Please help me. I can't find my Live CD, or get in any-way.

I don't know what to do!:(
~Caleb

---

### Post by wjm on 2010-03-18
This is actually hilariously common with people today (and yes, this thread did make me say that exact same phrase).  I fix this at work all of the time ...

The reason is because something has removed GRUBs understanding of where it's menu.lst and bootfiles are (or has removed them entirely).  Let's figure out which one that is first .

**these instructions assume you know what your kernel version is.  initrd is the same as kernel.**

type:

linux /boot/vmlinuz-2.6.XX-generic root=/dev/sda2  loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.XX-generic 
boot

That should work - although you may have to do something a little fancier like pass along the root information (as it would appear in the grub.cfg)

---

### Post by Da CalebMan on 2010-03-18
Thankyou sooo much for replying!:D

I entered the text just as you had it typed, but it said, 
"error: file not found"
Although I can't exactly comment on this, as this is far past my grasp of understanding, I do remember upgrading my kernels very recently.

Anything else you might think be the cause?
~Caleb

---

### Post by rnerwein on 2010-03-18
hi
just try this in the grub rescue mode:
1. ls
2. set prefix=(hdX,Y)/boot/grub     ( where X and Y are is your device )
3. set root=(hdX,Y)
4. insmod /boot/grub/linux.mod
5. linux /vmlinuz root=/dev/sdXY ro          ( there is a link of your newest kernel at /  )
6. intrd /intrd.img
7. boot
good luck
ciao

---

### Post by Da CalebMan on 2010-03-18
Thanks guys. I borrowed my friends installation disc.;)
Hopefully I can save all my files and reinstall successfully.

Anyway, thanks for the help.:)
I appreciate that there are so many people out there that are still wiling to lend a helping hand;)

~Caleb

---

### Post by TBallS on 2010-06-27
I did exactly the same thing, this is how i solved it. 

ok firstly i used the 'Booting from the rescue mode' from here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

first you need to find out which partition your linux kernel is installed on. type:

**search -f/vmlinuz**

your looing for a result like: hd0,msdos5 

just so you dont get confused about different hd labels they can be written like this:

hd0,msdos5 = hd0,5 = sda5
or
hd2,msdos3 = hd2,3 = sdc3

next load the linux module, type in the following command:

**insmod /boot/burg/linux.mod**

Now rembering your partition number, use the correct sdxx partioin number that matches what you found earlier. load the linux kernel using the following command (example for hd0,msdos5) :

**linux /vmlinuz root=/dev/sda5 ro**

next type:

[B]initrd /initrd.img
[/B]
and finaly type:

**boot**

Now you should boot into Ubuntu as normal. 
To fix the problem open 'ubuntu software center' 
search for 'grub'
uninstall the 'burg' entry
look for the installed grub entry and uninstal it makeing sure you dont turn your computer off at this point.
remember which version you uninstalled and install it again. 

once this is complete you should be able to reboot and the old grub screen comes up. i guess you could now have another attempt at reinstalling burg, if your that bothered. 

im sorry if this is shitly written or if i didnt use the correct terminal commands the whole way through, im not a very experienced Ubuntu user and this is how i fixed my problem. i hope it helps.

---

### Post by Da CalebMan on 2010-07-05
Thanks :)

---

### Post by saurabhprimal on 2011-01-23
Hi,

I followed the procedure above.But there is a small problem i am encountering.I remember typing sudo burg-install /dev/sda in the terminal.So even if I have removed burg from the Software centre the original Grub has not been restored.Please help me getting rid of burg and restoring grub.
Thanks.

---

### Post by saurabhprimal on 2011-01-23
sudo grub-install /dev/sda
That solved it.Thanks a lot!! Just informed myself that i should not mess with grub and burg..

---

