---
title: "How to fix my broken system ?"
date: 2010-06-10
forum: General Help
---

### Post by ibrahim.k on 2010-06-10
Hi,

after shutting down my laptop the hard way because the system was frozen,

I can not boot anymore ,

I get the user name and password screen

but after typing the user name and password I get a black screen and cursor becomes like (X) 


[SIZE=5]please tell me how to fix this or at least how to backup my evolution mails and firefox bookmarks[/SIZE]

I am now booting via ubuntu installation disc, " try without installation"

Thnx

---

### Post by ibrahim.k on 2010-06-10
I found the bookmarks folder but i dont have permissions to access it, because i am now booting via ubuntu live cd.

---

### Post by wilee-nilee on 2010-06-10
I would boot into the second line of the kernel, recovery what ever it's called, and then fix broken packages then boot normally if it brings you to a command line login and type startx.

This is if you have Ubuntu running independently of any other OS, in other words not a wubi install.

It has been a long day so I can't remember the kernel line name.

If your using wubi and did a hard shutdown I doubt this will work and shouldn't be used without more help.

---

### Post by bcbc on 2010-06-10
Can you plug in a usb and then just mount your ubuntu hard drive and copy your /home directory. This will have save all your data.

I believe your evolution mails should be under /home/<user>/.evolution

But now's probably a good time to back up your entire /home directory in case it gets messed up while you fix your system.

---

### Post by ibrahim.k on 2010-06-10
I do not have any options when booting, I am using ubuntu only not dual boot.

so how can i let this options appear?

Thnx in advance

---

### Post by ibrahim.k on 2010-06-10
> **bcbc said:**
> Can you plug in a usb and then just mount your ubuntu hard drive and copy your /home directory. This will have save all your data.

I believe your evolution mails should be under /home/<user>/.evolution

But now's probably a good time to back up your entire /home directory in case it gets messed up while you fix your system.


yes i have copied all the data and i restored firefox bookmarks, 

but now it would be better if i can fix the previous system.

Thnx

---

### Post by bcbc on 2010-06-10
When you boot, hold down the SHIFT key. This should bring up the grub2 menu.

If you are running legacy grub, hold down the ESC key.

The second menu item is the recovery menu. Select it and boot. Then you'll see some recovery options.

---

