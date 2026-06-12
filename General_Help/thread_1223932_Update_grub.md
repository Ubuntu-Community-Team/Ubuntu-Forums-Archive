---
title: "Update grub"
date: 2009-07-26
forum: General Help
---

### Post by tom66 on 2009-07-26
I've made a change to /boot/grub/menu.lst but my changes on the Grub menu aren't reflected. Is there another step like forcing an update to grub somehow? (I believe grub is installed in /boot/grub because kernel updates seem to manage to update the titles.)

---

### Post by drs305 on 2009-07-26
tom66,

Did you edit and save the file as 'root':
```

gksudo gedit /boot/grub/menu.lst

```

If you open it now do you see the changes you previously made?  If not, what kind of changes were you making?

Do you have mulitple partitions and possibly another /boot partition?

---

### Post by merlinus on 2009-07-26
Try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

and restart.

---

### Post by tom66 on 2009-07-26
I can see my changes. I added an entry for Arch Linux below Ubuntu 8.10 memtest86+.

```

title		Arch Linux
uuid		cc4deec3-d681-46a0-a12c-97f5f43625f3
kernel		/boot/vmlinuz26 root=/dev/disk/by-uuid/cc4deec3-d681-46a0-a12c-97f5f43625f3 ro vga=773
initrd		/boot/kernel26.img

```

Oddly it doesn't have any 9.04 entries which appear in my real grub - is it out of date maybe?

@merlinus: got two numbers from command, which one to choose?

```

grub> find /boot/grub/stage1
 (hd0,7)
 (hd0,9)

```

Thanks.

---

### Post by j0hn00 on 2009-07-26
this always worked for me

```
sudo update-grub
```

---

### Post by tom66 on 2009-07-26
I tried update-grub to no avail.

---

### Post by drs305 on 2009-07-26
> **tom66 said:**
> 
Oddly it doesn't have any 9.04 entries which appear in my real grub - is it out of date maybe?


I think you will find that you have more than one grub menu.lst 

You will need to find the one you are really booting from.

ADDED:

The edit and addition to your last post confirmed you have two sets. You need to find the other menu.lst, which is the one your system is using to boot. Which one contains your Ubuntu system, sda8 or sda10? Apparently your system is booting from the device that is *not* on your system partition, if you are editing /boot/grub/menu.lst and it is not having an effect, and especially if that one doesn't have your current kernel listed. You can change the one you use to boot from with the command that merlinus gave you and then update-grub again.

---

### Post by tom66 on 2009-07-26
Does anyone know where this other mystery menu.lst is? locate doesn't throw any bones:

```

/boot/grub/menu.lst
/boot/grub/menu.lst~
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/var/lib/ucf/cache/:var:run:grub:menu.lst

```

(ignore /boot/grub/menu.lst~ it's created by gedit).

---

### Post by merlinus on 2009-07-26
```
blkid
```will give the uuids for your partitions.  This seems to be the one for archlinux:

cc4deec3-d681-46a0-a12c-97f5f43625f3

So look for a menu.lst that does not contain that uuid in the linux stanzas.

---

### Post by tom66 on 2009-07-27
Thanks, solved the problem.

I had a grub menu.lst on my 9.04 partition and it was booting from that, even though it didn't have a boot flag set...

---

