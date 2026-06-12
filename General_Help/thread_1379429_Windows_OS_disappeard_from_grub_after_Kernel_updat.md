---
title: "Windows OS disappeard from grub after Kernel update"
date: 2010-01-12
forum: General Help
---

### Post by Onailati on 2010-01-12
Hello,
I'm running a dual boot Vista/Ubuntu Jaunty. I made some changes to the grab menu so that my windows OS would appear at the top of the list .I know I could have changed the default so that Vista would have been highlighted instead of Jaunty. But the reason I moved it to the top is because when I do a kernel update, I would still want Vista to be the default booting OS. Anyways, after the update my Vista OS disappeared from grub. It didn't get deleted because the Vista partition is still accessible from Jaunty. Can anyone help me boot into Vista and preferably make it the default OS even after a Kernel update? I attached part of my menu.lst . 

In an unrelated note, does anyone know how to activate spell check in OpenOffice.org? It doesn't identify errors.
Thanks.

                                  ```
## should update-grub adjust the value of the default booted system
 ## can be true or false
 # updatedefaultentry=false
 

 ## should update-grub add savedefault to the default options
 ## can be true or false
 # savedefault=false
 

 ## ## End Default Options ##
 

 title        Ubuntu 9.10, kernel 2.6.31-17-generic
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=37233bfc-ed76-4396-b204-7b4f0b15b73b ro quiet splash  
 initrd        /boot/initrd.img-2.6.31-17-generic
 quiet
 

 title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=37233bfc-ed76-4396-b204-7b4f0b15b73b ro  single
 initrd        /boot/initrd.img-2.6.31-17-generic
 

 title        Ubuntu 9.10, kernel 2.6.31-16-generic
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=37233bfc-ed76-4396-b204-7b4f0b15b73b ro quiet splash  
 initrd        /boot/initrd.img-2.6.31-16-generic
 quiet
 

 title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=37233bfc-ed76-4396-b204-7b4f0b15b73b ro  single
 initrd        /boot/initrd.img-2.6.31-16-generic
 

 title        Ubuntu 9.10, kernel 2.6.28-17-generic
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=37233bfc-ed76-4396-b204-7b4f0b15b73b ro quiet splash  
 initrd        /boot/initrd.img-2.6.28-17-generic
 quiet
 

 title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=37233bfc-ed76-4396-b204-7b4f0b15b73b ro  single
 initrd        /boot/initrd.img-2.6.28-17-generic
 

 title        Ubuntu 9.10, memtest86+
 uuid        37233bfc-ed76-4396-b204-7b4f0b15b73b
 kernel        /boot/memtest86+.bin
 quiet
 

 ### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Mickser_52 on 2010-01-12
Open office problem.
Go to Tools in the main menu
choose Options
then Language setting
then writing aids and check spelling as you type box.

When I wanted Windows to boot first I moved it above ubuntu in menu.lst can't explain why it disappeared or how you can get it back

---

### Post by Woody1987 on 2010-01-12
Grub gets overwritten when a new kernel is installed. You need to edit /etc/default/grub to make persistent changes. Change GRUB_DEFAULT as required. Then run /usr/sbin/update-grub as root.

---

### Post by michy99 on 2010-01-12
If you put another os first, you need to put it before the Automagic Kernals section or it will get lost when you upgrade kernals.

---

### Post by ajgreeny on 2010-01-12
> **Woody1987 said:**
> Grub gets overwritten when a new kernel is installed. You need to edit /etc/default/grub to make persistent changes. Change GRUB_DEFAULT as required. Then run /usr/sbin/update-grub as root.
Sorry, Woody, but the OP is using Jaunty, not karmic, so probably still using legacy grub

@ Onailati
Don't try what Woody told you as you will get nowhere, I'm afraid.

Try adding the following to your menu.lst file at the top of the menu part.  This assumes Vista is on the first partition of your first hard disk.  If different, change the line **rootnoverify    (hd0,0)** to take account of your partition arrangement.

```
title        Microsoft Windows Vista
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by michy99 on 2010-01-12
> **Woody1987 said:**
> Grub gets overwritten when a new kernel is installed. You need to edit /etc/default/grub to make persistent changes. Change GRUB_DEFAULT as required. Then run /usr/sbin/update-grub as root.

I think you are talking about Grub2. Since the OP is using Jaunty, he almost certainly has legacy Grub.

EDIT: What he said.

---

### Post by Woody1987 on 2010-01-12
Whoops, sorry about that, yea, just ignore my previous comment.

---

### Post by Onailati on 2010-01-13
> **Woody1987 said:**
> Whoops, sorry about that, yea, just ignore my previous comment.


Oooopss. I don't know what happened. I must have been very tired when I typed my first post. I'm using 9.10 which is Karmic Koala. I apologise to everyone for this mistake. What should I do in this case?
Again, sorry.

---

### Post by ajgreeny on 2010-01-13
So you're running karmic, but appear to have a menu.lst file, so I presume you must have done an online distro version upgrade from jaunty to karmic.

That probably means you are still using legacy grub, so the windows stanza I suggested may still be the way to go.  See my post #5 with the relevant info.

---

### Post by oldfred on 2010-01-13
Grub legacy's menu.lst updates all entries in the "automagic area". If you just put your entries above the Ubuntu stanzas then it will get overwritten on every update. You need to put it many lines above - find these lines:

# Put static boot stanzas [COLOR=Red]before [/COLOR]and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]Put windows stanza here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

---

### Post by ajgreeny on 2010-01-13
If you want to make sure windows boots by default you can also use the savedefault option at the end of the windows stanza:-

```
title        Microsoft Windows Vista
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
savedefault
```and the usual **default 0** line near the top of the file should be edited to **default saved**.

There is one other change you need which will be to make sure that update-grub does not change the whole thing back again, so you will need to uncomment the line just above the menu stanza entries from

## should update-grub add savedefault to the default options
## can be true or false
[COLOR=Blue]# savedefault=false[/COLOR]

to 
## should update-grub add savedefault to the default options
## can be true or false
[COLOR=Blue]savedefault=true[/COLOR]

Make sure you back up the file first just in case.

---

