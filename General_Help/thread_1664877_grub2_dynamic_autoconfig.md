---
title: "grub2 dynamic autoconfig"
date: 2011-01-11
forum: General Help
---

### Post by marbour on 2011-01-11
Hi.

 Sincere salutations and compliments on the more-then-active community I find here. Rarely have I not found my answer before having to post. This is very inspiring. But today I need your help.

I run Ubuntu 10.04 x64... fully updated all the time.

Here is my situation, an irritant actually: for the very rare gaming occasions I use Window$, I have a surprising number of computer restarts... After crashes, updates and such for examples.

Is there a dynamic way to tell grub2 that when I am asking the computer to reboot that the default grub boot option be the last OS I was using?

Scenarios: 

[LIST=1]
[*]I am running Ubuntu and want a restart... That it automatically restarts Ubuntu.
[*]I am running Ubuntu and want to shut down. It automatically reopens the next day in Ubuntu.
[*]I am running Window$ for gaming and have a system crash, M$ or game update that requires rebooting... That it restarts in Window$.
[/LIST]
For the time being, I have set grub's timeout to -1... Meaning that it'll wait for my input. But that is not always convenient when I have to restart and go the the kitchen at once.

Any pointers?

Regards.

Duke.

---

### Post by efflandt on 2011-01-11
**gksu gedit /etc/default/grub**

Comment out the GRUB_DEFAULT line by putting # at beginning of it and add 2 lines:

```
**#**GRUB_DEFAULT=0
[B]GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true[/B]
```Save and close gedit.  Then do: **sudo update-grub**

Done.  For more info about grub2 see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by marbour on 2011-01-12
Wow! That simple!

I admit I had tried to look in that page. I also admit I failed to be patient enough to read through the doc.

Thanks for your time. I'll amend myself for next time.

Best regards to you [efflandt]("http://ubuntuforums.org/member.php?u=937632")

Marc.

---

### Post by marbour on 2011-01-12
double post...

---

### Post by marbour on 2011-01-12
Wow! That simple!

I admit I had tried to look in that page. I also admit I failed to be patient enough to read through the doc.

Thanks for your time. I'll amend myself for next time.

Best regards to you [efflandt]("http://ubuntuforums.org/member.php?u=937632")

Marc.

---

