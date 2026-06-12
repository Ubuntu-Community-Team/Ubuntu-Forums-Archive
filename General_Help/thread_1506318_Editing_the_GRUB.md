---
title: "Editing the GRUB"
date: 2010-06-10
forum: General Help
---

### Post by Axolotl9250 on 2010-06-10
Hey all, can anyone tell me which file I'm supposed to change to add an OS entry to the GRUB that comes with Ubuntu? I've gone through the setup of Arch Linux to get it running besides ubuntu so I have another distro to play with, on the net people talk about menu.lst and a few other files, and I look around for files to do with GRUB and so far all I've found are odd looking Python files and a  file called grub.cfg in the directory menu.lst was said to be in. I'm eager to see if my Arch Linux install worked. Does anybody out there know which direction I should be clicking in or what I should be changing and where I can find it?

Cheers. :)

---

### Post by Mark Phelps on 2010-06-10
Using GRUB2, you're not supposed to manually add entries, and under NO circumstances, are you to edit grub.cfg.

What you do, instead, is open a terminal and enter "sudo update-grub".  That will scan your drives and automatically add entries for every Linux kernel and other OS that it finds.

IF that still does not work, then post back here.

---

### Post by towheedm on 2010-06-10
Mr. Phelps is right, sounds like to have Grub 2 installed, in which case there is no menu.lst.  There is a thread on Grub 2, but can't remember it right now, search the forums for it.

(This message will self-destruct after it's read by everyone.:p)

---

### Post by Axolotl9250 on 2010-06-10
Thanks Mark, that really seems to have worked and an entry for Arch has now appeared in the GRUB menu. :)
Cheers.

---

