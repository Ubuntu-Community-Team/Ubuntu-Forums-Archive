---
title: "Which Installation Process Should I Choose?"
date: 2011-09-23
forum: General Help
---

### Post by EpicTTR on 2011-09-23
So, I'm running Ubuntu in a virtual machine (Oracle VM VirtualBox), and I've set it all up and booted it all up, and there's two options for installation: Try Ubuntu and Install Ubuntu.

Now, I want to completely install Ubuntu - but only to the virtual machine, not to my regular machine. However, I'm not sure what I should click, because when I select Install Ubuntu it says how it'll delete all files on disk and how it'll install over everything.

What should I click to completely install Ubuntu to the virtual machine, but not over Windows on my regular machine?

---

### Post by seawolf167 on 2011-09-23
You need to download the Ubuntu iso file, then mount that iso file inside the virtual machine so that it boots off of it the first start to allow installation. Take a look at the [documentation]("https://help.ubuntu.com/community/VirtualBox") here (specifically [this section]("https://help.ubuntu.com/community/VirtualBox/FirstVM")).

---

### Post by EpicTTR on 2011-09-23
> **seawolf167 said:**
> You need to download the Ubuntu iso file, then mount that iso file inside the virtual machine so that it boots off of it the first start to allow installation. Take a look at the [documentation]("https://help.ubuntu.com/community/VirtualBox") here (specifically [this section]("https://help.ubuntu.com/community/VirtualBox/FirstVM")).

I think I may have worded my question in not quite the way I wanted to. I've completely set up my virtual machine and mounted the ISO inside the virtual machine. When it boots up, I get a screen that looks like:

[IMG]http://i.imgur.com/IPzWj.png[/IMG]

Now, I'm wondering which one I should click, "Try Ubuntu" or "Install Ubuntu". I want to install Ubuntu completely to my virtual machine, and not to my computer, so if I click "Install Ubuntu" while its running in the virtual machine, will it only install to the virtual machine, because on the next screen it says "Allocate Disc Drive Space", and then it default selects "Erase disk and install Ubuntu", will that just erase the virtual machine's disk, or my actual computers disk?

---

### Post by patryk77 on 2011-09-23
Yes, you can erase the entire disk.

You should see the size of the disk being the size you defined when you setup the virtual machine.

Ubuntu refers to a disk, which is in reality an image file.

Edit: Oh, and you can install it from either Try or Install... The only difference is that if you use "Try" you can explore the system before /while running the installer

---

### Post by seawolf167 on 2011-09-23
If it is running off the iso image inside your virtual machine (which it is), you can simply select to install ubuntu and use the entire disk, erasing any contents (an empty file) which exist.

---

### Post by EpicTTR on 2011-09-23
> **patryk77 said:**
> Yes, you can erase the entire disk.

You should see the size of the disk being the size you defined when you setup the virtual machine.

Ubuntu refers to a disk, which is in reality an image file.

Edit: Oh, and you can install it from either Try or Install... The only difference is that if you use "Try" you can explore the system before /while running the installer

So, then the disk it'll erase is the virtual disk, right?


I just don't want it to wipe out Windows or my other files, it'll be completely contained within the virtual machine, correct?

---

### Post by seawolf167 on 2011-09-23
> **EpicTTR said:**
> So, then the disk it'll erase is the virtual disk, right?

VBox creates a virtual disk which is [usually] setup as a dynamically expanding file on the host operating system. When you boot off the cd in the virtual machine, anything saved/deleted/etc. is done so on the virtual disk (the file on the host). So by clicking to install and erase the contents, you are installing Ubuntu to an empty file [as this is the initial setup for a virtual disk that has just been created - and is thus empty/blank].

---

### Post by patryk77 on 2011-09-23
> **EpicTTR said:**
> So, then the disk it'll erase is the virtual disk, right?


I just don't want it to wipe out Windows or my other files, it'll be completely contained within the virtual machine, correct?

That's right. Your files are safe.

---

