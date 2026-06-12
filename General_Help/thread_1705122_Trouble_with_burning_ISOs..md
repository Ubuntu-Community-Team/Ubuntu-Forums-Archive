---
title: "Trouble with burning ISOs."
date: 2011-03-11
forum: General Help
---

### Post by 23Andrew on 2011-03-11
I don't know if this is in the right place, but I'll ask anyway.

It's definitely a noobish question I'm guessing.

I have a strange obsession with collecting ISOs of different distros, that I never use. Now I'm trying to burn one to a memory stick, except so far, I've had no luck, with getting it working. Any ideas guys?? 

Thanks in advance guys.

Maverick (Netbook) is the game.

---

### Post by andrewthomas on 2011-03-11
Either do this:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Or just use dd

```
$ dd if=image.iso of=/dev/sd[x]
```where *image.iso* is the path to the iso file and */dev/sd[x]* is your USB device. 
**Warning: *****Make sure to use /dev/sdx and NOT /dev/sdx1.*** **This is a very common error!**

---

### Post by PoHandle on 2011-03-11
You can also use UNetbootin to write the image to a USB stick.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by 23Andrew on 2011-03-11
> **andrewthomas said:**
> 
```
$ dd if=image.iso of=/dev/sd[x]
``` Permission denied.
> **andrewthomas said:**
> 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Already tried this... but retrying.

I'll let y'all know how I get on, thanks for the help. :) EDIT: Didn't work. I tried to boot it up, but it wouldn't boot. Also, did I have to su root before the dd?? *tries*

---

### Post by andrewthomas on 2011-03-11
> **23Andrew said:**
> Permission denied.

I don't see why you wouldn't have write permissions to the flash drive but then just try with sudo.

---

