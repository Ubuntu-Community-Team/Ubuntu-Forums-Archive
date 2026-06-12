---
title: "Boot up woes"
date: 2009-10-18
forum: General Help
---

### Post by Vallaria on 2009-10-18
I installed Ubuntu 9.04. Everything worked fine after the install. Loaded up into it and ran all the updates and installed the proprietary ATI video driver.

I try to reboot and I get two options, same ubuntu generic install and another one that instead of being -11 is -15. I have tried both of these options in grub and all that I get is a shell login screen and no more Gnome Desktop Manager.

Can anyone help me out with this? I am new to Linux and I have just been following the support documentation so far and I couldn't find this anywhere in it.

---

### Post by Vallaria on 2009-10-19
Still nothing : \ all I am getting is a shell login for my computer and no GUI when I boot in.

---

### Post by Johnny B on 2009-10-19
at the shell, remove the ATI driver with the command
> sudo apt-get remove  fglrx
or 
> sudo apt-get remove  xorg-driver-fglrx 

---

### Post by Johnny B on 2009-10-19
try installing the driver with [envy-ng]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Vallaria on 2009-10-19
Nvm just saw your post.

Okay, wrote all that down. Going to go try it now.

---

### Post by Vallaria on 2009-10-19
Okay, I tried both those commands. The second one worked, but still no GUI even after a reboot.

I also noticed that it says "kinit: Attempting to Resume From Image"
"kinit: Failed to resume from image starting normal boot"

---

### Post by Vallaria on 2009-10-19
I read a couple of help files and the only recommendation I am getting is re-install. So I am going to attempt that.

---

### Post by Vallaria on 2009-10-19
Okay, so I am making this post using FF inside Ubuntu 9.04.....I still do not have working 3d drivers. I tried using envy-ng and I had to reinstall Ubuntu again due to the same issue. If I can't get this working I'll probably just re-install XP because this is way over my head in terms of know how to fix.

**EDIT**: I am currently attempting to run the update and then I will try to install the drivers once more after I have updated. If any info is needed on my hardware please ask. I have all of my technical information in a folder beside my computer.

---

### Post by P4man on 2009-10-19
> **Vallaria said:**
> Okay, so I am making this post using FF inside Ubuntu 9.04.....I still do not have working 3d drivers. I tried using envy-ng and I had to reinstall Ubuntu again due to the same issue. If I can't get this working I'll probably just re-install XP because this is way over my head in terms of know how to fix.

**EDIT**: I am currently attempting to run the update and then I will try to install the drivers once more after I have updated. If any info is needed on my hardware please ask. I have all of my technical information in a folder beside my computer.

Im guessing your videocard is not playing nicely with the ATI drivers available in jaunty. Not the first time I heard that :)

You could try downloading the latest ATI drivers from ati website. they provide an (overly extensive) PDF explaining how to install them.

The pdf is here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf)

drivers here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English)

---

### Post by Vallaria on 2009-10-19
Thank you so much for help, both of you <3. Problem solved and ATI driver is working.

/hug

---

### Post by P4man on 2009-10-19
Great. Out of curiousity, which videocard and laptop/pc do you have ?

---

### Post by Vallaria on 2009-10-19
> **P4man said:**
> Great. Out of curiousity, which videocard and laptop/pc do you have ?
I am using [2x ATI Radeon HD Cards](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102815) and I am using a desktop with a AMD Phenom II x4 Processor.

Also, I am now having to work through getting OpenGL to work and it's not play nice either. I think it may have something to do with me using x64 Ubuntu though vs i386. I may have to start from scratch and downgrade to finally find hapiness.

---

### Post by P4man on 2009-10-19
first of all, there is no need for pms. I automatically subscribe to all threads I post in so I already get notified of each new post.

As for opengl, what makes you think its not working? If you installed those drivers, opengl support should be there.

---

### Post by Vallaria on 2009-10-19
> **P4man said:**
> first of all, there is no need for pms. I automatically subscribe to all threads I post in so I already get notified of each new post.

As for opengl, what makes you think its not working? If you installed those drivers, opengl support should be there.
I attempted running Crossover first with no luck on a OpenGL application. Then I tried Wine with no luck, then I DLed a Linux 3d chess app and it didn't work either. I keep getting a error that it cannot open a OpenGL rendering window.

Oddly though I am able to turn on Compiz Fusion to "best" and it works fine.

**EDIT**: Also I am able to run glxgears just fine as well. I posted a support ticket to their site and according to the FAQ I should have a answer in three or so days. In the mean time I will turn to google to see if anyone else is having this issue.

---

### Post by Vallaria on 2009-10-19
**EDIT**: Okay, after searching google and spending time on forums/IRC I finally was directed to this thread.

[http://ubuntuforums.org/showthread.php?t=889659](http://ubuntuforums.org/showthread.php?t=889659)

I will be trying to set this up later today. I really don't know if it will work or not and I don't understand half of the thread, but I'll give it a try when I have plenty of time later today or tomorrow.

I am just unwilling to change my hardware to get Linux working. Considering I built this machine for Windows 7 and trying to get Ubuntu working is just a plus this isn't something that I am going to work on until I get frustrated at my computer over it. Simply not worth it.

If I can get something working with OpenGL and the ATI drivers in the next few tries I'll revisit Linux in a couple more years when it's had more time to develop.

---

### Post by P4man on 2009-10-19
> **Vallaria said:**
> **EDIT**: Okay, after searching google and spending time on forums/IRC I finally was directed to this thread.

[http://ubuntuforums.org/showthread.php?t=889659](http://ubuntuforums.org/showthread.php?t=889659)

I will be trying to set this up later today. 

Dont!
Its not for the right ubuntu version and it doesnt apply to your system. If you did install AMD drivers properly and the ATI catalyst control center is working, then dont touch the drivers. But perhaps confirm those IFs are indeed true.

Instead why not just provide the error messages you get when try to run glxgears or the chess program (run it from a terminal so you get to see the exact errors).

---

