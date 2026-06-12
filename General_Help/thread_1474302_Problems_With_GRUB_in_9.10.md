---
title: "Problems With GRUB in 9.10"
date: 2010-05-05
forum: General Help
---

### Post by vicroc4 on 2010-05-05
Okay, I'm not entirely certain what happened here, but it seems like immediately after I updated one of my Ubuntu installations (my family has four currently - all of which I am responsible for administering), GRUB decided that it was going to bring up a shell instead of the boot options.

This particular instance of Ubuntu is installed as Wubi under Vista - the Vista install has been having some boot problems as well, but I thought that they were unrelated as Ubuntu seemed to run fine.  Now I'm not so sure.

In any case, what originally happened when I tried to boot (when things were working) was that it came up with Vista's boot menu, then, when I selected the Ubuntu option, it came up with the usual GRUB menu to boot into Ubuntu.  Now it gives me a GRUB shell whenever I try to boot into Ubuntu - not only is this a little odd considering the usual behavior of GRUB with Ubuntu, I have no clue what I'm doing in the GRUB shell.

Seeing as I don't know what's going on, I'm not sure what other information I should provide, but a basic summary of my system is as follows:

Ubuntu Version: 9.10 installed as WUBI
Host OS: Windows Vista SP1
Model: HP/Compaq Presario F572US

---

### Post by pechacek on 2010-05-06
Hey vicroc4,

I am in the same situation, except this is a new Wubi install on Win7. Everything went fine, but when I choose Ubuntu in the Win7 boot menu, it goes to the Grub shell and have no clue what to do.

Sorry I don't have an answer for you, but I think our problems are along the same lines. One thing that I did notice is in the installation directory, the path ubuntu\disks\boot\grub does not have anything in it. I had Wubi working just fine under a WinXP install, then I did a clean install of Win7 and now can't get it to work.

Hopefully someone can shed some light on this issue.

Good luck!

---

### Post by cbecker78 on 2010-05-06
the below bug on launchpad seems similar to your problems:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

Look at posts 1 and 19 first and see if one of those works. 

If not, post 4 may be a possible route.

---

### Post by vicroc4 on 2010-05-07
cbecker: Thanks.  I was able to get it to boot using the linux-image-2.6.31-17-generic and the steps outlined in your link.  Curiously, 2.6.31-14-generic seems to not want to work either.  I honestly wonder if whatever made my Vista unworkable didn't do the same for Ubuntu.  Since they're essentially on the same disk, I would not be entirely surprised. XD  Anyway, I uninstalled 2.6.31-21-generic for now until I can figure out how to install it without destroying the GRUB configuration files and/or get it to boot from the GRUB console.  It's giving me a kernel panic when I try to boot as 2.6.31-21-generic for some weird reason - I'll try to see if I can get the dump next time I go into Ubuntu.  Again, thanks for the help. :)

---

### Post by cbecker78 on 2010-05-10
Glad you were able to get something working!  The kernel panic is a bit out of my league, but good luck with that!

---

