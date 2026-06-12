---
title: "Installing custom bootloader issues"
date: 2009-07-21
forum: General Help
---

### Post by Auraomega on 2009-07-21
Hi there,

I'm trying to install a custom bootloader to my flash drive in order to run my own OS (one I'm working on), however I'm having troubles writing said bootloader to the drive, I've been using```
sudo dd if=boot.bin bs=512 count=1 of=/dev/sdb1
``` but to no avail, it says it copies the file but infact doesn't. I know for a fact boot.bin works as it should as I've booted with it before, as well as it working in Bochs.

What is extremely frustrating is I had this exact problem not so long ago on another flash drive, which I eventually got working (somehow, I forgot what I did) and then managed to lose it.

Any help would be great :D

-Aura

---

### Post by andrewc6l on 2009-07-21
You might want to try going to /dev/sdb instead of /dev/sdb1 - I'm guessing sdb1 is writing to the first partition, instead of to the device.

(Usual caveats: don't accidentally do this to something that has data you care about, etc...)

---

### Post by synapsys on 2009-07-21
or try changing if= to a specific directory. Other wise it will copy your boot.bin to the current working directory

---

### Post by Auraomega on 2009-07-22
@andrewc6l: I'll give it a try when I get a chance and report back.

@synapsys: if = input file, of = output file. I'm copying from the cwd to /dev/sdb

-Aura

---

