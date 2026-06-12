---
title: "Stuck at grub rescue&gt;"
date: 2010-06-08
forum: General Help
---

### Post by rchristy1 on 2010-06-08
I installed Karmic on a slave drive last night w/ Grub2. I was able to boot both windows xp and ubuntu several times although Grub was extremely slow. Ubuntu just froze and upon reboot (even w/ live cd in i just get this)
 
GRUB loading
error: no such disk
grub rescue>
 
any help is greatly appreciated

---

### Post by beardo_jax on 2010-06-08
I got the same thing yesterday trying to run Lucid from an external. Then I tried it on another machine and it worked fine. If I figure anything out I'll post it here.

---

### Post by rchristy1 on 2010-06-08
Was finally able to get into bios and it no longer sees the hd  I installed linux on. any ideas?

---

### Post by rchristy1 on 2010-06-08
Now I have booted from live cd and gone to install and linux sees the disk SCSI2 (0,1,0) (sdb). This is the hd that bios does not see that I already have ubuntu installed on. Very strange.

---

### Post by Leppie on 2010-06-08
so install grub2 in the mbr of the first hd (hda):
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
/dev/sdb1 is the root partition of your ubuntu install, amend if different for your install.

---

### Post by rchristy1 on 2010-06-08
You mean the hd w/ windows on it? I set the bios up to boot from my 2nd drive with linux.

---

### Post by Leppie on 2010-06-08
> **rchristy1 said:**
> You mean the hd w/ windows on it? I set the bios up to boot from my 2nd drive with linux.
well, you stated that booting off that hd is slow. try using the other hd as boot device, you can always revert if you want.

---

### Post by rchristy1 on 2010-06-08
ok, if you say so. I was afraid to mess with the windows hd, being a newbie. I know that one works fine and didn't want to corrupt it in any way
 
Thank you, I'll let you know how it goes

---

### Post by rchristy1 on 2010-06-08
I am really afraid to mess w/ the hd with windows on it yet. Ubuntu finally loaded after staring at Gub loading for 5 minutes. Would you suggest a different version of grub possibly?

---

### Post by Leppie on 2010-06-08
could you explain what drives you've got in your system? are they both sata, or one sata and one ide, or both ide, or whatever?

as long as you've got an ubuntu livecd at hand, you can always set the boot record to factory defaults with little effort. the only exception would be if the drive is physically damaged...

i don't think a different version of grub would make a lot of difference. grub2 is very powerful, though in some rare cases not compatible wih old drives.

---

### Post by rchristy1 on 2010-06-08
They are both IDE. 
 
One is 30 GB (windows). This is set as IDE primary master.
 
The 40 gb IDE drive that has Ubuntu installed is set as the IDE secondary slave.

---

### Post by rchristy1 on 2010-06-08
once grub finally loads (6-7 minutes) the os loads quickly and everything seems fine. I would think if there were a physical problem with the disk it would manifest itself elsewhere. But then again I don't know my a$$ from a hole in the ground. Thank you for you patience.

---

### Post by rchristy1 on 2010-06-09
Ran: sudo badblocks -s -v /dev/sda1
 
0 bad blocks fund

---

