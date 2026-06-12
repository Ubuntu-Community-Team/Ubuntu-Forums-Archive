---
title: "File owner changed"
date: 2011-07-06
forum: General Help
---

### Post by gvillaran on 2011-07-06
hi, it seems i had some kind of intrusion and i found 6 files changed its ownership to user 1035 and group 1035, i dont know how but i need to change them back to its original owner (root) because one of them is the ls command and the other is the ifconfig how can i revert them to its original state? i cant do it with chown.

Thanks

---

### Post by dino99 on 2011-07-06
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

### Post by gvillaran on 2011-07-06
mmm. im pretty new to this, but how that article will help me? thats for creating users......if u mean that creating the user 1035 and group 1035 i already tried it and didnt work.

thanks for your answer

---

### Post by tredegar on 2011-07-06
Your computer appears to be compromised. You can no longer trust it.
Do  not reboot it, or change any of the logs.
Please do _take it offline now_.

You need to find out how/why this happened (so you can prevent it from happening again).
Details / clues will probably be in the logs, if you know what to look for.

There's a very good security forum over at linuxquestions.org in addition to the security forum here. 

The security exerts will want to know
- Version of the OS you are running
- What services you have been running (apache? ssh? etc) and their versions
- ...   and a lot of other stuff.

You cannot solve your problem by chowning those files.
Good luck.

---

