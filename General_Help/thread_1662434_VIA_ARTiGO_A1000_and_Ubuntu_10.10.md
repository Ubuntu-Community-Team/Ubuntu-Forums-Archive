---
title: "VIA ARTiGO A1000 and Ubuntu 10.10"
date: 2011-01-08
forum: General Help
---

### Post by sanju83 on 2011-01-08
Hi everyone,

I was wondering if anyone else either has or had the same problem as me. i want to get ubuntu netbook working correctly on the artigo a1000. fortunately i am able to install easily with little fuss. My only problem, so far, is that the keyboard and mouse input is so choppy and bad that it renders it useless. i have tried all sorts of lightweight Linux distros and they all do the same thing, poor mouse and keyboard response. i then concluded it was a driver issue because win 7 didn't have than issue, win 7 just lagged because it is to heavy, but ran 1000 times better than any Linux. anyways back on the topic. so i found this article ([http://stevehanov.ca/blog/index.php?id=29](http://stevehanov.ca/blog/index.php?id=29)) talking about openchrome not working well and using the via drivers. i went to via's website to look for them and they were pulled off, not supported anymore. i then went and looked for a step by step to install new or updated drivers for the artigo for any Linux distro, didnt find anything. i found some step by step to configure the old drivers but only for old ubuntu distro and who wants that. so my question is how to i easily configure Ubuntu to play nice with the artigo, in the least amount of steps possible for any linux OS?

Thanks in advance.

---

### Post by Samloops on 2011-01-25
I'm in the process of getting an A1100 (not one of the A1000's) up and running now.  After several tries, I have successfully gotten it into a usable state by:

1) installing the 10.04 32-bit Desktop (alternate install CD) using a portable CD unit.  The Artigo initially was booting off of a USB stick just fine but stopped doing that after a while.  No amount of BIOS boot order tweaking seems to resolve the issue.  Maybe it's the stick.  Anyway, I had to use the alternative install CD since a Live CD caused the screen to get scrambled once past the 5 Ubuntu dots.

2) Once that installed, I mounted the USB stick on which I had placed the uncompressed Ubuntu 10.04 VIA drivers.  There seem to be two versions of the Ubuntu 10.04 drivers on their website.  The one I found to work is on their Linux Portal site at [http://linux.via.com.tw](http://linux.via.com.tw) .  Ubuntu 10.04 is the latest version listed.  I also specified the VX855 platform / chipset.  That chipset may be different on the A1000, but they list several. 

3) I installed the driver using sudo ./vinstall and then restarted X with sudo service gdm restart.  Et voila!  Success.  Video acceleration seems to be working without any tweaking.

I haven't tried any audio yet or video...  also, I'll try moving to the 64-bit version of 10.10.  Let you know what happens.

I looked on the Linux Portal for the VX700 chipset drivers, the chipset that I believe is used on your A1000.  You are correct that they have none listed for that chipset for Ubuntu 10.04.  They do have a driver listed for Ubuntu 9.4 however.  Maybe you should start by installing 9.4, and use that VIA driver.  That should at least get things up and running.  Then you can update Ubuntu and see if anything breaks.  I haven't encountered any of the mouse/keyboard problems you mention.  Maybe I just don't type as fast as you.

Good luck!  It's a nice little device that deserves a little effort.

Sam Longiaru
Kamloops, BC

---

### Post by Samloops on 2011-01-25
I'm in the process of getting an A1100 (not one of the A1000's) up and running now.  After several tries, I have successfully gotten it into a usable state by:

1) installing the 10.04 32-bit Desktop (alternate install CD) using a portable CD unit.  The Artigo initially was booting off of a USB stick just fine but stopped doing that after a while.  No amount of BIOS boot order tweaking seems to resolve the issue.  Maybe it's the stick.  Anyway, I had to use the alternative install CD since a Live CD caused the screen to get scrambled once past the 5 Ubuntu dots.

2) Once that installed, I mounted the USB stick on which I had placed the uncompressed Ubuntu 10.04 VIA drivers.  There seem to be two versions of the Ubuntu 10.04 drivers on their website.  The one I found to work is on their Linux Portal site at [http://linux.via.com.tw](http://linux.via.com.tw) .  Ubuntu 10.04 is the latest version listed.  I also specified the VX855 platform / chipset.  That chipset may be different on the A1000, but they list several. 

3) I installed the driver using sudo ./install and then restarted X with sudo service gdm restart.  Et voila!  Success.  Video acceleration seems to be working without any tweaking.

I haven't tried any audio yet or video...  also, I'll try moving to the 64-bit version of 10.10.  Let you know what happens.

I looked on the Linux Portal for the VX700 chipset drivers, the chipset that I believe is used on your A1000.  You are correct that they have none listed for that chipset for Ubuntu 10.04.  They do have a driver listed for Ubuntu 9.4 however.  Maybe you should start by installing 9.4, and use that VIA driver.  That should at least get things up and running.  Then you can update Ubuntu and see if anything breaks.  I haven't encountered any of the mouse/keyboard problems you mention.  Maybe I just don't type as fast as you.

Good luck!  It's a nice little device that deserves a little effort.

Sam Longiaru
Kamloops, BC

---

### Post by Samloops on 2011-01-26
Hmmm... not sure why that last post appeared twice...

Anyway, no, the VIA driver throws an error and will not load when using the 64-bit version of Ubuntu 10.04.  Specifically, the error is:

dlopen: /usr/lib/xorg/modules/drivers/via_drv.so : wrong ELF class : ELFCLASS32
Failed to load /usr/lib/xorg/modules/via_drv.so
Unload module "via"
Failed to load module "via" (loader failed, 7)

Rolling back to 32 bit and the VIA driver which works well.

Sam Longiaru
Kamloops, BC

---

### Post by sbird on 2011-02-13
[sanju83]("http://ubuntuforums.org/member.php?u=1220133") -

   I had 10.10 successfully installed on my A1000 using VGA.  Wanted to switch to DVI for monitor.  Boots fine until GUI loads then video tearing like wrong refresh rate and/or resolution.

   Finally, decided to try fresh install of 10.10 from CD to see if it would detect monitor correctly.  No luck.  As soon as the 10.10 installer launches the GUI, the monitor starts tearing.

  How were you able to install 10.10 on the A1000?  

  I have the BIOS set to enable DVI.  I don't think the panel type setting makes any difference.  Did you change any other BIOS settings?

  Thanks for any help-
     Bob

---

### Post by Samloops on 2011-02-14
Hi Bob,

Just to make it clear, I installed on an A1100, but what you describe is exactly what I was experiencing on my first attempt to install Ubuntu.  Try the "alternate install" version of Ubuntu 10.10.  It is a text-based installer.  Once Ubuntu is installed and you get to a prompt you should be able to login, then sudo cd /etc/X11 and copy xorg.conf.failsafe to xorg.conf .  Then reboot.  Failsafe is just a barebones config file that specifies the vesa driver and so nothing real fancy, but it should get you a full GUI.

Sam

---

### Post by sbird on 2011-02-19
Sam -

  Got it working! Thanks for your help.  Generated a new xorg.conf and all is working fine with DVI.  I wasn't able to get 1920x1080 to work.  X kept complaining about supporting the size requested even though it works fine at 1920x1080 with VGA.  I generated and tried and bunch of modelines with no luck.  Running now on a smaller monitor at 1280x1024.

  Using it as a digital picture frame so good resolution was a requirement.

Thanks again for your help-
Bob

---

