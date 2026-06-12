---
title: "how to delete 1 of 2 operating systems on one hard disk ,,please help me"
date: 2010-08-31
forum: General Help
---

### Post by shenron on 2010-08-31
hi everyone ,,,i am new to this form i have installed ubuntu today and i am enjoying it so far but there is still some problems am having i will explain from the start ,,,i have a hp laptop it has 1 hard disk c,d the d am not planing to mess with it because it has the hp recovery and it might be helpful one day ,,,,so i downloaded ubuntu to an external hard disk then when i was installing it i selected it to be installed on C i thought it would automatically delete vista but it didn't when the restarted the computer i saw 2 options vista and ubuntu so i was wondering if anyone can tell me how do i delete the vista and keep only 1 operation system and btw i have no CD or DVD or floppy available so i cant download it on a cd then format c and install ubuntu again so i need away to delete vista from c while keeping ubuntu in c i hope that makes sense :s ,,,thank you for reading this am sorry its abit too long but i dont have another way to explain it thank you for your time :)

---

### Post by pricetech on 2010-08-31
Since you just installed, the easiest, and quickest, thing to do is just reinstall. Read the screens carefully, especially the ones about where you want to install Ubuntu, and make sure you choose to removed everything on the partition and install Ubuntu exclusively.

Do you have media for vista ?? If so, just wipe the whole thing.

---

### Post by Nytram on 2010-08-31
Hi Shenron

The easiest way to do what you want would be to format Windows on the C partition, and then update grub so that Windows is removed from your boot menu.

To format Windows you need to install a program called **gparted** it's in the software centre. After it's installed run it by typing **Alt-F2** and enter **gksu gparted.**

You can then format your Windows partition. Afterwards open a terminal and type into it:

**update-grub**

This should remove the Windows entry from the boot menu.

BTW it's usually wise to backup important data before working with partitions.

---

### Post by shenron on 2010-09-08
hi pricetech ,,,well at the time i didnt have dc or dvd and the only way to chose the settings to format the hard drive and install ubuntu is when ur installing it using the cd or dvd ,,,anyway i did get me a cd and after trying 3 Linux os's i ended up using the ubuntu lol ,,,thanks for your reply

---

### Post by shenron on 2010-09-08
hi Nytram ,,thanks for your reply ,,,i actually got me a dvd and went with the Pricetech advice ,,,,tc

---

### Post by shanep-server on 2010-09-08
if u don't have cd dvd or floppy drive... if your computer is new enough it might support booting from usb... u could download ubuntu iso an create a usb live stick with which u could re install from.

---

