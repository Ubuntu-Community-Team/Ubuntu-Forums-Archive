---
title: "Location of devices?"
date: 2011-12-30
forum: General Help
---

### Post by soreyes on 2011-12-30
Hi all,

This is probably a stupid question, but I'm trying to use Terminal to do something with a file on a CD I inserted. But I can't seem to write the correct path to the file... my question is, where is the CD "located?"

like, c//....//....?

---

### Post by azmyth on 2011-12-30
cd /media
ls
probably you will need to go to here
cd cdrom

---

### Post by soreyes on 2011-12-30
OK, the name of the device is WXPHEOEM_EN, and this is what I'm trying to do:

$ wine cd/media/WXPHEOEM_EN/SETUP.EXE
 
and then it tells me

wine: cannot find 'cd/media/WXPHEOEM_EN/SETUP.EXE'

Ugh, what am I doing wrong?

---

### Post by nothingspecial on 2011-12-30
> **soreyes said:**
> 

Ugh, what am I doing wrong?

You don't need cd

```
wine /media/WXPHEOEM_EN/SETUP.EXE
```

---

### Post by soreyes on 2011-12-31
^Yes, thank you, it worked!

---

### Post by Paqman on 2011-12-31
Just to be clear, the confusion here stems from:

> **azmyth said:**
> cd /media


Which means: **c**hange **d**irectory to /media. Note the space between cd and /media.

Then:

> 
ls


Which means: **l**i**s**t.

So these are instructions to show you everything that's located in /media, one of which will be your CD. All removable media like CDs and USB sticks get mounted in /media when they're connected.

---

