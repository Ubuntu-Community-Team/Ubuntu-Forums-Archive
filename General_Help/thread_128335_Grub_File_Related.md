---
title: "Grub File Related"
date: 2006-02-11
forum: General Help
---

### Post by aseem_mal on 2006-02-11
Hi. I have a dual boot Win XP + Ubuntu.
By default, it goes into Ubuntu, unless I select Win XP on start.

My Question is, Can I change the order of the OS, so that when the wife uses the computer, it takes her directly into XP? Also, can I change the nuumber of seconds (countdown) for the automatic selection?:confused: 

Thanks,
A

---

### Post by vruum on 2006-02-11
there are a couple of ways of doing it, but the file you need to edit is /boot/grub/menu.lst, so, open up a terminal and type
```
sudo gedit /boot/grub/menu.lst
``` find the windows entry, looking something like:
> 
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1 
move that section to just above the line that says
###DEBIAN AUTOMATIC KERNEL LIST### or something like that. 
then, to change the timeout. find the line that says "Timeout  5" an change the 5 to how many seconds you want the system to wait before booting the default.

---

### Post by aseem_mal on 2006-02-11
Thanks. Just one concern, before I do it:  Is it safe to do?:confused: 

Thanks.

---

### Post by Zalbor on 2006-02-11
You don't need to move the XP block, though it's perfectly safe. Just find the line that says "default" and a number and change the number to whatever order XP is in the list minus one. For example, if XP is the fourth "title" you change that line to "default 3".

---

### Post by lha on 2006-02-11
If you want to do what vruum suggested, you have to move those Windows-related lines just above
```
### BEGIN AUTOMAGIC KERNELS LIST
```
(There's another line with END DEBIAN instead of BEGIN, so be careful not to move lines to wrong place.)

If you don't make mistakes, it is safe. :) You can make a backup, open terminal and
```
cd /boot/grub/
sudo cp menu.lst menu.lst_backup
``` before you edit it. If something goes wrong, you can boot your computer with a live-cd and restore that backup file.

---

### Post by vruum on 2006-02-11
yes, but then you'd need to change the default number after upgrading or changing your kernel, I find it easier to keep everything not ubuntu/debian before the ##automatic kernel list. but then, I tend to distrohop. 
Anyway, It should be safe, but just to make sure, you can make a backup of the file before editing. 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup.
```

---

### Post by aseem_mal on 2006-02-11
I tried Zalbor's posting, and it worked.

Thanks, all of you.

- A

---

