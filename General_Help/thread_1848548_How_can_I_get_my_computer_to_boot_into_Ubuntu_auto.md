---
title: "How can I get my computer to boot into Ubuntu automatically"
date: 2011-09-22
forum: General Help
---

### Post by wayofthedragon on 2011-09-22
How can i get my computer to boot into Ubuntu automatically without it asking me which operating system to boot into? am using Ubuntu 10.10 and have grub 1.98

---

### Post by aura7 on 2011-09-22
Install Startup Manager from Synatic, you can configure you boot with it.

---

### Post by wayofthedragon on 2011-09-22
> **aura7 said:**
> Install Startup Manager from Synatic, you can configure you boot with it.

Ok what's synatic where can i get that? thanks

---

### Post by oldfred on 2011-09-22
Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Not sure if SUM has been updated to work with the very newest grub 1.99, yet but with the older versions it is fine.

---

### Post by rewyllys on 2011-09-22
> **wayofthedragon said:**
> Ok what's synatic where can i get that? thanks
It's actually "Synaptic", short for "Synaptic Package Manager".  You can open it by clicking on System-->Administration, and choosing it.

Once you're in the SPM, enter Startup Manager in the search slot; when you see "startupmanager" listed as an available package, right-click on it and choose "Mark for installation".  Then left-click on "Apply" in the toolbar.  The result will be that Startup-Manager will be installed, and will be available via System-->Administration.

---

### Post by wayofthedragon on 2011-09-22
> **rewyllys said:**
> It's actually "Synaptic", short for "Synaptic Package Manager".  You can open it by clicking on System-->Administration, and choosing it.

Once you're in the SPM, enter Startup Manager in the search slot; when you see "startupmanager" listed as an available package, right-click on it and choose "Mark for installation".  Then left-click on "Apply" in the toolbar.  The result will be that Startup-Manager will be installed, and will be available via System-->Administration.

K installed it. Put Ubuntu as default but it's still not working. Don't think that was what i need. What I'm wanting to do is when I start up my computer and you know how the little black screen appears and has Windows first then Ubuntu? Well I'm wanting it to have Ubuntu first then Windows that way it boots into Ubuntu automatically without me having to choose. Wasn't talking about second screen was talking about first.

---

### Post by garvinrick4 on 2011-09-22
Here is something of interest in a GUI method of managing grub.
It is very much worth a look for those who like using graphic interface.
[HOWTO: Grub Customizer - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

---

### Post by oldfred on 2011-09-22
Are you booting with Windows? And have Wubi then the Windows boot loader loads wubi with grub?

If you have wubi you have to edit boot loaders in Windows. If Vista or 7 you have to use BCDedit or XP edit boot.ini.

---

### Post by wayofthedragon on 2011-09-22
> **oldfred said:**
> Are you booting with Windows? And have Wubi then the Windows boot loader loads wubi with grub?

If you have wubi you have to edit boot loaders in Windows. If Vista or 7 you have to use BCDedit or XP edit boot.ini.

Don't know what I have. How can I check? I figured I would have to edit the boot loaders in Windows how can I check to see what I have so I can let you know?

Also I have Vista.

---

### Post by oldfred on 2011-09-22
Did you create partitions or install "inside" windows?

If you run bcdedit in your Vista do you have two entries, one Vista and the other Wubi? It should let you change order.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

