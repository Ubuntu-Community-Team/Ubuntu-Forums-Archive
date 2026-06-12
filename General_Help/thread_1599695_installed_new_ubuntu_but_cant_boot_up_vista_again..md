---
title: "installed new ubuntu but cant boot up vista again..."
date: 2010-10-18
forum: General Help
---

### Post by centruoides gracilis on 2010-10-18
Sorry if this belongs in another part of the forum. but i need to get this back to vista ASAP. i installed the ubuntu and all is fine. buuut usually when i start my computer up it asks me if i wanna use ubuntu or windows, and now that option isnt showing anymore. its just booting up ubuntu and im a fool and didnt make a back up disc nor do i have the windows CD.. if its even possible to get back to windows please help me...

---

### Post by sikander3786 on 2010-10-18
Can you please post the output of

```
sudo update-grub
```

from terminal.

---

### Post by centruoides gracilis on 2010-10-18
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
chino@chino-KJ310AA-ABA-SR5402FH:~$

---

### Post by sikander3786 on 2010-10-18
It is not seeing your Vista install. Are you sure you didn't overwrite your Vista partition?

Post the output of this bootinfoscript to help us better understand the situation. See instruction on the page.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Wrap the output with proper code tags #.

---

### Post by blueabysm on 2010-10-18
> **centruoides gracilis said:**
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
chino@chino-KJ310AA-ABA-SR5402FH:~$
try```
sudo update-grub2
```, and if you get the same reply, I think maybe something goes wrong with your Vista partition, please post more information as much as possible.

Good luck !  :)

---

### Post by centruoides gracilis on 2010-10-18
> **sikander3786 said:**
> It is not seeing your Vista install. Are you sure your didn't overwrite you Vista partition?

Post the output of this bootinfoscript to help us better understand the situation. See instruction on the page.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Wrap the output with proper code tags #.



im thinking thats what may have happened.. but i dont know how..

---

### Post by centruoides gracilis on 2010-10-18
> **blueabysm said:**
> try```
sudo update-grub2
```, and if you get the same reply, I think maybe something goes wrong with your Vista partition, please post more information as much as possible.

Good luck !  :)


yeah i got the same thing as before..

---

### Post by nothingspecial on 2010-10-18
Do you see an ntfs partition if you type ```
sudo fdisk -l
```

If you don`t, I`m afraid windows is gone.

---

### Post by centruoides gracilis on 2010-10-18
> **nothingspecial said:**
> Do you see an ntfs partition if you type ```
sudo fdisk -l
```If you don`t, I`m afraid windows is gone.

this is what i got

```
  Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfe07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris
                     
```

---

### Post by nothingspecial on 2010-10-18
I`m sorry but it looks like you`ve nuked windows.

---

### Post by sikander3786 on 2010-10-18
> **centruoides gracilis said:**
> this is what i got

```
  Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfe07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris
                     
```
It is time to say Good Bye to Windows as you don't have a Windows Disc at the moment.

Sorry couldn't resist.

You accidently over-wrote your NTFS partition. Post back if you need help reinstalling it once you get the installation media for Windows.

---

### Post by centruoides gracilis on 2010-10-18
> **nothingspecial said:**
> I`m sorry but it looks like you`ve nuked windows.




hahah thats terrible...my photoshop cs3 is gone.. all my music. pictures... ouch.. my brother is gonna kill me lol.    if i manage to get a windows vista CD will it load all my stuff back?

---

### Post by Quackers on 2010-10-18
Quote
buuut usually when i start my computer up it asks me if i wanna use ubuntu or windows, and now that option isnt showing anymore. 

At what point did this happen? Was this a Windows type screen or grub?

---

### Post by sikander3786 on 2010-10-18
> if i manage to get a windows vista CD will it load all my stuff back?

You'll have to reinstall everything I fear.

---

### Post by nothingspecial on 2010-10-18
> **centruoides gracilis said:**
> hahah thats terrible...my photoshop cs3 is gone.. all my music. pictures... ouch.. my brother is gonna kill me lol.    if i manage to get a windows vista CD will it load all my stuff back?

No, everything is gone. Unless you want to pay for forensic recovery.

Back up your stuff.

---

### Post by centruoides gracilis on 2010-10-18
lesson learned... FML.:P

---

