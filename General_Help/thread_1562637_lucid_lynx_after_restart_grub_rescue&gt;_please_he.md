---
title: "lucid lynx after restart grub rescue&gt; please help"
date: 2010-08-27
forum: General Help
---

### Post by douglaslees on 2010-08-27
Dear all,
 
i m a newbie when it comes to linux, but like the idea and hope one day to get away from microsoft all together. This is the second time I have tried to install ubuntu on my eeepc 1000HG in addition to windows 7. The first version was karmic koala netbook remix, and yesterday it was lucid lynx netbook remix. 
 
Its annoying because before the update packages are downloaded and installed it runs smoothly, even additional applications run with no problem, but after restart to complete installation the following error message appears.
 
error: no such device: 5290ea6f-1bdf-4eda-b56e-2f282662e188.
grub rescue>
 
 
I would be very grateful for any advice, and help.
 
Many thanks in advance.
 
Douglas

---

### Post by wilee-nilee on 2010-08-27
Are you installing from a live MS environment=wubi.

If this is the case your probably accepting a grub update, don't, grub in wubi is different then in a full install, don't install it to the mbr or a partition or upgrade it. 

Does this sound familiar with what has happened?

---

### Post by douglaslees on 2010-08-28
Hi! Thanks for your response, thats exactly what I did. I am quite tempted to install just ubuntu but I do not have a cd drive and it seems to be quite a complicated process to install from usb.
 
Thanks for your help, if I understand correctly then please correct me if I m wrong, I should not install grub updates from the update packages I download after the installation? This will avoid the system crashinG?
 
Also I was wondering if you could tell me wether it is a problem to install 10.04 alongside windows 7?
 
Many thanks for your help, I ll let you know how it goes. I really like the look of linux, but its been frustrating to lose so much time.
 
Regards,
 
Douglas

---

### Post by wilee-nilee on 2010-08-28
> **douglaslees said:**
> Hi! Thanks for your response, thats exactly what I did. I am quite tempted to install just ubuntu but I do not have a cd drive and it seems to be quite a complicated process to install from usb.
 
Thanks for your help, if I understand correctly then please correct me if I m wrong, I should not install grub updates from the update packages I download after the installation? This will avoid the system crashinG?
 
Also I was wondering if you could tell me wether it is a problem to install 10.04 alongside windows 7?
 
Many thanks for your help, I ll let you know how it goes. I really like the look of linux, but its been frustrating to lose so much time.
 
Regards,
 
Douglas

I have W7 and 2 versions of Ubuntu; Lucid and Maverick and 2 others in a virtual. What the key is are how many partitions you have as of now and what can be done. Snip  a screen shot of the disc manager in W7 and post it. Here is a picture of what gparted Ubuntu's disk manager looks like from my setup.
[ATTACH]167745[/ATTACH]

---

### Post by NibbleG on 2010-10-05
I have the same problem, though I was using Xubuntu through wubi.  Unfortunately I can't get rid of the Windows install at the moment.  Is there any hope?

---

### Post by NibbleG on 2010-10-05
And to clarify why I can't get rid of the Win 7 install, and possibly to show my dire and unfortunate situation. I am a young college student who needs to learn linux for school, and my mother "lent" me her netbook. I though I would be smart and install the wubi through Windows as it is easy to remove it after without overwriting the MBR or anything...
Oh how fate loves to be kind :P
So, please... help me if you can...

---

### Post by drs305 on 2010-10-05
NibbleG,

Edit: We determined that the "ls" command did not see any partitions (only hd0). See post 10 for solution.
***

If you get the "no such device" before any Grub menu appears:, try typing this (this assumes Windows is on sda1 (hd0,1). Change if different). 

To fill in the "linux" and initrd lines, don't type "...". Type the first part of the kernel and initrd image (vmlinuz and initrd.img) then double TAB to autocomplete that part of the line. In the linux line, don't forget to  add the rest after the autocompletion. Note: If it doesn't autocomplete, you probably haven't found the correct partition.

```
insmod ntfs
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-... root=/dev/sda1 loop=/ubuntu/disks/root.disk ro 
initrd /boot/initrd.img...
boot
```

---

### Post by NibbleG on 2010-10-05
I am attempting this as week speak, but does it change anything if I am in grub rescue> ?

---

### Post by NibbleG on 2010-10-05
I'm also building a usb Xubuntu live usb, and also, thanks for the speedy relpy.

---

### Post by NibbleG on 2010-10-05
Thanks DRS305, both installs work now.
in grub rescue ls would only show (hd0) nothing else...
Booting up with a live Xubuntu usb(i'm sure Ubuntu would also work) installing lilo and running: sudo lilo -M /dev/sda mbr
everything booted as normal.

---

