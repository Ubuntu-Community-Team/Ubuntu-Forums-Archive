---
title: "HOWTO : Properly install ATI drivers (Fixes Multiple Monitor Issues)"
date: 2011-01-11
forum: General Help
---

### Post by TG12 on 2011-01-11
Hey people! So anyway just a bit of background. I thought I would experiment with Ubuntu. I know my way around a computer a self confessed geek. Graduate Software Engineer, System Admin for 3+ Years anyway to cut a long story short . . . My Macbook screen broke which was my day to day computer, so whilst it was unavailable to me I installed Ubuntu on my Main PC at home, Previously this was just a filestore running windows, Watching BluRays and Videos etc. It was hooked up to a 32" Sony TV. 

I have always enjoyed the concept of the community and what it represents and not to mention the software that it produces. Anyway I borrowed an oldish monitor, It was over £470 when new, Sony 19" job. So it was still very good! I Set up Ubuntu fine. Working fine with it day to day. Set up everything I needed to. Found Windows Alternatives for software and it looked good so far. I was also going to get a new larger monitor anyway for my PC, I wanted to use it for stock trading. I wanted my Sony TV to be a TV and not a monitor that I would have to switch inputs to watch TV.

I went to install the ATI drivers on Ubuntu (The ones from ATI.com), Seemed streight forward enough. I wanted to use the Catalyst Manager. I am running a Radeon HD4650. 

Everytime I kept installing the drivers it kept bombing out to a terminal on boot up! I kept rolling back and trying new things. I gave up trying to use the ATI drivers for a while. I needed to concentrate on other things . . . Share Dealing! :D Worked fine with the built in drivers for now.

Fast forward on a few weeks . . . Got my 24" Samsung monitor. Looks beautiful. I want to get two so I can have the screen real estate for my trading. The plan was to do this all on Linux. 

Anyway I got it all hooked up, I was dual booting with Windows 7. The screen resolution didnt look right. I couldnt get 1080p Resolution to fit the full size of the screen. A quick Google tells me that I have to use the Overscan feature. 5Minutes and DONE. Looks very nice! Shutdown, Boot into Ubuntu . . . Here is where the issues start. I was getting the black lines round the edge of the screen. It was doing my head in. Searching and Searching there seemed to be numerous people having the same problem. Since I didn't have the ATI drivers I couldn't use the CCC as its now called and the Overscan feature. Nothing I did would get me the full screen resolution. I could g*et 1920 x 1080 to be full screen. *I followed allsorts of tutorials, Reconfiguring XWindows, Recreating a new xorg.conf file. Nothing Worked until now.

If you follow these instructions everything else will works and you can get the correct resolution support for your monitor and use the Overscan feature to make it the correct size for your monitor and enjoy 1080p Desktop Glory

> _***Prerequisites***_
Latest drivers from [http://www.amd.com/uk/Pages/AMDHomePage.aspx](http://www.amd.com/uk/Pages/AMDHomePage.aspx)
I used the x_86_64 but I dont see why it wont work just as well with the 32bit drivers.
kernel-headers package (Latest)
gcc (Latest)> All the following commands are run as **root**1) Download latest ATI drivers for your card and package, The Downloads folder is fine.

2) > apt-get update && apt-get upgrade (Make sure you have all the latest package versions)

3) Reboot

4) Open Terminal and change to the directory where you downloaded the drivers

> cd /home/james/Downloads5) Run the GUI Installer for the ATI Drivers. 

> sh ./nameofdriverfile.file 6) Install using the GUI, For 99% of users the defaults should be fine. DO NOT REBOOT at the end of the installation.

7) Back to the Terminal

8) Move to this directory 

> cd /lib/modules/fglrx/build_mod9) Compile the Driver Module 

> sh make.sh10) Move to the outer directory
 
> cd ..11) Install the compiled driver module

> sh make_install.sh12) ***CRUCIAL*** [B]Add nomodeset to kernel row of /boot/grub/grub.cfg file and Save

[/B]13) Reboot

14) You can now use the CCC to set the right resolution and then adjust the Overscan to suit your monitor. Profit! 

Enjoy! 
TG12

---

### Post by franrck on 2011-01-12
thanks, will consider if i buy hd5670

---

### Post by trekki on 2011-01-26
Hi TG12,
thank you for your HOWTO. Maybe you can assist me with your steps. I take this
> **TG12 said:**
> 
All the following commands are run as **root**

to set a "sudo" before each shell command.

But
> **TG12 said:**
> 
2) apt-get update && apt-get upgrade

of cause with sudo before give me this
[IMG]http://i1045.photobucket.com/albums/b459/trekkiOSM/sindsieroot.jpg[/IMG]
Translation of the last error message: Lock of the administation directory (/var/lib/dpkg/) not possible, are you root?

Some google reading only gave me the hint to add sudo before the command to avoid this "are you root" question. Any idea, what happens here?

trekki

---

### Post by TG12 on 2011-01-26
Most likely the package manager has the files locked. You do need to be root to do what I detailed.

---

### Post by trekki on 2011-01-26
Hi TG12,

you are right: "sudo su" gives me a root shell, sudo plus your command is not enough.:P

---

### Post by TG12 on 2011-01-26
If you are "root" then that takes presidency over anything. If you are root then it will be something else locking the package manager files.

---

### Post by Shanttu on 2011-02-08
Thank you for this tutorial. I'm having a problem on step 7. I'm running 10.10 on laptop, Graphics card is ATI mobility radeon 3470. I am desperately trying to get 1920x1080 work on my TV. On Windows it works fine. 

Back to the issue: Happened so far: uninstalled old propietary drivers. Rebooted. Downloaded new drivers. Installed on GUI. Did not reboot. On Terminal I cannot find /lib/modules/fglrx/build_mod 			 		location. On /lib/modules/ section there is only one file: 2.6.35-25-generic-pae. On /lib/fglrx/ i find only modprobe.conf.
Could someone please help go on with this one. It is possible that I find myself feeling stupid (again) because of a simple solution.

---

### Post by cottfcfan on 2011-02-08
I always find this tutorial easy to follow, and always works.

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package).

---

