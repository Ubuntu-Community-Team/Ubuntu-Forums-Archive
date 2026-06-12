---
title: "How to edit your boot order in Grub ubuntu 9.10"
date: 2010-04-18
forum: General Help
---

### Post by w1ll1am on 2010-04-18
Okay it took me forever to figure this out i read stuff about it on many different posts so i thought i would tell how i got it to work. 

I have Windows XP professional and Ubuntu 9.10 installed on the same system and i wanted to have windows as the default boot option. this is how you do it.

  open the terminal and type the following


[LIST]
[*]sudo update-grub
[/LIST]
Now count the number of "found" items there are on my system there are four. Now type the following

[LIST]
[*]sudo gedit /etc/default/grub
[/LIST]
There will be a line that says GRUB_DEFAULT=1. You now change the 1 to the number of the OS that you want to boot first in mine XP is what i wanted to boot first so i type in 4. Save the file and exit. you have to update the grub.cfg file now so run sudo update-grub again. Now restart the system and you should be good to go Windows XP or what ever OS you choose will now boot first.

---

