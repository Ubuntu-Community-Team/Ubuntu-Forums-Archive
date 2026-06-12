---
title: "Enabling NVIDA drivers causes bootup splash screen corruption (10.04)"
date: 2012-01-15
forum: General Help
---

### Post by StewartM on 2012-01-15
Hi,

On my 10.04 desktop, with a fresh install almost 2 years ago, I got the Nouveau drivers. I held off re-enabling the NVIDIA driver (Geforce 8600 GT) as the Nouveau driver had slightly better 2-D rendering, I hoped that Nouveau would eventually have 3-D capability (it's in the works) and finally a bug in jockey made the switch doable but non-trivial. 

Well, I finally tried re-enabling the NVIDIA driver, and it worked. Except that I got the huge fuzzy low-resolution "Ubuntu" icon at the bootup splash screen. "Not a problem, I thought, I'll just install StartupManager and up the resolution back to my screen capability (1280 x 1024)".

And it did up the screen resolution. But then I lost the Ubuntu logo and got a Times New Roman - like "Ubuntu 10.04" splash screen without the Ubuntu logo. I tried various things, like lowering the resolution back to 640 x 480. Didn't work. Removing Startupmanager didn't work. Going back to the Nouveau manager *does* work. But then if I re-enable the NVIDIA driver it goes back to ugly.

I've googled this problem, and I found threads like these:

[http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen](http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen)

And implemented both of the following:

> 
sudo apt-get install v86d hwinfo
sudo hwinfo --framebuffer

This will show you your supported resolutions. Take note.

Then:

gksudo gedit /etc/default/grub

Search for - GRUB_GFXMODE=

below this you need to type: GRUB_GFXPAYLOAD_LINUX=1024x768 <- your-resolution-here

Save the file and then:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub2
sudo update-initramfs -u

And

> 
The above solution might not work for you. In my case e.g. hwinfo doesn't show the supported resolutions. You can, however, get this information directly from grub.

Press c to get in the grub console and then enter vbeinfo to get the supported resolutions. If you native resolution is supported, use it. And use it directly as shown (i.e. 1680x1050x32, so include the colordepth). Get back by pressing ESC.

When you have the supported resolution edit /etc/default/grub and edit part of the file to look like this:

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1680x1050x32

Now run the following lines to make the splash show earlier and to actually commit the changes to grub.

echo "FRAMEBUFFER=y" | sudo tee -a /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
sudo update-grub

Hope this helps.

And I still get ugliness.

Googling futher, I find this:

[https://paolobernardi.wordpress.com/2010/11/07/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers/](https://paolobernardi.wordpress.com/2010/11/07/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers/)

Which calls for you to install a script.

And...

[http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown](http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown)

Which calls for the following modifications:

> 
Step 1: First, open up a terminal window from Applications -> Accessories menu. Run this command to install preparing tools:

sudo apt-get install v86d hwinfo

Then, use following command to get a list of supported screen resolution modes (800×600 16bits, 1280×1024 24bits 1024×768 16bits, etc&#8230;).

sudo hwinfo --framebuffer

Step 2: Now, let&#8217;s start editing the /etc/default/grub file:

sudo gedit /etc/default/grub

Find following section and change it looks like this:

    GRUB_DEFAULT=0
    GRUB_HIDDEN_TIMEOUT=0
    GRUB_HIDDEN_TIMEOUT_QUIET=true
    GRUB_TIMEOUT=10
    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap&#8221;
    GRUB_CMDLINE_LINUX=&#8221;&#8221;

    # The resolution used on graphical terminal
    # note that you can use only modes which your graphic card supports via VBE
    # you can see them in real GRUB with the command `vbeinfo&#8217;
    #GRUB_GFXMODE=1280×1024

Here, change 1280×1024-24 (1280*1024 24bits) to yours screen resolution and it must be listed in the output of sudo hwinfo --framebuffer

Step 3: Run this command:

sudo gedit /etc/initramfs-tools/modules

Add following line into the end and save it.

uvesafb mode_option=1280×1024-24 mtrr=3 scroll=ywrap

remember to replace 1280×1024-24

Step 4:Finally, execute following commands and then restart your machine.

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub2
sudo update-initramfs -u 


Which I think is probably highlighting the issue. Here's my /etc/default/grub file, and where I marked in RED I think is the problem.


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=769"[/COLOR]

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1280x1024x8

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

 
But I don't want to go messing around with grub's setting without asking here first. Which course would anyone recommend?

StewartM

---

### Post by Bobhuber on 2012-01-15
This page usually takes forever to load but the original instuctions all came from here and have worked for me on every version of ubuntu I've loaded. I still use it not for the splash screen but higher resolution in a virtual terminal.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by StewartM on 2012-01-16
> **Bobhuber said:**
> This page usually takes forever to load but the original instuctions all came from here and have worked for me on every version of ubuntu I've loaded. I still use it not for the splash screen but higher resolution in a virtual terminal.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Thanks! Worked like a charm this morning. I'll mark this thread as "SOLVED" to help others.:)

StewartM

---

