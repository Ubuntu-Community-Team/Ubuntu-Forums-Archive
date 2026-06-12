---
title: "Weird startup issue"
date: 2009-10-01
forum: General Help
---

### Post by j3rownjjvjjagik on 2009-10-01
Hello,

I recently installed 9.04...I love it so far but I've had one incredibly large issue the past two times I've tried to install it.  After logging in and updating/restarting my computer, I get this weird screen after the ubuntu loading screen, it looks like this:

[IMG]http://img36.imageshack.us/img36/4950/1001091324.jpg[/IMG]

It ends up just sitting on this screen, and obviously won't let me log in or do anything, really.

My computer is kind of old, ASUS motherboard, pentium III 3.2, ATI Radeon 5500, 1 gb ram.

Anyone have a clue what's going on?

---

### Post by sancho panza on 2009-10-01
It is quite likely that one of the recent graphics driver updates broke your display. I understand that ATI, Nvidia and Intel graphics can cause problems to a lot of users. Wait for 9.10 or downgrade drivers to the way they were before the update.

---

### Post by Giblet5 on 2009-10-01
The nvidia driver in the Ubuntu repository works fine on 9.04 and 9.10.

This looks like a botched GDM theme...

Try (blindly) typing your username, Enter, your password, Enter, and see if it logs you in.

If so, click System/Administration/Login and get rid of that GDM theme.


It kinda looks like a usplash, too...

Try flipping to the console (Ctrl-Alt-F1) and log in.

Then ```
sudo /etc/init.d/gdm restart
``` and that might get you to a usable state.

---

### Post by j3rownjjvjjagik on 2009-10-01
> **Giblet5 said:**
> The nvidia driver in the Ubuntu repository works fine on 9.04 and 9.10.

This looks like a botched GDM theme...

Try (blindly) typing your username, Enter, your password, Enter, and see if it logs you in.

If so, click System/Administration/Login and get rid of that GDM theme.


It kinda looks like a usplash, too...

Try flipping to the console (Ctrl-Alt-F1) and log in.

Then ```
sudo /etc/init.d/gdm restart
``` and that might get you to a usable state.

Tried both those options...no luck.

---

### Post by zenxi on 2009-10-01
> **j3rownjjvjjagik said:**
> Tried both those options...no luck.

do you have an ssh server installed on it? if so try sshing into that box

---

### Post by Giblet5 on 2009-10-01
> **j3rownjjvjjagik said:**
> Tried both those options...no luck.

Rats.

Try running memtest86 from the Grub boot menu. Let it run for two hours. If any failures occur, you have hardware issues and this is a fine time to get that shiny new Core i7 box.

If memtest86 won't even start, try booting from the Ubuntu Live CD and run memtest from there.

If it passes, you may just have a mangled / filesystem and you should be able to fix it from the Live CD.

Boot the live CD (in "try it" mode), open a terminal window, and ```
sudo bash
fdisk -l
``` and identify the device where your / ext3 filesystem is located.
```
fsck /dev/???
``` where ??? is the device you identified above.

If there are errors (and I guess there are), you can rerun fsck with the -y option to blindly rip through your data like rabid weasels through a boxful of baby bunnies. It'll probably do the right thing, but no guarantees.

You DO have a known-good backup, right? RIGHT?

Me neither. Backups are for wimps and Nancie[CARRIER LOST]

---

### Post by j3rownjjvjjagik on 2009-10-06
> **Giblet5 said:**
> Rats.

Try running memtest86 from the Grub boot menu. Let it run for two hours. If any failures occur, you have hardware issues and this is a fine time to get that shiny new Core i7 box.

If memtest86 won't even start, try booting from the Ubuntu Live CD and run memtest from there.

If it passes, you may just have a mangled / filesystem and you should be able to fix it from the Live CD.

Boot the live CD (in "try it" mode), open a terminal window, and ```
sudo bash
fdisk -l
``` and identify the device where your / ext3 filesystem is located.
```
fsck /dev/???
``` where ??? is the device you identified above.

If there are errors (and I guess there are), you can rerun fsck with the -y option to blindly rip through your data like rabid weasels through a boxful of baby bunnies. It'll probably do the right thing, but no guarantees.

You DO have a known-good backup, right? RIGHT?

Me neither. Backups are for wimps and Nancie[CARRIER LOST]

Haha thanks man...yeah, no backup...didn't think I would need one two hours after my install...I'm doing what you said right now, I'll get back to you after I'm done.

---

