---
title: "How to set the timer for the Dual-boot menu?"
date: 2010-07-08
forum: General Help
---

### Post by Abu Azzubair on 2010-07-08
I installed Windows, then Ubuntu, but I don't know how to set the timer for the Dual-boot menu to start at Windows first

On my Laptop, Ubuntu is set to run first and it's set to start after 10 seconds

But I wasn't the one who installed Ubuntu on my Laptop, it was someone else...etc. So I don't really know how to do the thing

I want to set the Dual-boot so that Windows bee's the first one to start loading, at a timer of 1 minute

Could you please help!!!

Thanks in advance O:)

---

### Post by Zip247 on 2010-07-08
All you need to know about grub is located here.  Just make sure you know which version of grub you are using.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by oldfred on 2010-07-09
After you read some of the info on manual setting and understand what you are doing then we will let you do it the easy way:smile::

the quick and easy to make a default boot:
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

### Post by bthomson100 on 2010-07-10
I tried this, installing the Startup Manager, but it still defaults to Windows instead of Ubuntu on startup despite having set it to Ubuntu.

---

### Post by skarme on 2010-07-10
> **Abu Azzubair said:**
> I installed Windows, then Ubuntu, but I don't know how to set the timer for the Dual-boot menu to start at Windows first

On my Laptop, Ubuntu is set to run first and it's set to start after 10 seconds

But I wasn't the one who installed Ubuntu on my Laptop, it was someone else...etc. So I don't really know how to do the thing

I want to set the Dual-boot so that Windows bee's the first one to start loading, at a timer of 1 minute

Could you please help!!!

Thanks in advance O:)
Go to the terminal and type this code
```
 sudo gedit /etc/default/grub

```
Set GRUB_DEFAULT=x, where 'x' is the desired OS i.e Windows in your case. If for example windows is the 6th option in the GRUB menu, then set x=5 i.e 6-1. This is because the 1st position in the GRUB menu is taken as 0.
You can set the timer to 1 minute by changing GRUB_TIMEOUT=10 to GRUB_TIMEOUT=60.
Once this is done, save the file and close it.
Get back to the terminal and type
```
sudo update-grub
```
This should do it.
Restart and check it out.

---

### Post by bthomson100 on 2010-07-10
> **skarme said:**
> Go to the terminal and type this code
```
 sudo gedit /etc/default/grub

```Set GRUB_DEFAULT=x, where 'x' is the desired OS i.e Windows in your case. If for example windows is the 6th option in the GRUB menu

But where is the GRUB menu? This is the contents of my grub file but there is no mention of Windows or the word "Ubuntu" which would indicate a menu choice!

=================
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=792"

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

=============================

---

### Post by oldfred on 2010-07-10
Startup manager should have let you reset it.

If you want the manual way:

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by skarme on 2010-07-11
> **bthomson100 said:**
> But where is the GRUB menu? This is the contents of my grub file but there is no mention of Windows or the word "Ubuntu" which would indicate a menu choice!

=================
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=792"

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

=============================
GRUB Menu is the GRUB display at startup, where the Operating Systems are listed.
To change the timer to one minute, simply set GRUB_TIMEOUT=60.
See this Image [http://www.davestechsupport.com/blog/images/grub.png](http://www.davestechsupport.com/blog/images/grub.png)
Here Windows XP is the 5th option, so we set x=5-1=4 i.e GRUB_DEFAULT=4.
Check which option Windows is in your GRUB menu.Once you're done with this, don't forget to save and run sudo grub-update, else the changes won't take effect.

---

### Post by hansdown on 2010-07-11
hi bthomson100.

Are you using a wubi install?

---

### Post by Abu Azzubair on 2010-07-11
First of all I really do apologize for my daftness Lol

I forgot to set this Thread to instantly let me receive an email when anyone posts Lol

________

As for your post on that thread, I'm reading on "grub" and to be honest this is the first time that I know that the Dual-boot menu is called "grub"...etc

So my question is:

Do I not have grub installed on my laptop/computer that has Linux Ubuntu?

Because when I tried to put some terminal commands they never worked for some reason :(

So I assumed that grub is already installed in my laptop that has Linux Ubuntu

---

### Post by oldfred on 2010-07-11
If you have wubi it boots to the windows boot loader that gives a choice for windows or Ubuntu. Then with Ubuntu you get a grub menu even though it is not really using grub to boot.

With install to partitions you have grub in the MBR of the boot drive and it will give you a choice of Ubuntu or windows.

---

### Post by skarme on 2010-07-11
> **Abu Azzubair said:**
> So my question is:

Do I not have grub installed on my laptop/computer that has Linux Ubuntu?

Because when I tried to put some terminal commands they never worked for some reason :(

So I assumed that grub is already installed in my laptop that has Linux Ubuntu

Yes, you do have GRUB installed on your PC. GRUB helps you boot into the desired operating system. 
Were you able to set your timer and choose Windows as your default Operating system?

---

