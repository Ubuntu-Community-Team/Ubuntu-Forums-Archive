---
title: "Deleting Grub (windows dual boot)"
date: 2010-06-02
forum: General Help
---

### Post by c.delgadoa on 2010-06-02
Hello Friends. 

I have my laptop NC6910p from HP with windows 7 and Ubuntu lucid as dual boot managed by grub loader. 

Yesterday I made a mistake and formated the ubuntu partition as ntfs with a windows media because I needed to do a test in that partition. Now, off course, when I boot the computer is not finding GRUB and naturally not booting to windows.

I tried to boot with ubuntu live cd and did the apt-get install ms-sys but it just does not find the package. I can browse the windows files and all of that. 

If you know what I can do in order to have the windows loader picked up during post, let me know. 

thank you.

---

### Post by TheNosh on 2010-06-02
you can do a few things.

- you can reinstall ubuntu (or any other distro or OS that uses Grub)

- you can reinstall Grub by itself (which i think is sill if you no longer have a linux partition.)

- or you can repair the windows bootloader in the MBR with your windows installation disk (assuming you have one.)

---

### Post by WorMzy on 2010-06-02
If you want to reinstall grub, you will also need to either A) install Ubuntu too, or B) create a dedicated boot partition. The part of grub that you install to the MBR is basically just a pointer to a /boot folder on a Linux filesystem, if you don't have a Linux filesystem with grub installed on it, then grub will always fail to load anything and just return an error. If you follow B and just create a boot partition, then you'll have a hard time managing it without a Ubuntu (or other Linux based OS) installation, as you can't easily access Linux filesystems from within Windows.

However, Windows comes with it's own boot loader, which you should be able to configure how you like; so why do you want to reinstall grub?

---

### Post by TheNosh on 2010-06-02
> **WorMzy said:**
> why do you want to reinstall grub?

i don't think OP said they wanted to reinstall Grub. they simply want a viable course of action that would make windows boot properly again. reinstalling Grub would be one path, and without a windows installation disk, fixing the windows bootloader would be quite difficult iirc.

---

### Post by WorMzy on 2010-06-02
Ah, yes, you're right. I must not have read the first post properly.

ms-sys isn't in the repos, but you can download the source [here]("http://sourceforge.net/projects/ms-sys/files/ms-sys%20stable/2.2.0/ms-sys-2.2.0.tar.gz/download"). Just extract the contents of the archive, cd into the newly created directory, run make, then you can run the application with ```
bin/ms-sys
```

```
bin/ms-sys --mbr7 /dev/sda
``` should install a Windows 7 bootloader to sda. I haven't used it myself though.

---

### Post by Mark Phelps on 2010-06-03
While the ms-sys approach MAY work, a safer approach would be to repair the Win7 boot loader using MS Windows software.

Since you most probably did NOT use the Win7 Backup function to create and burn your own Win7 Repair CD, you can download an image from the link below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once downloaded, burn the image to CD, boot from that, and run Startup Repair three times -- it fixes one item per pass and replaces the MBR on the third pass.

---

