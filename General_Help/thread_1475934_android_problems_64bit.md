---
title: "android problems 64bit"
date: 2010-05-07
forum: General Help
---

### Post by dsbig on 2010-05-07
does the android sdk work on ubuntu 64bit 10.04 becuase I try to run it in terminal, this is what i get
i cd to the tools directory and then 
sudo adb no file or directory

sh adb: adb 1: syntax error:"(" unexpected

whats wrong?

---

### Post by jobix on 2010-05-07
I think you're using the wrong syntax. IIRC, if you execute
> ./adb [......]
it will work. The [....] indicates you need to provide it with the requisite parameters. You can find those on the Android page.

---

### Post by dsbig on 2010-05-07
no matter what I do i cant get it to run. I type ./adb and gives no file or directy, i checked to make it was executable.

edit: as soon as I posted this reply i found a program call getlibs.deb it downloaded 32bit files needed and now adb runs

---

