---
title: "Walkman doesn't automount in nautilus ubuntu 10.04"
date: 2010-05-09
forum: General Help
---

### Post by JavaNut13 on 2010-05-09
It worked fine in every other version of Ubuntu, but now when I plug it in, it will appear in the 'devices' section in Rhythmbox, but not anywhere in nautilus. I am using Ubuntu 10.04, with my Sony Walkman (looks like a USB drive with a screen and buttons)

Is this some Apple-like music security feature? is there any way around it??

Cheers,
Will

---

### Post by JavaNut13 on 2010-05-13
I have found that if I open Rhythmbox, and plug it in, it does not appear in Nautilus. But if Rhythmbox isn't open, it mounts in Nautilus fine (just like it used to in 9.10)

Still I want it in nautilus all the time!!!

Cheears,
Will

---

### Post by JavaNut13 on 2010-05-25
I have looked at the properties (via Rhythmbox) of my Walkman. It says that it is using xrbmtp (my guess is X Rhythm Box Media Transfer Protocol) to access files, not mounting it like a normal computer.

???

Will

---

### Post by 3rdalbum on 2010-05-25
Turn off the MTP plugin of Rhythmbox and see if that works?

Walkmans can't be mounted as MTP on Linux, it never works. If you turn off the Rhythmbox plugin then Nautilus should mount it as ordinary USB mass storage.

---

### Post by JavaNut13 on 2010-05-25
Yup, thats fixed it.

Cheers!

---

