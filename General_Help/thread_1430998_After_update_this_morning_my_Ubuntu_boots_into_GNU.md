---
title: "After update this morning my Ubuntu boots into GNU GRUB version 1.97~beta4"
date: 2010-03-16
forum: General Help
---

### Post by crazysexycool on 2010-03-16
HI 

I am experiencing the above problem after doing a update what is the solution to this ?

Thanks

---

### Post by lordskid on 2010-03-16
> **crazysexycool said:**
> HI 

I am experiencing the above problem after doing a update what is the solution to this ?

Thanks

But I say that that is not a problem. unless you cannot boot your linux.
Been using grub2 1.97~beta for at least 6 months now.

---

### Post by crazysexycool on 2010-03-16
Hi it will not boot into ubuntu that is where my problem stems from

---

### Post by prodigy_ on 2010-03-16
Provide more background. Does GRUB menu show up? If so, then what happens when you try to boot into Ubuntu?

---

### Post by crazysexycool on 2010-03-16
Hi here is a bit more background i am using ubuntu 9.10 installed using wubi started up this morning did a update asked me to restart i said yes then the following screen comes up.

try hd0 

then goes to GNU GRUB version 1.97~beta4

minimal BASH like line editing is supported for the first word , TAB lists possible command completions. Anywhere else TAb lists possible device/file completions 

hope this is a bit more insight.

---

### Post by lordskid on 2010-03-16
try to type ls see if you get anything.

---

### Post by crazysexycool on 2010-03-16
> **lordskid said:**
> try to type ls see if you get anything.


hi have typed LS here is the output 

(loop0) (hd0) (hd0,1) (hd1) (hd1,1) (fd0)

---

### Post by prodigy_ on 2010-03-16
Boot from Live CD and check what's in your **/boot/grub/grub.cfg** file. Don't edit it directly. Instead edit custom script with ```
gksu gedit /etc/grub.d/40_custom
``` and then update grub: ```
sudo os-prober
sudo update-grub
```

If you're not sure how to edit your grub2 configuration, post the output of ```
mount
``` command and the contents of your **/boot/grub/grub.cfg**.

---

### Post by lordskid on 2010-03-16
if you have your live-cd fixing it would be easier done from there

[http://karmic-koala.totalh.com/index.php?p=1_5_What-to-do-if-Grub2-gets-busted]("http://karmic-koala.totalh.com/index.php?p=1_5_What-to-do-if-Grub2-gets-busted") see this page.

---

### Post by crazysexycool on 2010-03-16
Hi if i don't have a live CD available is there another way to perform this action ?

---

### Post by lordskid on 2010-03-16
try to type the command 

hd0 is the first hardisk this might be your windows
hd1 is a second harddisk most probably your linux so try

insmod ext2
set root=(hd1,1)
linux (hd1,1)/vmlinuz
initrd (hd1,1)/initrd.gz
boot

if you were to be able to boot using this then there is not much problem. all you have to do now is to open a terminal and type this command

sudo update-grub

or

sudo grub-mkconfig -o /boot/grub/grub.cfg

---

### Post by crazysexycool on 2010-03-16
> **lordskid said:**
> try to type the command 

hd0 is the first hardisk this might be your windows
hd1 is a second harddisk most probably your linux so try

insmod ext2
set root=(hd1,1)
linux (hd1,1)/vmlinuz
initrd (hd1,1)/initrd.gz
boot

if you were to be able to boot using this then there is not much problem. all you have to do now is to open a terminal and type this command

sudo update-grub

or

sudo grub-mkconfig -o /boot/grub/grub.cfg


Hi thanks for the advice i typed in linux (hd1,1)/vmlinuz

and it returned file not found...

---

### Post by lordskid on 2010-03-16
hmmm.... okay try 

ls (hd0,1) 

see if vmlinuz is there if not try

ls (hd0,1)/boot/grub

see if it gives errors

---

### Post by crazysexycool on 2010-03-16
Hi 

Hd0 gives me unknow file system and hd1 gives me the same error

---

### Post by lordskid on 2010-03-16
hmmm try 

```
insmod ntfs
```

then

```
ls (hd0,1)
```

---

### Post by theozzlives on 2010-03-16
> **lordskid said:**
> if you have your live-cd fixing it would be easier done from there

[http://karmic-koala.totalh.com/index.php?p=1_5_What-to-do-if-Grub2-gets-busted]("http://karmic-koala.totalh.com/index.php?p=1_5_What-to-do-if-Grub2-gets-busted") see this page.

Live CD won't help with WUBI.

---

### Post by lordskid on 2010-03-16
> 
insmod ext2
set root=(hd1,1)
linux (hd1,1)/vmlinuz
initrd (hd1,1)/initrd.gz
boot



sorry this was wrong.

do this instead
```

insmod ext2
set root=(hd1,1)
linux /vmlinuz
initrd /initrd.gz
boot

```

---

### Post by Prinz_Fritz on 2010-03-16
i have same problem with wubi and ubuntu

i havent found menue.list in grub .... is this the bug ?

i dont have a rescue-cd too

how can i create de menue.list in grub ?

like /usr/sbin/update-grub ? but how in grub-console ?

---

### Post by lordskid on 2010-03-16
okay now I think I got it. 

substitute (loop0) for every (hd1,1) from above.

---

### Post by lordskid on 2010-03-16
> **Prinz_Fritz said:**
> i have same problem with wubi and ubuntu

i havent found menue.list in grub .... is this the bug ?

i dont have a rescue-cd too

how can i create de menue.list in grub ?

like /usr/sbin/update-grub ? but how in grub-console ?

are you also getting the grub prompt? can you ls (loop0) for me if it shows something?

---

### Post by Prinz_Fritz on 2010-03-16
yes i have same thing ... i think is an bug from update last night ...

ls (loop0):

Dvice loop0: Filesystem type ext2, last modify....yadda ....

i have try the commands from upstairs but i come to the grub-console too ...

---

### Post by crazysexycool on 2010-03-16
> **lordskid said:**
> hmmm try 

```
insmod ntfs
```

then

```
ls (hd0,1)
```


Hi output for the above is Partition hd0,1: file system type ntfs, UUID28cbb0d4cbad532

---

### Post by crazysexycool on 2010-03-16
> **lordskid said:**
> sorry this was wrong.

do this instead
```

insmod ext2
set root=(hd1,1)
linux /vmlinuz
initrd /initrd.gz
boot

```

Hi after typing in linux /vmlinuz it says file not found

---

### Post by lordskid on 2010-03-16
even after the boot command?

did you replace all the (hd0,1) or (hd1,1) with (loop0)

---

### Post by Prinz_Fritz on 2010-03-16
yes, lordskid

> 
insmod ext2
set root=(loop0)
linux (loop0)/vmlinuz
initrd (loop0)/initrd.img
boot
/initrd.gz is not , but /initrd.img


but i come again to grub-console ...

i think i should make a menu.lst in /boot/grub/ ... the problem: when i boot the system then loading the vista-bootloader first and take normal way to boot (wubi)ubuntu 

but how i create a file with grub-console ??

---

### Post by crazysexycool on 2010-03-16
> **lordskid said:**
> even after the boot command?

did you replace all the (hd0,1) or (hd1,1) with (loop0)

i have just done the insmod ext2 set root=(loop0) linux /vmlinuz initrd /initrd.gz boot 

pressed enter and gave me another command line.

---

### Post by crazysexycool on 2010-03-16
> **Prinz_Fritz said:**
> yes, lordskid

/initrd.gz is not , but /initrd.img


but i come again to grub-console ...

i think i should make a menu.lst in /boot/grub/ ... the problem: when i boot the system then loading the vista-bootloader first and take normal way to boot (wubi)ubuntu 

but how i create a file with grub-console ??

This command worked says now that the Kernel panic  - not syncing  :VFS: unable to mount root fs on unknown wn-block(1,0)

---

### Post by lordskid on 2010-03-16
this is beyond me. I was hoping that would help. anyway I'll see what I can do and post here again.

---

### Post by crazysexycool on 2010-03-16
> **lordskid said:**
> this is beyond me. I was hoping that would help. anyway I'll see what I can do and post here again.

Hi thanks ill await your reply

---

### Post by AnthonyBeldt on 2010-03-16
can i tweak ubuntu as we can tweak any window operating system?

---

### Post by crazysexycool on 2010-03-16
Hi anyone got some new info for me??

---

### Post by crazysexycool on 2010-03-16
Hi found this thread but it is not helping should i try and substitute some off the commands?

[http://ubuntuforums.org/archive/index.php/t-1339541.html](http://ubuntuforums.org/archive/index.php/t-1339541.html)

---

### Post by crazysexycool on 2010-03-16
Hi i am in serious need off help with this

---

### Post by crazysexycool on 2010-03-16
HI any word on this as yet ??

---

### Post by Helkaluin on 2010-03-16
<speculative>Did you, by any chance, did a hard reboot before this happened? It could possibly be a corrupted ntfs block on the wubi image.

In that case try running chkdsk in Windows.</speculative>

---

### Post by crazysexycool on 2010-03-17
Hi no i didnt do a hard boot and i have run a chkdsk in windows it says everything is ok 

i am hoping there is a fix for this soon i really dont want to start a fresh install.

---

### Post by ben.walker on 2010-03-22
> **AnthonyBeldt said:**
> can i tweak ubuntu as we can tweak any window operating system?

No You Can nOt.

---

### Post by peter.hopkins on 2010-03-28
> **ben.walker said:**
> No You Can nOt.


Well i do not think we can tweak any linux based operating system.

---

### Post by crazysexycool on 2010-03-29
Hi back to the original problem any ideas on how to fix this??

---

