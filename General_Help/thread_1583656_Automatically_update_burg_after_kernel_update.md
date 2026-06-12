---
title: "Automatically update burg after kernel update"
date: 2010-09-28
forum: General Help
---

### Post by timgood on 2010-09-28
Title says it all really: is there an easy way to get burg to automatically update after a new kernel install in the same way that grub does it?

I live in hope.

---

### Post by eumetaxas on 2010-09-28
Unnfortunately found out that it does not after deleting the old kernel.
:confused:

---

### Post by stinkeye on 2010-09-28
To update burg manually
```
sudo update-burg
```

and to make burg update automatically with a new kernel
it is suggested [**_[COLOR="DarkRed"]here[/COLOR]_**]("https://bugs.launchpad.net/burg/+bug/594431") to alter your /etc/kernel-img.conf file to```
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
[COLOR="Red"]postinst_hook = update-burg
postrm_hook = update-burg[/COLOR]
```

---

### Post by timgood on 2010-09-28
Many thanks for this - was a pain having to do it manually. I will mark this thread solved.

---

### Post by LordNodens on 2011-07-18
Thanks a lot for this!

---

### Post by dcstar on 2012-09-06
Ok, this is a resurrection of this old thread to add in some information for using **burg** in 12.04 and having it updated automatically after a kernel install/removal, so open a terminal and:
```
cd /etc/kernel/postinst.d
sudo cp zz-update-grub zz-update-burg
sudo gedit zz-update-burg
```
Replace all "grub" strings with "burg" then save and close the file.
```
sudo cp zz-update-burg /etc/kernel/postrm.d
```

Now when a kernel is installed or removed **update-burg** will be called to automatically update burg. If you no longer use grub then you can probably remove the old grub update files, but leaving them won't do much harm.

---

