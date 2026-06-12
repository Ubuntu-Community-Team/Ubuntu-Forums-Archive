---
title: "Some beginner questions."
date: 2011-01-15
forum: General Help
---

### Post by Crux_Dissimilata on 2011-01-15
I just installed Ubuntu in a virtual box on my Windows machine to see if I can figure out how Linux works and act before replacing Widows for good. Now I came across some questions.

1. How do I change my menu "Applications" to fit my needs. So I can put the software I want in the folder I want?

2. I downloaded a program that I would like to install. I extracted it and it is now located at my desktop. The installation file is called install.sh but when I double click it it opens it in a text editor and I can view the source code. How to I run the installation file so the software actually get's installed?

3. Is there any online documentation for people that went from Windows to using Linux to learn the basics of how Linux works?

4. I am connected directly to the internet now but I also have a wireless card in my laptop. How do I see if my card is supported under Linux?

---

### Post by Smart Viking on 2011-01-15
2. Right click on the file and under the options select that you want it to have permissions to execute as a program, after that when you double click it say that you want to run it in a terminal.
3. Yes.
4. The fastest way is to boot up in a live session to see if things work.

---

### Post by TeoBigusGeekus on 2011-01-15
1. Right click the menus>Edit menus. You can add/delete/rearrange anything in there.

2. Open terminal and navigate to the folder where the install script is.
```
cd /path/to/script/
```
Then
```
chmod +x install.sh
```
to make the script executable and while you're in the same folder
```
./install.sh
```
to execute it.

3. Download the pdf from [here]("http://ubuntu-manual.org/"). 10.04 and 10.10 are more or less the same. It's a brilliant book for beginners; even my grandmother could understand it. I believe you are more tech savvy than her.

4. You can go to Administration>System>Additional Drivers and see if there is an additional driver for your wireless card; install it if there is. In any case, plug off your ethernet cable and enable wireless on your laptop; see if anything happens.

---

### Post by Crux_Dissimilata on 2011-01-15
If I would do a dual boot for Windows7 and Ubuntu. Is it possible to later removed Windows7 without it effecting the software installed and everything else I did to modify Ubuntu after my wishes?

---

### Post by ender4 on 2011-01-15
probably.

Removing the Windows 7, wouldn't change your ubuntu installation at all, however the main reason you would want to remove Windows 7 would be to resize the Ubuntu partition to fill the space currently used by Windows 7.  If the resize works successfully, then your installation should work the same as it always has.  However, whenever you change partitions, there is a chance of data loss, so make sure you back everything up first.  

I have actually done this myself, and didn't have any problems, so yes, it most certainly can be done.

---

### Post by llamabr on 2011-01-15
> **ender4 said:**
> 

Removing the Windows 7, wouldn't change your ubuntu installation at all, however the main reason you would want to remove Windows 7 would be to resize the Ubuntu partition to fill the space currently used by Windows 7.  If the resize works successfully, then your installation should work the same as it always has.  However, whenever you change partitions, there is a chance of data loss, so make sure you back everything up first.  

NB, you do not need to resize your partition to make use of another one.  You can just as effectively reformat the win partition and simply write to it, or re-use it to mount /home, etc.  A large separate partition might be useful for some as a file server, to to save photos.

---

### Post by mastablasta on 2011-01-15
> **Crux_Dissimilata said:**
> If I would do a dual boot for Windows7 and Ubuntu. Is it possible to later removed Windows7 without it effecting the software installed and everything else I did to modify Ubuntu after my wishes?


yes, also note that Ubuntu won't grow so much as windows tend to.

most disk you need will be for your data and maybe some programmes... programmes also dont' take so much space. but if they are windows programmes running under WINE then they take up sapce just like under windows.

---

### Post by mastablasta on 2011-01-15
> **Crux_Dissimilata said:**
> If I would do a dual boot for Windows7 and Ubuntu. Is it possible to later removed Windows7 without it effecting the software installed and everything else I did to modify Ubuntu after my wishes?


yes, also note that Ubuntu won't grow so much as windows tend to.

most disk you need will be for your data and maybe some programmes... programmes also dont' take so much space. but if they are windows programmes running under WINE then they take up sapce just like under windows.

---

