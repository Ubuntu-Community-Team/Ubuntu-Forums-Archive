---
title: "Initng and Sound Help !"
date: 2006-04-01
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-01
I have not had sound since I installed Ubuntu. I have the drivers. They are a bunch of .inf, dll, ini, and .sys files. I would really like to have sound so how can I set it up ? My sound worked in Dapper so I don't know what the problem is.

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=MasterChief1234]1. I'm following the Initng Tutorial in the Ubuntu Wiki. I got it installed and all that. Now I'm at the part where it says "edit your GRUB list: sudo gedit /boot/grub/menu.lst Make a duplicate Ubuntu entry and rename its title to something like Ubuntu (InitNG). In the kernel line add init=/sbin/initng"

Where is the kernel line ? Can someone who installed it post their menu.lst so I can see where it is. I have had no problem in the past installing it.
--------------------------------------------------------------------------
2. I have not had sound since I installed Ubuntu. I have the drivers. They are a bunch of .inf, dll, ini, and .sys files. I would really like to have sound so how can I set it up ? My sound worked in Dapper so I don't know what the problem is.[/QUOTE]
......................

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=MasterChief1234]......................[/QUOTE]
Please, I've been asking this question for over 5 hours..... :mad:

---

### Post by xXx 0wn3d xXx on 2006-04-01
I solved my Initng problem. Now I just need to solve the sound one.

---

### Post by idlewild on 2006-04-01
Read the man page on ng-update.  Make sure you have alsasound loading up on boot or what ever you're using for sound.

Also try be a bit more patient when asking for help :P

---

