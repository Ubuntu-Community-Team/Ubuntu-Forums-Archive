---
title: "Ubuntu 10.10 and ATI 6970? Possible?"
date: 2011-02-01
forum: General Help
---

### Post by siberial on 2011-02-01
Hello, I used to use ubuntu a little back in the day but never took enough time to really learn it very well.  I'm trying to reacquaint myself with this OS and am running into a potentially major issue.

I have been reading the forum and googling my *** off so b advised I am not simply posting this question as a first action.

I have downloaded and installed Ubuntu 10.10.

My system uses an ATI RadoenHD 6970 video card.

As you may know this is not supported by the built in driver.  Downloading the ATI driver from the web is useless as well as it does not work.  I have tried sever different installation methods.  I have successfully installed the driver however Catalyst will never successfully launch.  I happened across a similar thread where the respondent simply informed the user that Catalyst is not to be used as it does not function in ubuntu, and to wait for the FOSS Driver.

My question.  Can I "AT THIS MOMENT" install any form of driver so that I might use UBUNTU10.10 at a resolution higher than 1280x1024 considering i have a multi-monitor display both of which can support 1920x1080.

I would simply like to use UBUNTU at a reasonable resolution and "fingers crossed" extend the desktop across two monitors.

Feel free to yell at me for being new. However, I do ask that someone actually clarify this problem and provide the solution.

Thank you.
Sib

---

### Post by TightByte on 2011-04-10
Hello,

I found your post after doing resarch myself, without much success.  Finally, I went to AMD's site and found driver packages to download from there.  I've only just downloaded and installed, so I'll reboot now and update this post with my results.

... and, I'm back.  Well, I got it working, but I had to muck around a fair bit, hand-editing my /etc/X11/xorg.conf file and then running amdccele from within the display I finally got up.

So:  It's possible to get HD 6970 support and, I presume, full accelleration (my AMD Catalys Control Center even let me enable CrossFireX with my two 6970's, but I'm not sure how to test, in Linux, that it really works.)  I wish I could offer some kind of step-by-step procedure to get to setup I've got which finally worked for me, but I probably reached that point in the most non-linear way possible.

Anyways, good luck, and if you've got any questions after giving it a try on your own, post away and I'll try to answer.  Note:  I used the 11.3 version of the driver, found here:  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Cheers

---

### Post by Lordcrash on 2011-04-10
Hi,

I'm a new Linux user myself and was very excited to use this graphics card with Linux(since it made Windows 7 FLY). After trying numerous times to get it working using the FGRLX driver that Ubuntu was trying to install, I went and downloaded this driver

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

After installing this driver, it works perfectly. Hope this helps!!

---

### Post by walidzohair on 2011-06-14
well this is a non sense as the link now is pointing to 11.5 driver not 11.3 and yes I have tried it with every possible way you can google online .. and no luck.. you just do not have a gui after you restart.

using the amd 11.5 driver or the restricted driver from ubuntu or whatever .. it just d not work .. please post any useful information about the xorg.conf if you get back here

---

