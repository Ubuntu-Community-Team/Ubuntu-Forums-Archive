---
title: "From Windows to Ubuntu"
date: 2010-12-12
forum: General Help
---

### Post by Smile88 on 2010-12-12
Hi,

I have always been a Windows user, but have recently start checking out other operating systems. I've been reading a lot about Linux lately and I really think moving to Linux on my laptop is something for me. 

It seems like a safe hassle-free flexibel operating system to me. But what particularly interests me, is the option to have it to be lightweight and minimalistic. This has always appealed to me.

So, after some research I found Ubuntu + Fluxbox would seem to suit me. 

The only (big) problem is I don't really have any programming skills. I'm a complete beginner. :oops:
Do you think moving to this would be too big of a step for me? Or should I really try out one of the most popular desktop environments. 

Another problem is, I don't have an optical disk drive, and would have to install it through USB. Do you think I could just use this site and follow the steps?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Mark Phelps on 2010-12-12
Laptops pose special challenges for all Linux distros because of the frequency of customized hardware and the drivers needed for those components.

Your best bet would be to try out whatever distro you want -- BEFORE you install it on your laptop.  That's really the only way you'll be able to tell if a particular distro will work with your specific laptop.

That's normally done in Ubuntu using the LiveCD mode -- but since you have only USB, you'd have to convert that to USB mode and I don't know how you'd do that.

Also, laptops that come preinstalled with Windows 7 (which most do these days), all too often have the full set of 4 primary partitions already configured on the hard drive.  That makes installing a second OS a LOT harder.

---

### Post by Smile88 on 2010-12-12
Damn. I do have Windows 7. My laptop is the Lenovo Thinkpad X201i. 

Thanks for your response. I'll try the LiveCD mode, if anyone has any suggestions how to create a USB version with that.

---

### Post by Purplerob on 2010-12-12
Look here:
[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Numbers 2 and 3 are what you want.

---

### Post by rickyrockrat on 2010-12-12
Smile88,
You don't have to be a programmer anymore. I put an 86 year old man with no computer experience at all on Linux. The biggest issue you will find is:
1) Making sure Linux works on the hardware, and only buying hardware Linux works on.
2) Forgetting Windows nuttyness

You might also like xfce4. It it very lightweight yet still quite nice.

Welcome!

---

### Post by rickyrockrat on 2010-12-12
Here are some folks running Linux on your laptop:
[http://www.thinkwiki.org/wiki/Installing_Debian_5.0_%28Lenny%29_on_a_ThinkPad_X201i](http://www.thinkwiki.org/wiki/Installing_Debian_5.0_%28Lenny%29_on_a_ThinkPad_X201i)
[http://www.thinkwiki.org/wiki/Installing_Fedora_13_on_a_ThinkPad_X201i](http://www.thinkwiki.org/wiki/Installing_Fedora_13_on_a_ThinkPad_X201i)
[http://ubuntuforums.org/showthread.php?t=1571920](http://ubuntuforums.org/showthread.php?t=1571920)

If it runs on one Linux distro, chances are it will run on Ubuntu.

---

### Post by Smile88 on 2010-12-12
> **Purplerob said:**
> Look here:
[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Numbers 2 and 3 are what you want.

Thanks. I will use this.:p

> **rickyrockrat said:**
> Smile88,
You don't have to be a programmer anymore. I put an 86 year old man with no computer experience at all on Linux. The biggest issue you will find is:
1) Making sure Linux works on the hardware, and only buying hardware Linux works on.
2) Forgetting Windows nuttyness

You might also like xfce4. It it very lightweight yet still quite nice.

Welcome!

Hmm. Well, if it works with my sound cards and stuff like that I think I'll be ok. I've got some logitech speakers and HP printer, but I've read Linux users with the same products, which would mean it can work. Knowing how to set it up, is a different story. :P 

I've thought about Xfce, but I like the idea of starting with few applications, to start from scratch sort of speak. And just a windows manager (with keyboard shortcuts to applications though) I hope I'll be able to figure that out. Or do you think it'll be too complicated for the inexperienced user?> **rickyrockrat said:**
> Here are some folks running Linux on your laptop:
[http://www.thinkwiki.org/wiki/Installing_Debian_5.0_%28Lenny%29_on_a_ThinkPad_X201i](http://www.thinkwiki.org/wiki/Installing_Debian_5.0_%28Lenny%29_on_a_ThinkPad_X201i)
[http://www.thinkwiki.org/wiki/Installing_Fedora_13_on_a_ThinkPad_X201i](http://www.thinkwiki.org/wiki/Installing_Fedora_13_on_a_ThinkPad_X201i)
[http://ubuntuforums.org/showthread.php?t=1571920](http://ubuntuforums.org/showthread.php?t=1571920)

If it runs on one Linux distro, chances are it will run on Ubuntu.

Yes! Good news, thanks.

---

### Post by rickyrockrat on 2010-12-12
If you have never used Linux before, I'm afraid you are going to be bewildered with a minimal system, but if you're brave, you'll make it.

Your HP printer is almost certainly supported, since HP is one of the few companies actively supporting Linux. Look for hplip in the repositories (apt-cache search hplip)

Use hp-info from that package, and you'll be golden. Make sure cups is installed.

One of the things to remember is very few folks install windows themselves, so when they try to install Linux and get frustrated, I challenge them to do the same thing with Windows.

I think the biggest thing in Linux is how it handles disk drives. There's no C: D: E: etc, there's just root (/) and everything is mounted there.  Windows mounts drives too - they just show up as C: instead of some place on the directory tree.  

If you use Thunderbird, Firefox, and Open Office in Windows, then going to Linux is easy since those programs when installed on Windows will extract the settings from their Windows counterpart.

---

### Post by Smile88 on 2010-12-29
Ok. Going start doing this. I suppose I'd have to back up my files, the first step? I'd like to keep my music/some documents.

---

### Post by Bucky Ball on 2010-12-29
What is on the hard drive at the moment and what do you want on there? You need to get out the pen and paper and make a plan at this point but I totally relate to where you're coming from as it was me in 2007. I really haven't looked back. Was a power Windows user but this is the life for me!

It can sometimes take a bit of tweaking to get things up but I think you will be fine (HP are well supported also). Thing is, once the machine is up, it is generally going to stay that way until you screw with things. No unexpected blue screens of death! Leave the machine on for hours, days, weeks, without restarts. 

Welcome and enjoy the learning curve. ;)

You are going to need some free disk space. You can dual-boot with Windows or just use the current Windows partition and leave your data partitions where they are (backup always wise of course). There are plenty of sites for help and theres always this forum (and others).

Just remember: Post separate threads for separate issues. You will get better help that way. :)

Partitions:

/ = root partition: OS
/home = your stuff
/swap = swap partition

You can add any other partitions you like to this. Always a good idea to keep /home on a separate partition. If you let the installer use all free space this won't be the case. Manual partition when you get to that bit; you'll see any used partitions you have and then you can leave them alone if you wish.

Good luck with it.

---

### Post by Jerry N on 2010-12-29
> **rickyrockrat said:**
> One of the things to remember is very few folks install windows themselves, so when they try to install Linux and get frustrated, I challenge them to do the same thing with Windows.

I accept the challenge but I don't know why you think that installing Windows is some sort of a big deal.  I build my own desktop computers and installing Windows is not one bit more difficult than installing Ubuntu or Mint (some Linux distributions are quite a bit more challenging).  Of course you shouldn't start out by throwing away the motherboard and video board support CDs :p:p .  But with Win 7 you don't even need those!

For a new user, I would suggest starting out with plain vanilla Ubuntu or Mint and then move to something more minimalist after developing some experience with Linux.   

Jerry

---

### Post by Smile88 on 2010-12-30
> **Bucky Ball said:**
> What is on the hard drive at the moment and what do you want on there? You need to get out the pen and paper and make a plan at this point but I totally relate to where you're coming from as it was me in 2007. I really haven't looked back. Was a power Windows user but this is the life for me!

It can sometimes take a bit of tweaking to get things up but I think you will be fine (HP are well supported also). Thing is, once the machine is up, it is generally going to stay that way until you screw with things. No unexpected blue screens of death! Leave the machine on for hours, days, weeks, without restarts. 

Welcome and enjoy the learning curve. ;)

You are going to need some free disk space. You can dual-boot with Windows or just use the current Windows partition and leave your data partitions where they are (backup always wise of course). There are plenty of sites for help and theres always this forum (and others).

Just remember: Post separate threads for separate issues. You will get better help that way. :)

Partitions:

/ = root partition: OS
/home = your stuff
/swap = swap partition

You can add any other partitions you like to this. Always a good idea to keep /home on a separate partition. If you let the installer use all free space this won't be the case. Manual partition when you get to that bit; you'll see any used partitions you have and then you can leave them alone if you wish.

Good luck with it.



Thanks for the tips. 

I've just got some documents I need to save, so PDF and DOC files. So I could make a back up for this, on a stick. Then eh, uninstall Windows. Then use the USB to boot the Ubuntu installer? Or is this a stupid suggestion?

---

### Post by Smile88 on 2010-12-31
I just tried the Ubuntu USB Installer, to try Ubuntu from the stick and really liked it. I suppose it was Gnome, considering the desktop and the applications? Is that the standard desktop environment it installs? 

My internet worked. :p  I'll try xubuntu.

---

### Post by Bucky Ball on 2011-01-01
Yes, Gnome for Ubuntu. Different for Xubuntu - xfce (thus the X in Xubuntu).

Sounds like you're ready to roll. 10.04 LTS is the current long term support release ('til April 2013), one year longer than 10.10 and more stable.

---

### Post by Smile88 on 2011-01-02
Deleted Windows and installed Xubuntu. Couldn't be happier. It's a lot easier than I had realised. I'm really glad I switched.

I even installed stuff through the terminal. Man, that was scary. This rocks.

Two problems though, which I haven't been able to figure out.

1. How do I access my USB headset, since it won't pick up on it automatically?

2. Flash support for Iron. I got it working for Firefox. On the Adobe site it says:

> 
If you are using the open source Chromium browser, please download and install the Flash Player plug-in below.

So I did. Downloaded the ".deb for Ubuntu 8.04+" At which I get an error saying:

Error: Conflicts with the installed package 'flashplugin-installer'

Any ideas?

---

### Post by rburkartjo on 2011-01-02
smile just have fun there is a learning curve but there is a lot of help available here. i havent used windows for over 4 years. i did though just install window7 on a separate hard drive on my computer.
7 is okay better than vista but imoo ubuntu is much better. on a new install it was amazing of the addware that came installed. i had to user sybot and spyware blaster to disable. enjoy

---

### Post by Bucky Ball on 2011-01-02
Easiest way to install anything is through Synaptic Package Manager (in  Xubuntu Applications->System from memory ... not on my other machine  at mo). Try there first before downloading debs. You  should find xubuntu-restricted-extras in there and that will install  flash for you. :) The deb your trying to install is for 8.04 and you are using 10.04 (I think). Try this link if the above fails. It basically does the same as what I've described:

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29")

USB headset: run this in a terminal with the headset plugged in:

lsusb

Is it there? The machine should pick it up no prob but if not we need to work on that before getting it working.

Great you got things working. Enjoy the new OS and the learning curve. ;)

---

### Post by Smile88 on 2011-01-03
> **Bucky Ball said:**
> Easiest way to install anything is through Synaptic Package Manager (in  Xubuntu Applications->System from memory ... not on my other machine  at mo). Try there first before downloading debs. You  should find xubuntu-restricted-extras in there and that will install  flash for you. :) The deb your trying to install is for 8.04 and you are using 10.04 (I think). Try this link if the above fails. It basically does the same as what I've described:

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS%20%28Lucid%20Lynx%29%20and%209.10%20%28Karmic%20Koala%29")


Ok. Well it said 8.04+, so I thought that meant 8.04 versions and up. :P I found it. Thanks!

> 
USB headset: run this in a terminal with the headset plugged in:

lsusb

Is it there? The machine should pick it up no prob but if not we need to work on that before getting it working.

Great you got things working. Enjoy the new OS and the learning curve. ;)

I ran lsusb. It said: 

Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:0a0c Logitech, Inc. 
Bus 001 Device 004: ID 17ef:4816 Lenovo 
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Cool. It's a Logitech headset, so I suppose it found it. How do I get it to work? :P


@rburkartjo. It is a steep learning curve. But trying to figure things out though. It's kind of fun. Still getting used to things though. I love this Pidgin messenger. It's quite amazing. But still questions though. Like is it possible to get other fonts for Pidgin? Verdana etc.. are microsoft fonts aren't they?

Downloaded VLC. Now trying to replace Foobar. I tried Audacious and Aqualung. It's really difficult to add things to this, especially in Aqualung. Audacious has more support, I suppose? I'll stick to that, if I can get a gapless playing plugin. Which means more figuring out..

---

### Post by mastablasta on 2011-01-03
> **Smile88 said:**
> Deleted Windows and installed Xubuntu. Couldn't be happier. It's a lot easier than I had realised. I'm really glad I switched.
 

 
once you get settled in you might give Kubuntu a try (it's sort of a bling bling version that has more similar look to windows), Lubuntu uses LXDE (very lightweight environment even lighter than XFCE, uses only about 80MB ram and can work on as low as 128MB, though a bit slower).
 
And since you want minimalistic - there is always that minimum install cd and you build from there on (as long as you figure out what you need - which drivers and such).
 
i use GNOME as it has good software support.

---

### Post by ekjsim on 2011-01-03
So which is the best distro? Or rather what are the characteristic of each distro?

---

### Post by Bucky Ball on 2011-01-03
Try 'em out:

[https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html](https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html)

Just uninstall again if you don't like. After install, log out, at the log in screen hit 'Sessions' and the installed desktop environment will be there. Choose it, log in and you're there!

Xfce is zippy and though not enough bells and whistles for some users, you can add as many as you like to the basic desktop. 

Remember; you will have access to the SAME apps as you have now in Ubuntu (plus a few others) regardless of what desktop environment you boot into. ;)

---

### Post by Smile88 on 2011-01-03
Is there any way to connect to a specific wireless network automatically the moment Xubuntu is loaded?

I have to manually click it, everytime I restart.

---

### Post by Bucky Ball on 2011-01-03
Yep, you should be able to set that up in Applications->System->Network from memory or right click the network icon and 'Edit Connections', also from memory as not at the Xubuntu box at the mo. 

Do you mean you need to input the details of your AP everytime (Access point/router)?

---

### Post by perspectoff on 2011-01-03
> **Smile88 said:**
> Damn. I do have Windows 7. My laptop is the Lenovo Thinkpad X201i. 

Thanks for your response. I'll try the LiveCD mode, if anyone has any suggestions how to create a USB version with that.

I have Kubuntu on 3 Lenovo Thinkpads at work. No problems.

A clean interface is what you make of it. Kubuntu is much cleaner than Ubuntu IMO (and functions more like Windows), but it is all a matter of personal taste. 

I have both Ubuntu and Kubuntu on my personal laptop but only use Kubuntu.

I have never found a good reason to move to Mint or Fluxbox or other fork. I tried Xubuntu but found no advantage over Ubuntu. (I prefer the Ubuntu-fork PuppyLinux for resource-limited computers anyway.)

Ubuntu Studio is perhaps the only exception (for audiovideo-philes), since they have lots of customization for AV production already organised.

But to try a smaller fork for a few desktop tweaks is silly, IMO.

---

### Post by Smile88 on 2011-01-04
I heard Kubuntu would be slower, with more 'bells and whistles' sort of thing. But I'll sure check it out, once I get settled.

> **Bucky Ball said:**
> Yep, you should be able to set that up in Applications->System->Network from memory or right click the network icon and 'Edit Connections', also from memory as not at the Xubuntu box at the mo. 


Thanks, I've found it.

Do you know how I can get my headset working? 

I ran lsusb. It said: 

Bus 002 Device 002: ID 8087:0020 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:0a0c Logitech, Inc. 
Bus 001 Device 004: ID 17ef:4816 Lenovo 
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. 
Bus 001 Device 002: ID 8087:0020 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So that means it found my (logitech) headset right? How do I make it work?

---

### Post by Bucky Ball on 2011-01-04
You should really post a new thread about this new problem with an appropriate, descriptive thread title. You will get more specific help, more heads on the job. People won't find it this deep in this thread. Post a link back here and I'll take a look. ;)

---

