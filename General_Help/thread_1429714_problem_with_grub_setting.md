---
title: "problem with grub setting"
date: 2010-03-14
forum: General Help
---

### Post by justborn on 2010-03-14
i am not able to boot,the booting process keeps going on and on.....i think there is something wrong wid this, please help me.....```
recordfail
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set bea1dea5-9b97-42a8-b287-44010ebeb\35f
linux /boot/vmlinuz-2.6.32-16-gneric rppt=UUID=bea1dea5-9b97-42a8-b\287-44010ebeb35f ro splash quite splash
initrd /boot/initrd.img-2.6.32-16-generic
```

---

### Post by rahilm on 2010-03-14
i suppose the spelling of generic in the fifth line has to do something with it...
here is mine for reference
```

    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set 23337842-4f5c-4d5e-bf05-7a3f3d5a28c4
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=23337842-4f5c-4d5e-bf05-7a3f3d5a28c4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic

```

i think its root=UUID instead of rppt

---

### Post by t.rei on 2010-03-14
It might. I really think computers should implement the dwim(x) function. (Do what I mean to x). :)

---

### Post by justborn on 2010-03-15
i hope these outputs might help....

ls
```
(hd0) (hd0,5) (hd0,1) (fd0)
```

ls (hd0)
```
Device hd0:Partition table
```

ls (hd0,5)
```
partition hd0,5: unknown filesystem
```

ls (hd0,1)
```
partition hd0,1: filesystem type ext2
```

ls (fd0)
```
Device fd0: filesystem cannot be accessed
error: no such disk
```

---

### Post by justborn on 2010-03-15
> **rahilm said:**
> i suppose the spelling of generic in the fifth line has to do something with it...
here is mine for reference
```

    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set 23337842-4f5c-4d5e-bf05-7a3f3d5a28c4
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=23337842-4f5c-4d5e-bf05-7a3f3d5a28c4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic

```

i think its root=UUID instead of rppt
sry dude that was a typo....anything else???

---

### Post by rahilm on 2010-03-15
root=UUID="the uuid of your partition".. its probably right because it differs from partition to partition...
what exactly is the issue you are facing?? you say booting process goes on and on..how? is it followed by an error message or the computer simply reboots?
how about trying sudo update-grub
..restart and see whether the issue is fixed.

Update:
I can't really confirm this..but in this case you can simply remove the "root=UUID=....." it basically does nothing special if you got the "set root" line right.

---

### Post by justborn on 2010-03-15
i meant plymouth keeps going on and on.....

and ya i tried editing the set root line from (hd1,1) to (hd0,1)
and then cntrl+x,to boot ,but still the same...... am i supposed to save ,after i make that change ,if so how??

---

### Post by rahilm on 2010-03-15
you said plymouth..is this lucid or karmic??

  set root should be (hd0,1).. but i guess that didn't work for you.

---

### Post by justborn on 2010-03-15
it's lucid...

and yes i tried (h0,1)....

do u know a way to edit the /boot/grub/grub.cfg from the grub commandline???

---

### Post by rahilm on 2010-03-15
well if it is lucid then i have no idea. plymouth is still buggy. I was having the same problem you are having when i installed lucid to one of my usb hard drives. then i did a complete re-install and now things are working fine.

I don't know of anyway of editing grub.cfg from the command line.. There is however some thing  you can do.
1)You can boot to a live-cd and  then edit grub.cfg
2)If you still have windows, make a grub.cfg file and when you get to grub prompt enter coomand line and then
```
configfile (hdX,Y)/path.to.the.file
```

---

### Post by mhgsys on 2010-03-15
Press **e** to edit a line, **c** to create a line, escape to go back, and **b** to boot

When you got it booting, make sure to edit the /boot/grub/menu.lst to make the correct settings permanent.

edit; :-x 

[SIZE="3"][SIZE="1"]I overlooked the fact it's lucid.[/SIZE][/SIZE]

---

### Post by justborn on 2010-03-20
i got i working.....the actual problem was with the BIOS....it would reset the date evertime i wanted to boot.....for time being i'm having to set the correct harware timing before i boot...i'll soon try to find a solution for that...

thanks all....

---

### Post by mhgsys on 2010-04-05
nice to know you've fixed the problem

a new battery in the mobo will do

---

