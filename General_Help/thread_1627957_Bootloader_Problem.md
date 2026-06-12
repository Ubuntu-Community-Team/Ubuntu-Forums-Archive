---
title: "Bootloader Problem"
date: 2010-11-22
forum: General Help
---

### Post by Graht on 2010-11-22
After dual booting windows 7 and Ubuntu on 2 different partitions on my PC for 1 month till i get the hang of Ubuntu i decided since i am not a gamer to completely uninstall windows and stick with Ubuntu which make my PC shine.

Ok here's the problem tho : i have 2 different hard drives C + D , windows  on C and Ubuntu on D. Since i decided to remove windows i incerted the ubuntu disc and installed Ubuntu on C forgeting the fact that i had them already or to be exact not thinking it much.

at first my PC had 2 Ubuntu : one on C and the other on D, so everytime i started the PC the Grub bootloader screen poped up to make me choose from the 2 diff linux installations.
I figured that by formatting D which was my first and not needed Ubuntu installation i would got rid of the grub bootloader screen, i guessed wrong tho.

I search for Grub commands in forums and in grub main site but since i know very little about the fancy console commands i cant figure what to do.. 
My main goal is to get rid of the Bootloader screen so my PC stars in Ubuntu right away. ( on C )

Anyone here can assist me ? its not a major issue since my PC runs awesome, but i wana know how to do it both to learn and get rid  of the bootloader screen.

Thanks in advance.

---

### Post by wilee-nilee on 2010-11-22
From just a quick read are these or any wubi installs?

---

### Post by Graht on 2010-11-22
and by wubi you mean ?

---

### Post by wilee-nilee on 2010-11-22
> **Graht said:**
> and by wubi you mean ?

Wubi is installing Ubuntu in a live windows environment, rather then booting a live cd to partition and install side by side. The way you have worded it C&D parts of windows makes it sound like you installed from a live Windows. Just making sure we don't want to bork your setup.;)

---

### Post by Graht on 2010-11-22
oh got it!!! no i incerted a CD booted from it and installed! not windows enviroment.. 

thx for your assistance :)

---

### Post by wilee-nilee on 2010-11-22
> **Graht said:**
> oh got it!!! no i incerted a CD booted from it and installed! not windows enviroment.. 

thx for your assistance :)

Actually if I had read your first post I guess you said you had Ubuntu's side by side. 

So your final goal is bypassing the grub screen but this is really only possible with one Ubuntu installed. If you have two you can change the timeout to be shorter, but never set it to 0 as that grub screen will save your booty if something goes wrong. Do you want just one install of Ubuntu? 

Also your in Linux land now letters for partitions are not used and really confusing to us.;) I use XP and W7 but the letters for partitions are windows, in Linux land it is a different nomenclature.

Hey and welcome to the open source life it is rather nice here.;)

---

### Post by Graht on 2010-11-22
thx :) feels better in linux land :) sorry for the windows language , i think i must get used to the linux one  :) i formatted the partition with the second ubuntu installment and the bootloader screen still pops up! i want to get rod of it!

---

### Post by wilee-nilee on 2010-11-22
> **Graht said:**
> thx :) feels better in linux land :) sorry for the windows language , i think i must get used to the linux one  :) i formatted the partition with the second ubuntu installment and the bootloader screen still pops up! i want to get rod of it!

Your doing fine could you post the output of this command run in the terminal.
```
sudo fdisk -l
```

I'm going to go smoke a cig so i will be right back.

---

### Post by tajiknomi on 2010-11-22
[SIZE=2]I think u hadn't tried 
"**sudo update-grub**" after formating...

[/SIZE]

---

### Post by Graht on 2010-11-22
actually i am at work on a crappy Wxp laptop! i will not go home for about 2 hours at least.. will catch you l8r then ?

---

### Post by wilee-nilee on 2010-11-22
> **tajiknomi said:**
> [SIZE=2]I think u hadn't tried 
"**sudo update-grub**" after formating...

[/SIZE]

That is a distinct possibility good eye.;)

---

