---
title: "fresh vista wipe out my dual boot Menu Help !!!!!"
date: 2009-08-06
forum: General Help
---

### Post by msayerh on 2009-08-06
i lost my dual boot after i install a fresh vista. I use to dual boot between Vista and Ubuntu 9.04. but now when i turn the computer on it goes straight to vista 
i had tried to recover grub and follow the instruction from here "recovering Grub after installing Windows": [https://help.ubuntu.com/community/Wi...ling%20Windows]("https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows")
 sudo grub 
grub > root (hd0,2) because    i have one hard drive and ubuntu on the E drive
it goes fine but when  i type setup (hd0) it give me this error 
Error 17: Cannot mount selected partition
and i have no idea why ????
any help will be gr8
HELP :confused:

---

### Post by baliganikhil on 2009-08-06
Boot in with Live CD
open terminal.
type in - sudo grub
find /boot/grub/stage1

it will return something... Use it in place of what I have used below
root(hd0,1)

setup (hd0)
quit

restart your computer

---

### Post by thezood on 2009-08-06
> **msayerh said:**
> i lost my dual boot after i install a fresh vista. I use to dual boot between Vista and Ubuntu 9.04. but now when i turn the computer on it goes straight to vista 
i had tried to recover grub and follow the instruction from here "recovering Grub after installing Windows": [https://help.ubuntu.com/community/Wi...ling%20Windows]("https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows")
 sudo grub 
grub > root (hd0,2) because    i have one hard drive and ubuntu on the E drive
it goes fine but when  i type setup (hd0) it give me this error 
Error 17: Cannot mount selected partition
and i have no idea why ????
any help will be gr8
HELP :confused:

You could also try following the "extended" instructions on this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by burmanabhay88 on 2009-08-06
These kind of things happen. I use a software in Windows to restore my grub. It's called super grub loader. Google it out. Really ease to use.

---

### Post by CatsRninja on 2009-08-06
Well, when i reinstaled vista in my laptop, the ******* swiped clean all my partitions.and forced me to have only vista in my laptop, so i had to reeinstall everything again.

Check if the same didnt happen to you.

---

### Post by burmanabhay88 on 2009-08-06
> **CatsRninja said:**
> Well, when i reinstaled vista in my laptop, the ******* swiped clean all my partitions.and forced me to have only vista in my laptop, so i had to reeinstall everything again.

Check if the same didnt happen to you.

that would happen only if you had partitioned the entire hard drive as etx3 (which vista doesn't recognise)

---

### Post by metalf8801 on 2009-08-06
> **CatsRninja said:**
> Well, when i reinstaled vista in my laptop, the ******* swiped clean all my partitions.and forced me to have only vista in my laptop, so i had to reeinstall everything again.

Check if the same didnt happen to you.

yeah I've heard about Vista doing that?  You also won't be able to see your Ubuntu files from vista like you can in XP.  Why I don't know buts its a good idea to worn people like your are

---

### Post by CatsRninja on 2009-08-06
> **burmanabhay88 said:**
> that would happen only if you had partitioned the entire hard drive as etx3 (which vista doesn't recognise)

nop, i had dual boot with vista/ubuntu, just wanted to reinstall vista in partition where vista was.
I was instaling from a dvd created first thing when my laptop arrived brand new.
So i guess the only thing it did was to wipe out all the disk and reinstall itself.
i thought it strange, it didnt even asked me in witch partition to install, and i also ignored the format warnings thinking the ext3 partitions would be safe.
I guess that it was my fault not be causios enouth with it.
and btw, it instaled a lot of google aplications i didnt have before when i received the laptop, i fealt kinda raped, it installed stuff i didnt wanted to.

---

