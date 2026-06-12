---
title: "Usability: Mounting a 2nd drive on startup without editing /etc/fstab"
date: 2010-10-13
forum: General Help
---

### Post by ean5533 on 2010-10-13
First, some background. On my system I have a 2nd hard drive that I use to store all my data (music, movies, docs, etc). It's actually divided into two partitions, but all of my data is stored on one partition (the second partition is irrelevant). Anyway, I auto-mount that data partition on startup so it's always mounted to the same place, **/media/disk**, and then in my home folder I create links to places on that drive. For example, my **/home/USERNAME/Music** folder is just a link to **/media/disk/Music**. This is all fine.

My concern is that it seems rather difficult to make that drive auto-mount. On every install of Ubuntu I've ever done (including 10.10 a couple days ago), I've always had to add a line to **/etc/fstab**. If I don't, that drive partition won't be re-mounted on reboot and all those links in my home folder will be broken until I manually mount the drive again. It's not that difficult to edit fstab, but I don't understand why it needs to be done that way. Shouldn't you be able to right-click a mounted drive, go to properties, and check "auto-mount on startup"? Is there some easier way that I'm just not aware of? Everything else in Ubuntu is trivially easy, but this one thing still forces me back to the command line (and forces me to look up the format I need for an fstab line).


Note: The command line doesn't scare me (I'm a programmer), and I know it works, but I still maintain that there should be a simpler way of accomplishing this task, like there is for everything else in this OS.

Second note: I know this topic has come up about 800 times in the last few years, and I did my best to search for an answer, but it seems that every thread ends with "just add a line to **/etc/fstab**".

**EDIT:** This is specifically Ubuntu (GNOME). I haven't tested this problem on KDE or any other DE.

---

### Post by JustinR on 2010-10-13
> **ean5533 said:**
> First, some background. On my system I have a 2nd hard drive that I use to store all my data (music, movies, docs, etc). It's actually divided into two partitions, but all of my data is stored on one partition (the second partition is irrelevant). Anyway, I auto-mount that data partition on startup so it's always mounted to the same place, **/media/disk**, and then in my home folder I create links to places on that drive. For example, my **/home/USERNAME/Music** folder is just a link to **/media/disk/Music**. This is all fine.

My concern is that it seems rather difficult to make that drive auto-mount. On every install of Ubuntu I've ever done (including 10.10 a couple days ago), I've always had to add a line to **/etc/fstab**. If I don't, that drive partition won't be re-mounted on reboot and all those links in my home folder will be broken until I manually mount the drive again. It's not that difficult to edit fstab, but I don't understand why it needs to be done that way. Shouldn't you be able to right-click a mounted drive, go to properties, and check "auto-mount on startup"? Is there some easier way that I'm just not aware of? Everything else in Ubuntu is trivially easy, but this one thing still forces me back to the command line (and forces me to look up the format I need for an fstab line).


Note: The command line doesn't scare me (I'm a programmer), and I know it works, but I still maintain that there should be a simpler way of accomplishing this task, like there is for everything else in this OS.

Second note: I know this topic has come up about 800 times in the last few years, and I did my best to search for an answer, but it seems that every thread ends with "just add a line to **/etc/fstab**".

**EDIT:** This is specifically Ubuntu (GNOME). I haven't tested this problem on KDE or any other DE.

If you don't want to edit '/etc/fstab' why don't you just add a command in System > Preferences > Startup Applications that does this command:
```

mount /dev/sdX /media/FOLDER

```

---

### Post by ean5533 on 2010-10-13
> **JustinR said:**
> If you don't want to edit '/etc/fstab' why don't you just add a command in System > Preferences > Startup Applications that does this command:
```

mount /dev/sdX /media/FOLDER

```

I haven't tried that, and I'm sure it would work, but it still seems unintuitive and overly complex. Are there any simpler ways? I noticed that this has been [submitted]("http://brainstorm.ubuntu.com/idea/25897/") to the brainstorm but hasn't received any followup.

---

### Post by JustinR on 2010-10-13
> **ean5533 said:**
> I haven't tried that, and I'm sure it would work, but it still seems unintuitive and overly complex. Are there any simpler ways? I noticed that this has been [submitted]("http://brainstorm.ubuntu.com/idea/25897/") to the brainstorm but hasn't received any followup.

You can't get simpler than Ubuntu's own startup manager - especially when your using a simple mount command in the startup manager.

---

### Post by ean5533 on 2010-10-13
> **JustinR said:**
> You can't get simpler than Ubuntu's own startup manager - especially when your using a simple mount command in the startup manager.

The way I described seems simpler to me. Right-click a mounted partition, click Properties, check the auto-mount checkbox. Much easier than having to:

[LIST]
[*]Know the syntax of a mount command
[*]Figure out what device name a mounted partition has (/**dev/sdb1**? **/dev/sdb**2? **/dev/sdc1**?)
[*]Manually create a folder in **/media** (which requires root) and give it the proper permissions (which it won't have by default).
[/LIST]

---

### Post by Morbius1 on 2010-10-13
There are a lot of utilities that will do this none of which I would recommend but I would like to point out something:
> On every install of Ubuntu I've ever done (including 10.10 a couple days ago), I've always had to add a line to **/etc/fstab**.You don't have to add anything to fstab after you install if you use the "Specify partitions manually" option during the initial install.

You will get a window that looks like the attachment. Double click an ntfs partition for example and it will ask you 3 questions:

(1) Where do you want it mounted? ( and it will create the mount point automatically )
(2) How is it formatted ?
(3) Do you want it formatted ? - Most likely you do not.

When you first boot you will have a line in fstab already there.

---

### Post by ean5533 on 2010-10-13
> **Morbius1 said:**
> There are a lot of utilities that will do this none of which I would recommend but I would like to point out something:
You don't have to add anything to fstab after you install if you use the "Specify partitions manually" option during the initial install.

You will get a window that looks like the attachment. Double click an ntfs partition for example and it will ask you 3 questions:

(1) Where do you want it mounted? ( and it will create the mount point automatically )
(2) How is it formatted ?
(3) Do you want it formatted ? - Most likely you do not.

When you first boot you will have a line in fstab already there.

Ah ha! That's something I hadn't thought of. I think that's a pretty good way to do it next time I install Ubuntu. I still wish there were an easier way to do it post-install.

Thanks for the heads up.

---

### Post by spoon_ on 2010-10-13
This is simply a feature that Ubuntu should have but doesn't.

---

### Post by JustinR on 2010-10-13
> **ean5533 said:**
> The way I described seems simpler to me. Right-click a mounted partition, click Properties, check the auto-mount checkbox. Much easier than having to:

[LIST]
[*]Know the syntax of a mount command
[*]Figure out what device name a mounted partition has (/**dev/sdb1**? **/dev/sdb**2? **/dev/sdc1**?)
[*]Manually create a folder in **/media** (which requires root) and give it the proper permissions (which it won't have by default).
[/LIST]

When you mount a drive it's usually only a temporary drive - like  flash drive. If you wanted it to automount and have permissions, etc. then it sounds like you should just be making what ever drive you need on bootup an internal drive - instead of remounting it and editing permissions.

---

### Post by ean5533 on 2010-10-13
> **JustinR said:**
> When you mount a drive it's usually only a temporary drive - like  flash drive. If you wanted it to automount and have permissions, etc. then it sounds like you should just be making what ever drive you need on bootup an internal drive - instead of remounting it and editing permissions.

I think you're agreeing with me without realizing it. The drive I need on bootup **is** an internal drive. I don't **want** to remount it and edit permissions, but that's what I'm forced to do if I didn't already set it up during my Ubuntu install.

You're telling me that I "should just be making what ever drive you need on bootup an internal drive", and I agree; I'm saying that it should be easier to do that. That's all.

---

### Post by sinner99 on 2010-10-14
an fstab auto script from a trusted source...scans the system bus for whats there and sets the mount points etc. if you ask me that should be a task during system installation by now!!! cmon ubuntu! its 10.10 now! we all GONE MAVERICK lol
that should be this rls's official tagline BTW. lol :p

---

### Post by Morbius1 on 2010-10-15
> **sinner99 said:**
> an fstab auto script from a trusted source...scans the system bus for whats there and sets the mount points etc. if you ask me that should be a task during system installation by now!!! cmon ubuntu! its 10.10 now! we all GONE MAVERICK lol
that should be this rls's official tagline BTW. lol :p
It already exists. It's been there for quite some time.

See post #6 above.

---

