---
title: "kernel module now missing, was here a minute ago?"
date: 2010-02-27
forum: General Help
---

### Post by the_genrl on 2010-02-27
hi friends,  i believe problem is a kernel module problem, but im not very good in linux so maybe someone can guide me.  even some tips on how modules work and why they needed to be loaded for every kernel you have installed ???

running ubuntu 9.04, installed virtualbox 2.1.4_OSE with no problems through synaptic package manager.  

virtualbox was running fine with a xp vm (there is a program that only works on XP...sorry), then had a problem installing another VM for my server stuff (ftp, http, dc++, nzb client, etc).  so i restarted the computer.  

after the reboot, NOTHING for virtual box works other than the program itself.  the program starts but when i try to start an operating system, it says "vboxdrv not installed".  sure enough, the director it is looking for the module isnt there. :confused:  it was just working!  

i tried the virtual box forums, im not getting any responses.  ive been hours at this...

any information you can provide would be a great help!

---

### Post by the_genrl on 2010-03-14
hi again everyone and thanks for the onslaught of helpful replys... :disappointed:

anyway as an attempt to help to people in the future, turns out i accidentally booted into a different kernel, one that didnt have the needed modules.  so make sure you boot into the same kernel that you installed the vbox modules on!

---

