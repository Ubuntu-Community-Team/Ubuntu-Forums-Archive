---
title: "Help, locked out of Grub.  I am an idiot"
date: 2009-09-15
forum: General Help
---

### Post by artemenko on 2009-09-15
So I've been tinkering with StartUp-Manager to make a nice boot screen for my dual boot Windows XP and Ubuntu setup.  And to a large extent, it worked great ([http://wwww.ubuntuforums.org/showthread.php?p=7914011](http://wwww.ubuntuforums.org/showthread.php?p=7914011))

Only thing was, my entries were not password protected -- even when I selected that option with Startup-Manager. (I do remember my password when I entered it into StartUp-Manager).

When that didn't work, I manually added the term "lock" to each of my startup options in the Grub menu.  Big mistake, I know.

Now, when I try to load them, it says "hit P to enter a password" and when I do it says "Failed!"

Ugh -- is Grub looking for the Md5 version of what I typed into Startup-Manager?  Honestly all I did was add "lock" to each entry in my Grub menu.

Any help would be appreciated!

(clearly I'm writing this from the live CD)  =/

---

### Post by drobster on 2009-09-15
[SIZE="3"]Hopefully the Grub legacy manual will help.

[http://www.gnu.org/software/grub/manual/html_node/index.html#Top](http://www.gnu.org/software/grub/manual/html_node/index.html#Top)

or try the SuperGrub disk which restores grub to the MBR automatically.

lol,  :lolflag:

drobster[/SIZE]

---

### Post by artemenko on 2009-09-15
Anything I can do from a Live CD?

---

### Post by lindsay7 on 2009-09-15
see

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by artemenko on 2009-09-15
[> http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

I think that is for resetting a user password, not a grub password...

I accidentally "locked" my partitions in [FONT=Bitstream Vera Sans Mono]menu.lst[/FONT]

---

### Post by lindsay7 on 2009-09-15
You can type this in the terminal to edit the grub menu.

sudo gedit /boot/grub/menu.lst

I do not know what you need to change

---

### Post by ankspo71 on 2009-09-15
Hi,

First you have to try to remove the words "lock" from /boot/grub/grub.lst ((I think)).

[edit] I changed grub.conf to grub.lst. 

 

Then you can use the following tutorial.

How to restore grub using Live CD
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)

I'm not a grub expert, but the above link saved me from reinstalling before.
Hope this helps,
James.

PS. You can see if your grub editor left you a backup file to use too.

---

### Post by keplerspeed on 2009-09-15
Did you back up your /boot/grub/menu.lst before editing? If so, the easiest way would be to boot from cd and replace the menu.lst with the backup. Or just edit the menu.lst and remove the 'lock' option, as lindsay has suggested.

IF you used gedit to edit /boot/grub/menu.lst there will be a backup /boot/grub/menu.lst~

---

### Post by artemenko on 2009-09-18
> First you have to try to remove the words "lock" from /boot/grub/grub.lst ((I think)).

Can I change the grub.lst from a live CD?

I can use windows recovery console ("fixmbr" command") to blast through the locked grub to get at the windows partition.

Then, when I reinstall grub from the live CD to try and get into the Ubuntu partition -- everything is locked again, even after a fresh grub reinstall because it's referencing the same locked grub.lst file.

---

