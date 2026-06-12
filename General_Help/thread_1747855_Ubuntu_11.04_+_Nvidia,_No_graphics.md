---
title: "Ubuntu 11.04 + Nvidia, No graphics"
date: 2011-05-03
forum: General Help
---

### Post by sshh on 2011-05-03
If I try normal boot, the screen just freezes for a lot of time, 
does not move, and is black. 

If I try recovery mode, normal boot, then startx I SOMETIMES get a normal screen,
but mostly (like right now) I have no panels, no menu, no headers (the close/minimize/maximize things). 

How can I solve it? Failsafe mode works, but it's depressing to work with
(and the menu does not work, just "applications" is working, but no "Places" or "system").

Any ideas? I'm a HP Pavilion dv9000, ubuntu 11.04, no drivers installed 
(the problems started since I installed one of them. I uninstalled both of them, but no results).

Oh, startx said something about "EE: failed to load module nvidia (does not exist, 0)".

For the logs, this: [http://ubuntuforums.org/showpost.php?p=10750672&postcount=7](http://ubuntuforums.org/showpost.php?p=10750672&postcount=7) is what they
 looked like yesterday. Since nothing changed since then, should be still relevant.

---

### Post by edm1 on 2011-05-03
Im just going to take a guess here to speed things up. I googled your laptop, looks like it has a NVIDIA GeForce Go 7600 graphics card. When you first installed ubuntu did nothing seem to be wrong at first? This was because you were using the open source noveau driver (package 'xserver-xorg-video-nouveau') for your graphics card. Then you installed the proprietary (binary) driver through the Additional Drivers application and it all balls'ed up?

If this is the case I can only recommend uninstalling the binary driver and living with the open source one. It will probably have a lower performance (no 3D) but less problems associated with it.

---

### Post by seawolf167 on 2011-05-03
Here is what I would do:

Go to Nvidia's website and download the drivers for your [graphics card]("http://www.nvidia.com/object/linux-display-ia32-270.41.06-driver.html") (took the model number from edm1's post.
Put the driver on a flash drive, and plug the flash drive into your computer
Enter the first tty console with [CTRL][ALT][F1]
Run the following command
```
sudo service gdm stop
```
You may need to enter
```
top
```
and look for any remaining gdm entries if the installer throws that error.
Next cd to the flash drive directory
```
cd /path/to/flash/drive
```
and run the following commands
```
sudo chmod +x NVID*
./NVID*
```
Then follow the onscreen prompts, when asked, choose to overwrite the current x config file. Once it has finished, reboot and hopefully everything will be good to go

---

### Post by edm1 on 2011-05-03
I just reread your original post. If you decide you do want the noveau driver over the proprietary one. Open synaptic, search 'nvidia', remove all packages installed which begin with nvidia except nvidia-common (as this will remove 'ubuntu-desktop', which i dont actually think would be a problem). Then the following command should reconfigure xorg, unless something has changed over the last couple of releases:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sshh on 2011-05-04
Hello everyone. 
I'm sorry for the late answer. 
edm: It worked, thank you. 
I will live without 3d, but it worked perfectly in 10.10.
I think I will work on it. 
Thank you.

---

### Post by seawolf167 on 2011-05-04
You should be able to get the 3d working by following my previous post and installing the propriety drivers. If you are concerned about breaking the system you can always make an image of your hard drive with Clonezilla.

---

