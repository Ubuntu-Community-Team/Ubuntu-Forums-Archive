---
title: "disaster:  won't boot at all"
date: 2011-03-25
forum: General Help
---

### Post by Total Noob on 2011-03-25
Major crisis. Ubuntu 10.4. Celeron M 1.5 chip in Acer laptop. 1GB Ram.

I have been using it like this for a full year, and now error message something like this: Install failure. Power configuration incorrectly installed. See administrator.

Sorry I don't have exact text; had to use Windows to get back on line at all, can't cut and paste that way.

I am the sole user. I never had any trouble with the power configuration, and have booted the thing thousands of times, including 15 minutes prior to this failure. Installation not really the problem, possibly file corruption, though that has not been a problem before either.

The only thing I can think of is that I have filled up the hard drive with data, and literally there is only about 2 mb of HD left. Could something have overwritten a crucial file like a power configuratin file? If so, that is a major snafu with Ubuntu.

Anyway, I have no idea how to fix this. Along with the error message comes a log-in ID, which I had turned to off in the initial set up, and when I enter the password, it simply recycles to the same point and repeats the error message.

I need a fix and need to save my data, not necessarily in that order.

Anybody?

---

### Post by drs305 on 2011-03-25
If it's a disk space issue, you can make some space by booting the LiveCD, mounting your Ubuntu partition and removing some files. Change XY to the appropriate values (for example, sd**a5**)
```

sudo mount /dev/sd**XY** /mnt
gksu nautilus /mnt/var/cache/apt/archives
```
Use SHIFT-DEL to delete the files in that folder. Do NOT delete the "partial" folder. 

You can also empty root's trash at /mnt/root/.local/share/Trash. Make sure you have hidden file viewing enabled. And you own trash at /mnt/home/<username>/.local/share/Trash. You can use SHIFT-DEL to delete the 'files' and 'info' folders. They will be recreated when needed.

Don't know if that is what your problem is but it will at least provide a bit of breathing room.

---

### Post by Total Noob on 2011-03-25
> **drs305 said:**
> If it's a disk space issue, you can make some space by booting the LiveCD, mounting your Ubuntu partition and removing some files. Change XY to the appropriate values (for example, sd**a5**)
```

sudo mount /dev/sd**XY** /mnt
gksu nautilus /mnt/var/cache/apt/archives
```
Use SHIFT-DEL to delete the files in that folder. Do NOT delete the "partial" folder. 

You can also empty root's trash at /mnt/root/.local/share/Trash. Make sure you have hidden file viewing enabled. And you own trash at /mnt/home/<username>/.local/share/Trash. You can use SHIFT-DEL to delete the 'files' and 'info' folders. They will be recreated when needed.

Don't know if that is what your problem is but it will at least provide a bit of breathing room.

Would this be possible as an alternate to the above? once I mount the sda5 with a live CD, will it show up in Places, allowing me to offload some of my data onto a keychain drive? Or alternately, is there some command that I can use to move that data to my keychain?

Thanks.

---

### Post by drs305 on 2011-03-25
You might actually see it in Places before you do anything. 

Sure, you can copy or move things do another partition. The .deb files in /var/cache/apt/archives are downloads used for installations but then aren't needed. Unless you have restricted bandwidth those files would be downloaded again should you need to reinstall something.

The file browser should allow you to copy/move the files if you operate as root. (gksu nautilus)

---

### Post by Total Noob on 2011-03-25
I did get the approximate wording of the error message. More or less, it is this:

Configuration default for GNOME Power Manager was not installed correctly. See Administrator.

As noted, it operated correctly for a year, so it really isn't an install error, one wouldn't think. Before shifting around data, is the amount of storage really the source of the problem, and will moving data provide a fix?

Or am I looking at offloading the data and then reinstalling Ubuntu out of necessity?

---

### Post by drs305 on 2011-03-25
> **Total Noob said:**
> Or am I looking at offloading the data and then reinstalling Ubuntu out of necessity?

You do not need to reinstall Ubuntu - at least not yet. If in fact there is no more disk space on the drive odd things can happen. It could give a power error one boot and something else on the next. You'd probably only have to delete a few of the .deb files if that was the problem.

Since you are consistently getting the same message about the gnome-power-manager, you might want to concentrate on that. You can use chroot and the LiveCD to reinstall gnome-power-manager. If you don't know how to chroot, you can use the procedures in my signature link ('chroot'). (Step one is all you need to get into chroot)

Once you have chrooted, "sudo apt-get install --reinstall gnome-power-manager".

---

### Post by Total Noob on 2011-03-26
> **drs305 said:**
> You do not need to reinstall Ubuntu - at least not yet. If in fact there is no more disk space on the drive odd things can happen. It could give a power error one boot and something else on the next. You'd probably only have to delete a few of the .deb files if that was the problem.

Since you are consistently getting the same message about the gnome-power-manager, you might want to concentrate on that. You can use chroot and the LiveCD to reinstall gnome-power-manager. If you don't know how to chroot, you can use the procedures in my signature link ('chroot'). (Step one is all you need to get into chroot)

Once you have chrooted, "sudo apt-get install --reinstall gnome-power-manager".

None of this advice worked well or at all. 

I used a live 10.10 CD to get going, and sure enough did find my drive in Places and tried to access and download my data that way, only to get an insufficient permissions to do anything with it error message.

So next I mounted as you said and tried deleting files, which worked fine, but the next step was to delete them from trash -- useless. Here is the error message. 

```
** (nautilus:4606): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '4606'

(nautilus:4606): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:4606): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

```

This is Greek to me.

Next, I tried Chrooting, and really did not understand the instructions, which are written for a very experienced user, not a Noob like me. Some instructions take for granted that the reader understands such things as changing directories to launch applications and that he knows the procedure to do so without step by step information. Nevertheless, I cut and pasted and substituted sda5 for xya5, and after getting some unusual caret prompts as opposed to the usual $ prompts, I apt-got the power manager, and reinstalled it, and that seemed to work fine. 

But when I rebooted, same problem. GNOME power configuration not installed correctly.

Reboot again with live CD, and try just mounting sda5 with the above code so maybe I have permission to download my data. No luck. SDa5 mounts, but I then can't find it in File Browser or Places. Even searching was futile. My data is in there somewhere, unreachable. 

Ironically, I have full access to my Windows partition even as I have no access to my Linux partition.

I have already given up on this installation. I don't think I can get the Power Manager going even if I can offload my (important) data. But there has to be some way of retrieving my data and getting it onto a disk or something.

---

### Post by drs305 on 2011-03-26
Ok, if "gksu nautilus" isn't working, we can install a nautilus add-on that will allow you to open folders as root.

Boot the LiveCD and mount sda5:
```
sudo mount /dev/sda5 /mnt
```

Next install a nautilus addon:
```
sudo apt-get install nautilus-gksu
nautilus /mnt # Should open to your Ubuntu partition
```
You should be able to navigate to /mnt/home
Find the folder with your username, right click on it, and select "Open as administrator" 
This should open the folder as root and you should be able to do anything you want with those files.

---

### Post by Total Noob on 2011-03-26
> **drs305 said:**
> Ok, if "gksu nautilus" isn't working, we can install a nautilus add-on that will allow you to open folders as root.

Boot the LiveCD and mount sda5:
```
sudo mount /dev/sda5 /mnt
```

Next install a nautilus addon:
```
sudo apt-get install nautilus-gksu
nautilus /mnt # Should open to your Ubuntu partition
```
You should be able to navigate to /mnt/home
Find the folder with your username, right click on it, and select "Open as administrator" 
This should open the folder as root and you should be able to do anything you want with those files.

Thanks, but I just went ahead and installed 10.10 to replace 10.4,and learned my lessons about storing important data on Ubuntu. I didn't have the patience for trial and error of yet more potential fixes all day or for several days.

It seems to me that there is a huge flaw in 10.4 if a user without special powers can crash an installation by doing something seemingly harmless such as filling the partition with data to 99.99 percent. If there is the remotest possibility that doing something not involving fooling around as root will cause system file corruption, then it should not be possible, there should be an internal check on that.

Thanks again for your help.

---

### Post by drs305 on 2011-03-26
Sorry we weren't able to resolve this. Just for clarification, I don't know that the problem was a lack of disk space. It was just something we could correct and I know it was an issue a few releases ago. The package could have become corrupted in some other way.

Best of luck with the new installation.

---

