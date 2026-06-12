---
title: "Cannot burn at anything other than maximum?"
date: 2009-07-01
forum: General Help
---

### Post by Iendicis on 2009-07-01
The gist of it: My DVD drive refuses to burn at anything other than 24x. While this is okay for Audio CD's and such, Ubuntu discs almost always fail to finish burning at this speed.

I'm running Windows Vista (ew) and Ubuntu 9.04, both 32-bit. I'm trying to get the 64-bit version onto a CD, but using every known program I still get the same result. The "change your drive speed" section is grayed out, or if I do change it I get an error message of some sort. I've tried backed-up ISO files of Linux distros I know I have burned and installed, and even those fail.

I've tried ISO Recorder, Infra Recorder, CDBurnerXP, and Nero 7 Essentials in Vista. I've tried Brasero and Gnomebaker in Ubuntu.

Any ideas?

---

### Post by boof1988 on 2009-07-01
> **Iendicis said:**
> The gist of it: My DVD drive refuses to burn at anything other than 24x. While this is okay for Audio CD's and such, Ubuntu discs almost always fail to finish burning at this speed.

I'm running Windows Vista (ew) and Ubuntu 9.04, both 32-bit. I'm trying to get the 64-bit version onto a CD, but using every known program I still get the same result. The "change your drive speed" section is grayed out, or if I do change it I get an error message of some sort. I've tried backed-up ISO files of Linux distros I know I have burned and installed, and even those fail.

I've tried ISO Recorder, Infra Recorder, CDBurnerXP, and Nero 7 Essentials in Vista. I've tried Brasero and Gnomebaker in Ubuntu.

Any ideas?

If you don't mind using CLI, you can use [*cdrecord*](http://linuxcommand.org/man_pages/cdrecord1.html) (I think it's installed by default in Ubuntu) to burn the DVD.

In a Terminal...
[LIST=1]
[*]Navigate to directory containing the .iso file.
```
cd <directory containing .iso file>
```
[*]Execute the command to burn the DVD.  Specifying your prefered speed by using the "*speed=#*" option.  Where "#" is an integer speed-multiple you wish to use.  And the "-v" option makes the command give verbose output (feedback).  I think that the "dev=/dev/cdrom" part will still work to burn a DVD (if I recall correctly).
```
cdrecord -v speed=# dev=/dev/cdrom <filename>.iso
```
[*]Observe verbose output of what is being done.
[/LIST]

---

### Post by Iendicis on 2009-07-01
> **boof1988 said:**
> If you don't mind using CLI, you can use [*cdrecord*](http://linuxcommand.org/man_pages/cdrecord1.html) (I think it's installed by default in Ubuntu) to burn the DVD.

In a Terminal...
[LIST=1]
[*]Navigate to directory containing the .iso file.
```
cd <directory containing .iso file>
```
[*]Execute the command to burn the DVD.  Specifying your prefered speed by using the "*speed=#*" option.  Where "#" is an integer speed-multiple you wish to use.  And the "-v" option makes the command give verbose output (feedback).  I think that the "dev=/dev/cdrom" part will still work to burn a DVD (if I recall correctly).
```
cdrecord -v speed=# dev=/dev/cdrom <filename>.iso
```
[*]Observe verbose output of what is being done.
[/LIST]

Thanks for your reply; I will give that a try.

---

