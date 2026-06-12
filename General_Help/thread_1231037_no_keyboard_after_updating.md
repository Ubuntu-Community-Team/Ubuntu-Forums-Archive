---
title: "no keyboard after updating"
date: 2009-08-04
forum: General Help
---

### Post by andy08 on 2009-08-04
Hi,
I have Kubuntu 9.04. Yesterday I installed some updates including 4 blocked updates. Since then, my keyboard doesn't work at all. I can't write anything. In Windows it works normal. Of course I tried it with another new keyboard, but the same problem.

How to solve that Problem? Thanks in advance.

---

### Post by Zorael on 2009-08-04
Hmm. Boot up in recovery mode and pick netroot.

(If you don't have your machine connected to the internet with a wired cable and with DHCP (IP addresses automatically assigned), you'd need to enter a few more commands here.)

Enter the following. (Omit the hashmark **#**)
```
# aptitude update
# aptitude safe-upgrade
```
Make *certain* note of what packages it says are being held back (if any). Write them down, so you can report here in case this didn't do the trick. Onwards;
```
# aptitude install xserver-xorg-input-kbd
# dpkg-reconfigure hal
# exit
```
Then pick resume.

---

