---
title: "CD Burning issue"
date: 2006-06-18
forum: General Help
---

### Post by Timokl on 2006-06-18
After upgrading to Ubuntu Dapper, I cannot burn CD correctly any more. All CDs are ruined after burning. With Breezy, burning was possible (although horribly slow). 

This is what cdrdao tells me:

```
timo@ubuntu:/dev$ cdrdao scanbus
Cdrdao version 1.2.1 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Using libscg version 'ubuntu-0.8ubuntu1'

ATAPI:0,0,0          PHILIPS , CDRW/DVD SCB5265, TX03

```

Any ideas?

Bye,
Timo

---

