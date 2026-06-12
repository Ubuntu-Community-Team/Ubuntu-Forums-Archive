---
title: "ubuntu 8.04 slow start"
date: 2009-09-22
forum: General Help
---

### Post by tsueseres on 2009-09-22
hello, ive been using ubuntu 8.04 hardy for a while, but i have notice that the startup of the system takes longer to load that before. how can i make the startup faster with out formatting

---

### Post by tgeer43 on 2009-09-22
Well it's not like Windows where things tend to get slower over time for no apparent reason or due to severe disk fragmentation. With Ubuntu it's usually due to adding applications and/or services that run at startup.

Try looking in System->Preferences->Startup Applications and System->Administration->Services (I thinks they're called something else in Hardy) to make sure that you haven't got anything starting up that you don't need.

You can also profile your boot up to increase it's speed. To do this:

[LIST=1]
[*]On boot up press 'e' at the GRUB menu to edit.
[*]Arrow down to the first line of the kernel you are booting and press 'e' again.
[*]Move to the end of the line and add a space and the word 'profile'.
[*]Press ENTER to accept the line and 'b' to boot.
[/LIST]
This boot will take longer than usual as it profiles the files needed to boot your system. Subsequent boots should be faster. Do this AFTER disabling any unneeded services and startup apps because the files needed to boot will change.

If things are still too slow you can install 'bootchart' from the repositories. It will create a nice chart of everything that's happening during bootup to help you identify where the major delays are.

tgeer

---

### Post by tsueseres on 2009-09-23
is there any risk in doing profile, do i loose something?

---

### Post by tgeer43 on 2009-09-23
It's perfectly harmless - you risk nothing.

tgeer

---

### Post by tsueseres on 2009-09-23
> **tgeer43 said:**
> It's perfectly harmless - you risk nothing.

tgeer

well it got a littlebit faster, 
i installed bootchart but how do i activated to start with ubuntu to get the information

---

### Post by tgeer43 on 2009-09-23
Once you install bootchart it automatically runs each time you boot.
You just need to go into /var/log/bootchart/ to see the results.

tgeer

---

### Post by tsueseres on 2009-09-23
> **tgeer43 said:**
> Once you install bootchart it automatically runs each time you boot.
You just need to go into /var/log/bootchart/ to see the results.

tgeer

i dont know whats wrong but it doesnt show me the file

---

### Post by tgeer43 on 2009-09-26
> **tsueseres said:**
> i dont know whats wrong but it doesnt show me the file
Do you even have a /var/log/bootchart folder? If so, what (if anything) is in it?
If you don't have this folder then go back into synaptic and verify that bootchart is indeed installed as I can't think of any reason that it would not be generating the charts if the package is installed.

tgeer

---

