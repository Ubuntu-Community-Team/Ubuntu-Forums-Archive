---
title: "what can i use to rip an .iso??"
date: 2011-01-09
forum: General Help
---

### Post by JuicyCouture on 2011-01-09
whats the "toast" or "imgburn" equivalent for ubuntu?

---

### Post by wilee-nilee on 2011-01-09
Brasero, do you mean burn not rip correct?

---

### Post by JuicyCouture on 2011-01-09
no i mean rip

like make an image of a cd

my sister needs me to get one of her school programs that comes on CD - onto a usb, so im gonna rip an .iso and have her mount it

which is my next question - what do you linux people use to mount image files?

---

### Post by wilee-nilee on 2011-01-09
> **JuicyCouture said:**
> no i mean rip

like make an image of a cd

my sister needs me to get one of her school programs that comes on CD - onto a usb, so im gonna rip an .iso and have her mount it

which is my next question - what do you linux people use to mount image files?

Are you sure it will load to a thumb and boot? 

What is the ISO?

Brasero is a ripper as well.

I am also not a Linux people, I am a human being, and would expect that I am addressed that way.:)

---

### Post by Headcrab on 2011-01-09
An .iso is an image file - ubuntu can mount .iso images out of the box.

Hope that helps.

---

### Post by wojox on 2011-01-09
Double Post

---

### Post by wojox on 2011-01-09
You got to go old school with disk dump:

```
sudo dd if=/dev/cdrom of=~/cdrom_image.iso
```

Replace /dev/cdrom with where ever you cd is.

```
sudo fdisk -l
```

This will make a copy of cd-rom.iso in your Home Directory. You can change cdrom_image.iso to something else as well. Ex. school_program.iso

---

### Post by JuicyCouture on 2011-01-09
> **wilee-nilee said:**
> Are you sure it will load to a thumb and boot? 

What is the ISO?

Brasero is a ripper as well.

I am also not a Linux people, I am a human being, and would expect that I am addressed that way.:)

i just checked out brasero

loos like a good program

but i dont see an option to rip an image file

---

