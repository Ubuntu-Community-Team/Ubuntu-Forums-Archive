---
title: "boot menu getting bigger"
date: 2011-06-29
forum: General Help
---

### Post by soulcat on 2011-06-29
hi

my grub boot menu keeps getting bigger i assume after updates i started off originally with 2 options for ubuntu & one for win 7, how can i delete the one's that are not used. pic attached

---

### Post by seawolf167 on 2011-06-29
Easiest way would be to search in the package manager (System -> Administration -> Synaptic Package Manager) for linux-image, then remove any/all **that are not your current kernel**, which you can find by typing in this at a terminal

```
uname -r
```

---

### Post by drs305 on 2011-06-29
It's due to new kernels being added, which increase the size of the menu. The good news is, the latest Grub 2 in Natty has a way of dealing with this (submenus). For earlier versions, you can remove older kernels. I recommend Ubuntu Tweak. Here is a link for removing older kernels, although I'd recommend keeping at least one older one as a backup.
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by nzjethro on 2011-06-29
As well as Grub2, some graphical Grub interfaces (like BURG, which I use, and grub-customiser) allow you to "fold" old kernels and recovery modes away (until you need them) and reorder your OSes, as well as giving you a pretty looking boot menu.

[Here's how to install BURG]("http://code.google.com/p/burg/wiki/InstallUbuntu")
[And here's grub customiser]("https://launchpad.net/grub-customizer")

:)

---

### Post by amjjawad on 2011-06-29
Used to remove old Kernel from Synaptic and always keeping one extra just in case of disasters :)

---

### Post by soulcat on 2011-06-29
hi

thanx for the replys i went for unbuntu tweak but could not install via the instructions within the link saying 'Error: Dependency is not satisfiable: python (>= 2.7)' also i decided to download & save to the download folder but unsure how to install

regards

---

### Post by varunendra on 2011-06-30
> **seawolf167 said:**
> Easiest way would be to search in the package manager (System -> Administration -> Synaptic Package Manager) for linux-image, then remove any/all **that are not your current kernel**, which you can find by typing in this at a terminal

```
uname -r
```
+1
This is how I do it-

[LIST]
[*]open synaptic
[*]type **linux **in search-box (make sure packages are listed by **Status > Installed** to avoid a huge mess in the list)
[*]arrange list in alphabetical order
[*]scroll way down until I start finding packages that start with 'linux'
[*]check (to completely remove) everything that is associated with earlier versions. Precisely - linux-headers and linux-image. BE CAREFUL NOT TO CHECK ANYTHING of CURRENT VERSION.
[*]I'd also suggest to 'Install' "linux-headers" for the current version if not already installed. They're required if you install something that requires to be compiled before installation (like virtualbox dkms).
[/LIST]
 > **amjjawad said:**
> Used to remove old Kernel from Synaptic and always keeping one extra just in case of disasters :)
- good point. I also do it when I'm suspicious about the latest kernel.

From your screenshots, it seems you can safely remove linux-image (and headers) "2.6.35-22". Also "2.6.35-28" if you're sure the current one ("2.6.35.30") is working fine and you'll not need the earlier one.

---

### Post by soulcat on 2011-06-30
hi

thanx for great answers now sorted, before i close this thread as sorted what about the memory test also in the menu should i leave well alone or remove if so how ?


regards

---

### Post by seawolf167 on 2011-06-30
I'd leave that there - its not hurting anything by being present, and if you ever have random shutdowns, purchase new RAM, etc. you'll want to run memtest to ensure that the DIMMs are good and don't need to be RMA'd.

---

### Post by soulcat on 2011-06-30
ok cheers boot menu looks alot tidy now :D


regards

---

### Post by drs305 on 2011-06-30
If you want to remove it, all you have to do is make it's script in /etc/grub.d un-executable:

```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

Should you ever need it, you can change it back with: sudo chmod **+**x /etc/grub.d/20_memtest86+

---

### Post by Zero2Nine on 2011-06-30
It's best to keep one extra kernel version, so one before the latest. In case the newest version gives problems you can switch to the last properly working version. Kernels older than that can be safely removed.

---

