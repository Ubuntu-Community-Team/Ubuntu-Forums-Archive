---
title: "login problem with latest ubuntu.  won't let me in"
date: 2009-11-12
forum: General Help
---

### Post by juntjoo on 2009-11-12
i think i just upgraded to 9.10. suddenly i have this thing called xubuntu(?).  i think my roommate did it on accident.  anyway, i can only log in using my old regular ubuntu because when i try with xubuntu, this new blue themed system, although it doesn't say there is a problem after putting in my password, after showing some snowflake looking graphic moving in one spot, it just keeps going back to the login screen.  just out of curiosity i tried putting in a wrong password and it caught that and reprimanded me for it, so i know i wasn't putting in a wrong password.

---

### Post by Brandon Williams on 2009-11-12
[Here](http://ubuntuforums.org/showthread.php?t=1317265) is a related thread.

---

### Post by juntjoo on 2009-11-13
thanks

---

### Post by tryonce1 on 2009-11-22
I uprgraded to version 9.10 (not sure what type x or regular) it did it automatically for me. I was able to log in a couple of time after serveral attempts but now it doesn't let me in at all. 
I know most of you guys know how to use the command line but I don't so your explanations of code don't help the ignorant like me. I wonder if there is a step by step in plain English documentation I could use to go back to the previous version of Ubuntu. I hope so.

Cesar

---

### Post by David_Huffman on 2010-10-03
Hi All;
 
I'm relatively new to linux, used Ubuntu for a while, but finally wasn't able to get the screen resolution I needed after efforts configuring for Unichrome Pro.  Booted an Xubuntu live cd and liked that, it detected no specific graphic card but the resolution was right so I did an install.  At first, no problems logging in as I set up user and password, permissions.  Then I downloaded/installed the recommended updates (which included one for grub).  After that, I kept getting prompted for login user/password over and over.  
 
I know a bit about legacy grub, I've set up multiple partitions and OS's, but grub2 is brand new to me.  It didn't detect my FreeDos and Puppy5 (furgal, that's probably why, stuff is in a directory a level down) installs, so I'm going to have to edit this custom file thing.  Default grub2 install goes right to Xubuntu login without a grub screen if there are no other OS's set . . . unless you hold down the shift key during boot.
 
Well, long story short, when I hold down the shift, then select Xubuntu from the grub menu, I don't get the problem of the repeated login failures.  So, I wonder, since the grub2 loader is beta, if that isn't where the problem is, or the update overwrote something in the grub config file.

---

