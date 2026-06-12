---
title: "Programs --&gt; Accessories not showing up"
date: 2010-08-28
forum: General Help
---

### Post by topito2 on 2010-08-28
Hello, 
 
I had a version of wine prior of 1.2 (I think it was 1.0.1) installed in  my Ubuntu 9.04 operating system and decided to upgrade to version 1.2 
 
I checked some forums on the net and one of them recommended to remove wine using the following command in terminal 
 
sudo apt-get remove wine 
 
then I should remove the .wine folder in my home directory 
 
rm -rf .wine 
 
and finallly the said I had to remove the wine entry in the Applications  menu, so I did by going to System--->Preferences--->Main Menu 
 
After following these instructions, I installed version 1.2 without any  problems but now I see that under Applications--->Wine I lost the  entry for the Programs --> Accessories ---> Notepad feature  (please take a look of the screenshot)

[IMG]http://img291.imageshack.us/img291/1417/myscreenshot1z.png[/IMG]

Did I do something wrong?

I asked this same question in the Wine Forum, and they said I had to ask Ubuntu team about this issue since Wine by itself does not install any menu entries for its own build-in programs

I'll really appretiate your help

---

### Post by plucky on 2010-08-29
Right click on **Applications** and select **Edit Menus**

In the window that opens go to the + button in front of Wine and select.Select **Programs** and tick the box for Accessories.


(See screenshot)

Good Luck

---

### Post by topito2 on 2010-08-31
> **plucky said:**
> Right click on **Applications** and select **Edit Menus**

In the window that opens go to the + button in front of Wine and select.Select **Programs** and tick the box for Accessories.


(See screenshot)

Good Luck
It didn't work, my friend. I check the box besides Accessories and click Close, and the Programs folder does not appear. I tried checking the box besides the Programs folder when selecting Wine but it deselec automatically, as if I could not select the Programs folder to show up.

---

