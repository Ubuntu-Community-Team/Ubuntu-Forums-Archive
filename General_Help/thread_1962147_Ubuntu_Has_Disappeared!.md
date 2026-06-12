---
title: "Ubuntu Has Disappeared!"
date: 2012-04-20
forum: General Help
---

### Post by demonboy on 2012-04-20
Unfortunately I had to do some recovery work on Windows 7 and when I stuck the disk in I spent ages waiting for it to do its recovery business. Seems it wasn't recovering but kinda half re-installed W7 files (I didn't lose data).

When I went to reboot I lost the grub screen and can now no longer access my Ubuntu installation.

In Windows I used Gparted and I currently have the following disk structure:

> 
/dev/sda1 ntfs 200Gb
/dev/sda2 extended 97Gb
  /dev/sda5 ext4 92Gb
  /dev/sda6 linux-swap 5Gb


I have all my data backed up and it might just be easier to reinstall both W7 and Ubuntu again but if there is a quick solution to my problem I would be grateful to hear it.

---

### Post by for.i.am.root on 2012-04-20
Boot to a live CD and re-install grub.
This will also update your initramfs, just in case.

Applications - Accessories - Terminal

sudo umount /dev/sda5
sudo mount /dev/sda5 /mnt
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
chroot /mnt
sudo update-initramfs -u ALL
sudo update-grub

If you need to install grub:
sudo grub-install /dev/sda

---

### Post by jerome1232 on 2012-04-20
Yup windows re-wrote your mbr, isn't it fun how they do this stuff without asking?

---

### Post by demonboy on 2012-04-20
Thanks for the tip. I stuck the live disk in. I had to rename my account but it saved all my data. However it appears to have lost my screen res settings and, more importantly, the drivers for both my USB mouse and the mousepad. Not familiar with keyboard shortcuts I don't know  how to reinstate them. Any idea why it has lost these drivers or how I get them back?

[edit] I guess I should ask this second part in a new thread since the original problem has been solved. Cheers.

---

### Post by for.i.am.root on 2012-04-20
Why did you have to rename your account?

You probably just need to re-insert the modules for them. Not sure on this one.

---

### Post by jerome1232 on 2012-04-20
> **demonboy said:**
> Thanks for the tip. I stuck the live disk in. I had to rename my account but it saved all my data. However it appears to have lost my screen res settings and, more importantly, the drivers for both my USB mouse and the mousepad. Not familiar with keyboard shortcuts I don't know  how to reinstate them. Any idea why it has lost these drivers or how I get them back?

[edit] I guess I should ask this second part in a new thread since the original problem has been solved. Cheers.

You didn't reinstall did you...

that wasn't the advice given.

---

### Post by for.i.am.root on 2012-04-20
> 
Boot to a live CD and re-install grub.


I think he misunderstood me and re-installed his OS :O

Oops.

for.i.am.root STOP giving bad advice.

Bad root!

---

### Post by demonboy on 2012-04-21
> **for.i.am.root said:**
> Why did you have to rename your account?

You probably just need to re-insert the modules for them. Not sure on this one.

I inserted the disk and simply followed the wizard, hoping that there would be an option to 'repair' like there is on the Windows disk. I've only ever used the Live CD to do a clean install and am unfamiliar with installing just components. There was no repair option so I just continued until I realised I was re-creating my old login. All the files were still there so I wouldn't have called this a reinstall, but I guess that's just semantics. 

Because most of my documents are in clouds and on external hard drives in the end I reformatted my hard disk and started again, something I tend to do once a year or so anyway. No big deal.

---

### Post by GreatDanton on 2012-04-21
If you are using Windows, then it's good for you to reinstall it every year, because otherwise your system will become very slow. However for Ubuntu there is no need to do that :)

---

### Post by demonboy on 2012-04-21
Absolutely!

---

