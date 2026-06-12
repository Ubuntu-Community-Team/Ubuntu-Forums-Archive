---
title: "Problem to create a live-cd with remastersys"
date: 2009-08-13
forum: General Help
---

### Post by cazz on 2009-08-13
Hi
I trying to create a ubuntu/debian live-cd.
I going to have partimage to help me to automatic recover some partition from a image file.

I have try both latest debian (netinstall version) and ubuntu server 9.04.
I dont want to have any GUI that why I have try this two.


After I have install the ubuntu/debian I install partimage and the remastersys.

I run
```
sudo remastersys dist
```
and it create a ISO file

I send it to a server that I can burn the ISO file.
But when I trying to boot the cd nothing happend.

I did try to add the ISO to the viritualbox and it say "no bootable medium found"

so I have create a ISO that is not bootable?

---

### Post by blueridgedog on 2009-08-13
Do you receive any errors when building the ISO image (errors in the output of remastersys)?

---

### Post by cazz on 2009-08-14
No I get no error.
Have look att the screen and read the log.

Is very very strange

---

### Post by lisati on 2009-08-14
> **cazz said:**
> No I get no error.
Have look att the screen and read the log.

Is very very strange

Couldn't see the log because it wasn't on my screen, sorry.

Did you remember to [burn the file as a disk image]("https://help.ubuntu.com/community/BurningIsoHowto")?

---

### Post by cazz on 2009-08-14
yes I have burn the ISO with nero on a diffrent computer.
I have even try with mount it with viritualbox

---

### Post by cazz on 2009-08-14
I did trying for fun to open the ISO that I have create in remastersys (ubuntu) and debian-live (debian) with magicISO.

But the Magic ISO say about the both file "Found a invalid directory in the ISO file!"

---

### Post by blueridgedog on 2009-08-15
Can you mount the ISO image on the linux system and see what the contents are?

```
sudo mkdir /mnt/remaster
sudo mount -o loop /path/to/and/nameofisofile.iso /mnt/remaster
cd /mnt/remaster
ls -al
```

Change /path/to/and/nameofisofile.iso as needed to point to your ISO file.

---

### Post by cazz on 2009-08-18
I have delete all ISO file I have create.
I trying now with Reconstructor to see if it work with that.

---

