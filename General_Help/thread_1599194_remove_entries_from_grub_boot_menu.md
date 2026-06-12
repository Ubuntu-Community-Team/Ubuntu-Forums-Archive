---
title: "remove entries from grub boot menu"
date: 2010-10-17
forum: General Help
---

### Post by lunit2 on 2010-10-17
Hi,

How can I remove entries from my grub menu?

Like from the grub.cfg file, but it is not supposed to be edited. I read the guide but couldn't find anything.



Thanks.

---

### Post by TeoBigusGeekus on 2010-10-17
If you have a lot of kernels installed, open synaptic package manager, search for linux image and remove all the kernels except from the last 2.
Then 
```
sudo update-grub
```
This way, not only will the abundant lines will be deleted from your grub menu, but you'll free up some space from your hd.

---

### Post by lunit2 on 2010-10-17
No its for other linux versions, not ubuntu.

---

### Post by drs305 on 2010-10-17
You will have to be a bit more specific of what you want to delete entries for: kernels, memtest86+, recovery mode, other OS's, etc.

For starters, you can read the "Built-In Settings..." section of this thread on how to easily remove some of the more mundane entries:
[Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

---

### Post by lunit2 on 2010-10-18
Yes, what I wanna do is remove 3 of my 4 slackware sections. I only wanna use the last in the list as it shows up in grub.

I read the title tweaks but haven't figured it out yet.

---

### Post by tristan on 2010-10-18
You actually can edit the grub.cfg file if you are careful. I've edited mine to rename the entries to something simpler eg

Ubuntu 10.10
Ubuntu Recovery
Memtest
Windows 7

However it will be overwritten the next time grub is reconfigured.

---

### Post by lunit2 on 2010-10-18
Oh ok, thanks. That did it.

But anyway, is there a better way to do it? The proper way? This kinda seems like a "fix". if you get what I mean. :)

---

### Post by drs305 on 2010-10-18
> **lunit2 said:**
> Oh ok, thanks. That did it.

But anyway, is there a better way to do it? The proper way? This kinda seems like a "fix". if you get what I mean. :)

I wrote the Tweaks thread and admit it can be difficult to follow. If you don't plan on changing partitions, the easiest way to use the tweaks in the 30_os-prober section is to hide them by device (sda1, sdc3, etc). That way you don't have to worry too much about titles.

If you need help just post in that thread. Include your grub.cfg file.

---

### Post by oldfred on 2010-10-18
I brute force it by copying most into 40_custom and editing there:

Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Copy the other system entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by marcusjames on 2010-10-18
For my 2 cents using a customised boot menu is more work on an upgrade..
the other thing i noticed in this thread is that u can in fact relabel the entries without hacking the .cfg......people often say u shouldnt hand edit and then say they did it anyway............thats based on a fundamental misunderstanding of what the cfg file....and why it is never necessary to change it - most peeps do it in sheer desperation lol......

---

