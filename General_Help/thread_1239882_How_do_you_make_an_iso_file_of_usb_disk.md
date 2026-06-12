---
title: "How do you make an iso file of usb disk?"
date: 2009-08-14
forum: General Help
---

### Post by jis on 2009-08-14
I tried to copy the device file to a file in another device, but the file will get too big.

---

### Post by Psycho.mario on 2009-08-14
```
dd if=/dev/<USB-DEVICE> of=~/Desktop/usb.iso
```

---

### Post by Bachstelze on 2009-08-14
> **Psycho.mario said:**
> ```
dd if=/dev/<USB-DEVICE> of=~/Desktop/usb.iso
```

Please refrain from posting if you don't know.

```
mkisofs -o usb.iso /media/usbdisk
```

---

### Post by Psycho.mario on 2009-08-14
I have used that command to write the contents of my USB drive to a DVD actually, i know it's not the proper way, but it works.

---

### Post by Bachstelze on 2009-08-14
I *highly* doubt that. Unless you have the power to magically convers a FAT32 filesystem into a ISO9660 one.

---

### Post by P4man on 2009-08-14
No offence but Psycho.mario answer was not wrong. If you use dd, the resulting image wont be ISO9660 but a raw image, but no one said it had to be ISO9660. 

If the OP wants to use the image file to duplicate on other sticks, if anything it would be a problem if its ISO9660. I read his post as wanting to copy, so I assume he wants to duplicate his stick

Even if he wants to write it to cd, the raw image created with dd works, although its a bit odd to have vfat on a cd, and maybe windows wont like it, so  I agree your solution is  better. Doesnt mean you have to snipe at someone for giving another response.

---

### Post by Psycho.mario on 2009-08-14
My method does work, it just may not seem correct to you, it worked for me.

---

### Post by Bachstelze on 2009-08-14
> **P4man said:**
> No offence but Psycho.mario answer was not wrong. If you use dd, the resulting image wont be ISO9660 but a raw image, but no one said it had to be ISO9660. 


The thread title clearly says "How do you make an iso file of usb disk?"

---

### Post by jis on 2009-08-14
Thanks HymnToLife. Your solution creates a smaller file.

---

### Post by harry2006 on 2009-08-14
@jis, you should thank Psycho.mario as well.... :-)

---

### Post by jis on 2009-08-14
> **harry2006 said:**
> @jis, you should thank Psycho.mario as well.... :-)

I guess the result is same as what ```
cp /dev/<USB-DEVICE> ~/Desktop/usb.iso
``` generates. (Both required sudo here.) Both commands create way too big file; I suppose it is the capacity of the source device, but I did not take the time to wait them to finish.

---

### Post by P4man on 2009-08-14
> **HymnToLife said:**
> The thread title clearly says "How do you make an iso file of usb disk?"

Strictly speaking, I guess you`re right, although many people use ISO when I suppose they should use the term *image*. Precious few  posters here would know the difference. In fact, Im still very much in doubt the OP needs a CD image.

jism if you intend to burn to a cd, HymnToLife gave you the best answer. If you need to restore the image to an usb stick, having an ISO is not what you want (if you restore it, the stick will be read only). dd makes an exact copy, even of unused space, so for smaller size you can use:

```
dd if=/dev/usbtick | gzip -c  > image.img.gz
```

to restore the image:

```
gzip -dc image.img.gz | dd of=/dev/usbstick
```

---

### Post by jis on 2009-08-14
> **P4man said:**
> 
 dd makes an exact copy, even of unused space, so for smaller size you can use:

[CODE]dd if=/dev/usbtick | gzip -c  > image.img.gz[/CODE


I doubt I need that. Your way is much slower than the ISO way and generates bigger file. You can create bootable USB media from an ISO image using UNetbootin.

---

### Post by P4man on 2009-08-14
Well if you don't say, then I can't guess what you're trying to do.. but you can speed up dd a lot by adding a bigger blocksize:

dd if=/dev/usbtick bs=2048| gzip -c  > image.img.gz

it will copy as fast as the stick goes. But it does copy every byte, even unused bytes, so if you're imaging a 16GB stick that has 1GB data on it, it will be slow and you'll end up with a 16GB (uncompressed) image. If you know the size, you can limit the scope of the copy but.. well. whatever.

Just realize by making an ISO you're converting the usb filesystem to a read-only ISO9660 file system. UNetbootin can convert an iso to a bootable stick, but it expects a standard live cd as input, and if you got something entirely different on that stick, then I got no clue what you'll end up with, but you'll find out...

---

