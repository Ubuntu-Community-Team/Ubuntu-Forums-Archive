---
title: "menu.lst file non existant ?"
date: 2011-07-25
forum: General Help
---

### Post by Hirobian on 2011-07-25
I am following a guide on how to change the boot order using a terminal on Ubuntu.

Link: ( [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS) )

At the **Back Up Grub Settings** part I do the " /boot/grub/menu.lst_backup " command and input my password and it gives me this: 
name@name-laptop:~$ /boot/grub/menu.lst_backup
bash: /boot/grub/menu.lst_backup: No such file or directory

So I hesitatingly decide to skip this part.
At the **Open in a Text Editor **part I do the " /boot/grub/menu.lst " command in the terminal and it opens an empty file and I get a hunch...I go into /root/grub to check if the file even exists and I cannot even find the menu.Ist file anywhere.

I am guessing there may be a problem or the file is simply named differently for some reason, anyways I need help to figure out whats wrong or where the menu.Ist file is.

---

### Post by 23dornot23d on 2011-07-25
> 
[B]This guide applies only to systems using grub (aka grub legacy, where  menu.lst exists) and not grub-pc ([COLOR=Red]aka grub2, where menu.lst doesn't  exist[/COLOR]).
[/B][B]
Your grub will possibly be [COLOR=Red]grub2[/COLOR] ..... 


You may want [/B][[COLOR=Blue]_*this Link*_[/COLOR]]("https://help.ubuntu.com/community/Grub2")

---

### Post by hyfanious on 2011-07-25
if u have grub2 must use this:
/boot/grub/grub.cfg

---

### Post by Mark Phelps on 2011-07-26
> **hyfanious said:**
> if u have grub2 must use this:
/boot/grub/grub.cfg

NO ... you do NOT use this!  Even the file itself has warnings inside to NOT edit it.  

Don't give folks bad advice.

---

### Post by Hirobian on 2011-07-26
Hmm...seems we have a prankster lurking in the threads  waiting to make a move... just kidding. :P

I am not certain if I have grub2, I never saw anything saying grub-pc or grub2  while on the grub menu or even while on Ubuntu. :confused: 

Anyways, I will give the grub2 link a look, see if that works and I will come back to say if anything worked or went wrong. #-o

---

### Post by drs305 on 2011-07-26
You can run this command to see if you have grub 2:
```
grub-install -v
```
Grub 2 will be a version between 1.96 and 1.99

For making changes to the Grub 2 menu, I highly recommend a GUI app called Grub Customizer. I created a thread about it - click the 'Customizer' link in my signature line.

If you want to learn more about how Grub 2 works, you could look at the 'GRUB2', 'Basics' or 'Tasks' links, also in my signature line.

---

### Post by Mark Phelps on 2011-07-27
To add to what drs305 already said ... some might recommend you install and use startup-manager -- but I've discovered (the hard way) that it does not work with recent (v1.99RC) GRUB versions.

So, Grub customizer is the way to go ...

---

