---
title: "Can't Resurrect Sudo"
date: 2006-05-24
forum: General Help
---

### Post by palsyboy on 2006-05-24
I was adding some users via KUser, and somehow, my original user can no longer execute sudo.  I probably unchecked something accidentally. ](*,) 

Anyway, I'm trying to boot back into my system, but it's not working.  I've tried advice from several threads advising a Rescue Mode boot, so I've thrown the "rescue" boot option, and it's gotten me in, asked which partition to mount as /, etc.

However, whenever I get to a root prompt and try
```
nano -w /etc/group
```
I get the followng error: 
```
Error opening terminal: bterm
```
Doing a search at google.com/linux only gets me stuff about rewriting grub.conf, which doesn't seem to be relevant.

Does anyone have any ideas on how to rescue this system?  Thanks.

---

### Post by codejunkie on 2006-05-24
[QUOTE=palsyboy]I was adding some users via KUser, and somehow, my original user can no longer execute sudo.  I probably unchecked something accidentally. ](*,) 

Anyway, I'm trying to boot back into my system, but it's not working.  I've tried advice from several threads advising a Rescue Mode boot, so I've thrown the "rescue" boot option, and it's gotten me in, asked which partition to mount as /, etc.

However, whenever I get to a root prompt and try
```
nano -w /etc/group
```
I get the followng error: 
```
Error opening terminal: bterm
```
Doing a search at google.com/linux only gets me stuff about rewriting grub.conf, which doesn't seem to be relevant.

Does anyone have any ideas on how to rescue this system?  Thanks.[/QUOTE]
try this boot in rescue mode when you hit the terminal run this command ```
passwd root
```then enter a new password for the root account, reboot and when you need to have admin rights to run a command, run it like this open konsole enter ```
su
```enter the new password you just set when prompted, this will give you root permision in that terminal, then enter the command for example ```
kuser
``` this should give you root access so you can fix the problems with your user accounts.
if you have any problems with this, let me know and i'll try to help
codejunkie,

---

### Post by palsyboy on 2006-05-24
Thanks! :) 

It wouldn't open up any GUI apps as root from within my user's profile, but I edited /etc/group and ensured that my user was in the sudo and admin groups.  After that, I could run sudo commands just fine.

---

