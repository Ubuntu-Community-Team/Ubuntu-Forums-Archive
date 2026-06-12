---
title: "Cant execute file"
date: 2009-11-21
forum: General Help
---

### Post by nunojpg on 2009-11-21
gipsy-segal#/goa-5.0/bin/local>ls -l setday_p 
-rwxr-xr-x 1 gipsy users 100415 May 21  2009 setday_p
gipsy-segal#/goa-5.0/bin/local>./setday_p 
./setday_p: Command not found.

File exists and is executable, but...

---

### Post by renkinjutsu on 2009-11-21
file it

```
file setday_p
``` is it a binary or a script?

---

### Post by nunojpg on 2009-11-21
Binary.

---

### Post by renkinjutsu on 2009-11-21
did the arch match yours?
are you trying to execute a 32bit binary with a 64bit kernel?

---

### Post by nunojpg on 2009-11-21
yes! is that an issue? well, I see it is. But can I execute on AMD64? I have too much RAM to go back.

---

### Post by renkinjutsu on 2009-11-21
i see.. then i don't know what you can do, since a lot of 64bit users here have no problems running 32bit apps.. but i know that there's a kernel feature to emulate 32bit execution, but that would require to recompile your kernel..

i'm not even 100% sure if that'll work

Just stick around till someone can help, the problem could be as simple as downloading a few 32bit libraries

---

### Post by nunojpg on 2009-11-21
I asked this last without checking google.

Instaling ia32-libs did the trick:

sudo apt-get install ia32-libs


Thanks!

---

### Post by renkinjutsu on 2009-11-21
heey, no problem.. I KNEW it was going to be something simple


goodluck with whatever you're doing

---

### Post by Johnneylee on 2009-11-21
You can also create a chroot environment that is essentially like the windows compatibility for 32-bit applications on 64-bit windows.

A quick link
[DebootstrapChroot]("https://help.ubuntu.com/community/DebootstrapChroot")

Cheers!

---

### Post by renkinjutsu on 2009-11-22
> **Johnneylee said:**
> You can also create a chroot environment that is essentially like the windows compatibility for 32-bit applications on 64-bit windows.

A quick link
[DebootstrapChroot]("https://help.ubuntu.com/community/DebootstrapChroot")

Cheers!

Hey thanks! I might give Adobe Air 2 a spin after i finish installing packages from debootstrap.. this is pretty neat, as i don't like mixing my 32bit libraries with my 64bit ones.

---

