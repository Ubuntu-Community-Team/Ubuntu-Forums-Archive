---
title: "Ugly UGLY purple bootscreen Ubuntu 10.04"
date: 2010-10-07
forum: General Help
---

### Post by markh789 on 2010-10-07
OK - I took a quick photo sorry for the horrible photography. 

So it's this purple screen with white text - and there is a black strip down the left, and the picture looks very pixelated. 

What's going on? 

> user@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux
user@ubuntu:~$ 


---

### Post by mastablasta on 2010-10-07
looks like you did some partial upgrade of your system.

---

### Post by coffeecat on 2010-10-07
That is not a 9.10 bootscreen - that's from 10.04 or 10.10. Which version are you running?

The black strip down the left (which is not in your screenshot, unless you mean the right)) is probably down to your monitor not tuning in to the graphics card output. Try pressing the 'auto' button.

What graphics card and what driver?

In future, please use the manage attachments utility to upload an image file to get a clickable thumbnail. A huge image like that in a thread is offputting.

---

### Post by markh789 on 2010-10-07
Sorry. Attached that.

My bad - it is 10.04 LTS, and I really dis-like the bootscreen. Is it possible to get the previous one that was much nicer looking.

Edit: GeForce 8500 GT by the way. 
VBIOS Version: 60.86.26.00.00

And you can't see the black strip in the photo, bad photography.

---

### Post by gandaran on 2010-10-07
> **markh789 said:**
> Sorry. Attached that.

My bad - it is 10.04 LTS, and I really dis-like the bootscreen. Is it possible to get the previous one that was much nicer looking.

Edit: GeForce 8500 GT by the way. 
VBIOS Version: 60.86.26.00.00

And you can't see the black strip in the photo, bad photography.
this is easy to correct, install startup-manager, then play around with it until you you find the perfect setting, either try changing the resolution or change the color to 24 bit.

---

### Post by markh789 on 2010-10-07
This community is great, thanks for the help. Here's where I'm at.

> user@ubuntu:~$ sudo startupmanager
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Grub2 detected
Usplash not detected
Splashy not detected
user@ubuntu:~$ sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  usplash: Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme
E: Broken packages
user@ubuntu:~$ 


Broken packages?

---

### Post by coffeecat on 2010-10-07
> **markh789 said:**
> Edit: GeForce 8500 GT by the way. 

You didn't say which driver, but I guess the proprietary nvidia one. This is a well-known issue that the nvidia driver makes the 10.04 Plymouth bootsplash ugly. It's really quite elegant with the open source driver.

There is a workaround if you want to keep this bootsplash but have it displayed the way it's meant to be displayed. If I find the link, I'll post it

---

### Post by philinux on 2010-10-07
> **markh789 said:**
> Sorry. Attached that.

My bad - it is 10.04 LTS, and I really dis-like the bootscreen. Is it possible to get the previous one that was much nicer looking.

Edit: GeForce 8500 GT by the way. 
VBIOS Version: 60.86.26.00.00

And you can't see the black strip in the photo, bad photography.

I've edited the thread title to 10.04.

---

### Post by ean5533 on 2010-10-07
> **markh789 said:**
> Broken packages?

Here's the [installation instructions]("https://help.ubuntu.com/community/StartUpManager#Installation Instructions") for StartUp Manager. I'm assuming the part that you're missing is enabling the universe repository.

The quick and easy way to install it without needing the command line:

Install with Synaptic:
[LIST]
[*]**Open Synaptic**: System > Administration > Synaptic Package Manager.
[*]**Enable the universe repository**: Synaptic, Settings > Repositories > Ubuntu Software. Select Community-maintained Open Source Software (universe).
[*]Press Close and, from the Synaptic menu, Reload.
[*]**Select *startupmanager*** in the right panel, mark for installation, and press Apply.
[/LIST]

---

### Post by NightwishFan on 2010-10-07
Odd, it (almost) isnt possible to install usplash due to dependencies, but the package remains. :/

---

### Post by mastablasta on 2010-10-07
mine doesn't even show, but it does show the shut down screen. sometimes startup screen shows but is garbled. i don't really care... as long as the thing works and brings me to login screen...

---

### Post by Claus7 on 2010-10-07
Hello,

searching the net about plymouth, xsplash and usplash I found out that:

the latter is dropped because of the (xsplash and) plymouth project. This means that the broken packages that you get, and the messages that usplash is not going to be installed are perfectly normal.

I would remove everything that had to do with usplash, reinstall plymouth and see what I can get.

Regards!

---

### Post by amac777 on 2010-10-07
Here's the thread that fixed this Nvidia plymouth issue for  me:

[http://ubuntuforums.org/showthread.php?t=1558174](http://ubuntuforums.org/showthread.php?t=1558174)

Using recluce's post #1 combined with Veedub's post #4 was the solution for me.

---

### Post by markh789 on 2010-10-07
Hey, thanks for all the input.

amac777 - I'm trying your method now, hopefully I don't screw it up.

I've also removed everything usplash. :)

Edit: OK. Here's what happens now (if someone can explain what's going on, please do)
It comes up with the purple screen with the text again (in the middle) flickers black. Then goes back to the purple screen and the text is now in the left corner (very small).

Here's the history of what i've done:
>   493  sudo nano /etc/initramfs-tools/modules
  494  sudo update-initramfs -u
  495  sudo nano /etc/initramfs-tools/modules
  496  sudo hwinfo --framebuffer
  497  sudo apt-get install hwinfo
  498  sudo hwinfo --framebuffer
  499  sudo nano /etc/default/grub
  500  sudo update-grub2
  501  history


My /etc/default/grub file:
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-32@60,mtrr=3,scroll=ywarp"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


My /etc/initramfs-tools/modules file:

> # List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod

uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap


Any ideas?

---

### Post by Joris Donders on 2010-10-08
try  this guidance; it worked for me. 
Note ! write down your native monitor's resolution and use it with all resolution settings you encounter. 

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by markh789 on 2010-10-08
> **Joris Donders said:**
> try  this guidance; it worked for me. 
Note ! write down your native monitor's resolution and use it with all resolution settings you encounter. 

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)


That looks like the fix - thankyou!

---

### Post by Joris Donders on 2010-10-08
no thx, that's what the forum is for !!

---

