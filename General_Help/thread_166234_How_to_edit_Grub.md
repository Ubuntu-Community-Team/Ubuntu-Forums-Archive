---
title: "How to edit Grub?"
date: 2006-04-26
forum: General Help
---

### Post by minghai on 2006-04-26
Hi all,

   I've just downloaded Dapper beta iso and extracted it to a seperate partition hda8.  Is there any way to edit Grub so I can boot into hda8 and do a clean install of Dapper beta into another partition (hda7)?  Thank you.

Ming Hai

---

### Post by aysiu on 2006-04-26
You extracted the .ISO...?

Where is Grub right now? Which partition has the /boot/grub/menu.lst for it?

Are you trying to install Ubuntu to /dev/hda7 or copy /dev/hda8 to /dev/hda7?

---

### Post by minghai on 2006-04-26
I extracted the iso, putting all its contents into hda8.

Grub is in hda7 which is where I wanna install Dapper into ... now that I'm typing this, that seems like its not gonna work huh?  Should I install Grub into another partition?  Is there an easy way to move it?  I was hoping I could keep extracting different ISOs (Kubuntu, Edubuntu, etc) into hda8 and somehow do a clean install into hda8 so I can keep trying different distributions.

Ming Hai

---

### Post by aysiu on 2006-04-26
I don't believe you can install from one partition to another using the extracted contents of an .ISO.

---

### Post by Toxicity999 on 2006-04-26
That is a little obscure... you could I guess set it up as a remote repo but it's all on the same harddrive so that would be... weird at best and then you would already need a really basic installation... why not just create a cd... or if you want to be pretty about it use espresso on the live CD.

---

### Post by minghai on 2006-04-26
Yeah, the more I think about it, the more I realise I hadn't really thought it through properly.  What I essentially wanted to do was have a way to make successive clean installs of distros (like Dapper beta, Xubuntu beta, kubuntu beta) without burning CDs, just downloading the ISOs and somehow using them to install.

Ming Hai

---

### Post by aysiu on 2006-04-26
[QUOTE=minghai]Yeah, the more I think about it, the more I realise I hadn't really thought it through properly.  What I essentially wanted to do was have a way to make successive clean installs of distros (like Dapper beta, Xubuntu beta, kubuntu beta) without burning CDs, just downloading the ISOs and somehow using them to install.[/QUOTE] You know you can have Xubuntu, Kubuntu, and Ubuntu all on one installation, right? Since you said "clean installs," though, I'm going to assume you want some kind of triple-boot situation instead. You can actually do that if you burn **one** CD. Download an .ISO and burn it as a disk image.

Then boot it up and install whatever it is (for the sake of this example, let's say it's Ubuntu). Install it and put Grub on the MBR.

Then reboot and do a server install (at the boot prompt, type ```
server
``` and hit Enter instead of just hitting Enter without typing anything). For partitioning, choose either to resize automatically using free space or resize manually (if you knwo what you're doing). Put Grub on the MBR again--this should automatically add Ubuntu to the boot menu. Then when you log into a text-only prompt, type ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

Then reboot and do another server install, same deal with partitioning. Put Grub on the MBR one last time--this should add Ubuntu and Kubuntu to the boot menu. Type in ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by minghai on 2006-04-26
Ok, I'll give it a shot.  Thanks!

Ming Hai

---

