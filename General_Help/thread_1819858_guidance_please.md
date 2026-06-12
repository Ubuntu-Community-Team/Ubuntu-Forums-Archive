---
title: "guidance please"
date: 2011-08-06
forum: General Help
---

### Post by dartz003 on 2011-08-06
i am a newb with linix... can some1 please point me to a guide for dual boot win 7 and ubuntu, i have win 7 installed. ... i never installed grub or the like ... please give me a guide from square 1. oh i already have an empty partition set aside for ubuntu

---

### Post by daccount10 on 2011-08-06
1. Get a ubuntu cd (download it from ubuntu.com then burn it- instructions there)
2. Boot /reboot computer with cd in (if it doesn't work make sure cd is first in boot order in bios)
3. When you get to the partition stage in the installation:
[INDENT]a)if you made a partition go to manual and format that partition as ext4 mounted as / with some space left and make a small swap partiton
b) else install ubuntu next to windows with the slider
[/INDENT]4. Complete installer it should finish quickly

NOTE: there are many other, better guides online. Just google it.

---

### Post by jerrrys on 2011-08-06
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot&sa=Search&cof=FORID:9#896](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot&sa=Search&cof=FORID:9#896)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+windows+7&sa=Search&cof=FORID:9#1001](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+windows+7&sa=Search&cof=FORID:9#1001)

---

### Post by Basher101 on 2011-08-06
The SAFEST way is to free disk space from within windows 7. You do that when you rightclick on Computer and then on Manage from the drop down menu. wait until a window pops up and go to Disk utility (im not 100% sure if that was the name) then you just rightclick on your C: or D: partition and free up some space. Then when you boot from the Live CD you will get the "install side by side" option when installing, hit that and youre done. Just follow the installer then.

---

### Post by bodhi.zazen on 2011-08-06
> **dartz003 said:**
> i am a newb with linix... can some1 please point me to a guide for dual boot win 7 and ubuntu, i have win 7 installed. ... i never installed grub or the like ... please give me a guide from square 1. oh i already have an empty partition set aside for ubuntu

Here is a step-by-step guide with screenshots:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Be sure to back up your data first, defragment your windows install, and you will need at least two partitions for Ubuntu, 3 if you use a separate /home, and 4 if you wish a separate data partition to share data (separate from either OS).

So decide on your partitioning next and make sure you understand partitioning in Linux.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

From there, follow the defaults, set up your partitions, and you should be ggod to go. Let us know if you have a problem.

---

### Post by dartz003 on 2011-08-06
i installed ubuntu... but... ubuntu11.04 has no battery life icon.. which is terrible since i am using a laptop :( i don't want my laptop to die on me randomly :(.  i am totally new with ubuntu, so please help me wit this issue... and i cannot access windows 7 anymore :(, it goes straight to ubuntu now, no option for win 7 :(

---

### Post by Basher101 on 2011-08-07
It has an option for windows 7. On bootup your OS is selcted in Grub. By default it will boot ubuntu after 10 seconds (you must hit any key except enter to cancel) then go down all the ways and select windows

---

