---
title: "Installing ATI driver Ubuntu 9.10"
date: 2010-10-10
forum: General Help
---

### Post by Aardappelschijfje on 2010-10-10
Dear users,

When I go to "Hardware Drivers" and let it install my graphic drivers automatically, my Ubuntu doesn't start anymore and the screen goes black after rebooting.

On the internet I have looked for some other drivers, but the drivers which I downloaded also didn't work. I got the error "vcdk is missing".

My videocard:** ATI Mobility Radeon HD 3470.**

Does anyone have an idea to get my graphics fixed? You should know that I am completely new to Linux; I just learned today how to open a terminal.

I thank you in advance.

Kind regards,
Aardappelschijfje

---

### Post by rapiertg on 2010-10-10
Can you boot your system in recovery?

Hold shift during boot and choose option with (recovery). Menu will show up after a moment. Then choose safe mode in the menu.

---

### Post by Aardappelschijfje on 2010-10-10
> **rapiertg said:**
> Can you boot your system in recovery?

Hold shift during boot and choose option with (recovery). Menu will show up after a moment. Then choose safe mode in the menu.

Yes, I can do this.

I must add that I have re-installed Ubuntu and tried to install the driver with EnvyNG. Unfortunately, I have the same problem now (thus Ubuntu doesn't start anymore).

---

### Post by rapiertg on 2010-10-11
Is it stucked? Can you change to another tty (CTRL+ALT+F1)? And paste log from:
/var/log/Xorg.0.log

---

### Post by Aardappelschijfje on 2010-10-11
> **rapiertg said:**
> Is it stucked? Can you change to another tty (CTRL+ALT+F1)? And paste log from:
/var/log/Xorg.0.log

At the moment I am in the recovery meny, and I can select several options (like root, restart, etc)

When I press CTRL + ALT + F1, I get nothing.

---

### Post by QIII on 2010-10-11
In the "Similar to Vogon building notices that are available but buried in a locked vault" category...

A documented requirement that you probably did not ever run across is this:

To initialize your ATI driver, you must issue the following in the terminal

```
sudo aticonfig --initial -f
```

---

### Post by Aardappelschijfje on 2010-10-11
> **QIII said:**
> In the "Similar to Vogon building notices that are available but buried in a locked vault" category...

A documented requirement that you probably did not ever run across is this:

To initialize your ATI driver, you must issue the following in the terminal

```
sudo aticonfig --initial -f
```

Thank you very much for your reply!

I just re-installed Ubuntu again, so there are no drivers installed anymore.

Do I have to install the driver from the automatic hardware updater and then type the above command?

I am sorry for being such a newbie and I thank you for your patience :)

---

### Post by QIII on 2010-10-11
Install the driver.  On one of your panels, you should have an icon that looks like a PCB.  Or, your can go to Hardware.

Install the offered ATI driver.

When that is done, immediately use the command in the terminal.

The driver will not be activated until your next reboot.

---

### Post by Aardappelschijfje on 2010-10-11
> **QIII said:**
> Install the driver.  On one of your panels, you should have an icon that looks like a PCB.  Or, your can go to Hardware.

Install the offered ATI driver.

When that is done, immediately use the command in the terminal.

The driver will not be activated until your next reboot.

I am now downloading and installing the ATI driver from the Hardware Driver section. After that's done, I will immediately type that command and reboot.

I will let you know how it went. Thank you!

---

### Post by Aardappelschijfje on 2010-10-11
> **QIII said:**
> Install the driver.  On one of your panels, you should have an icon that looks like a PCB.  Or, your can go to Hardware.

Install the offered ATI driver.

When that is done, immediately use the command in the terminal.

The driver will not be activated until your next reboot.

Unfortunately it didn't work. I did exactly as you described, but after rebooting my Ubuntu doesn't start anymore.

Could it be that my laptop is confused with screens? I have a monitor connected to my laptop, because the screen of the laptop is broken.

I would love to hear more wise knowledge which could help me!

---

### Post by QIII on 2010-10-11
Let's completely remove the ATI driver now and see if we can get you back to using the open source one.  I'm very surprised what we did did not work, despite the external monitor.

Take a look at the following URL.  Look at the section about removing the proprietary ATI driver.  You will have to do this from the recovery mode so you will have a command line.

Aw, dung.  I forgot to add the URL.  Let me find it again.


[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


EDIT:  I just happened to think that there is no xorg.conf by default, and initializing the ATI driver would have created  one.  To avoid problems, follow the  instructions above, but before you leave the terminal, execute the following command:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_BAK
```

That will effectively rename the xorg.conf file so it won't interfere with starting the open source driver.

---

### Post by Aardappelschijfje on 2010-10-11
> **QIII said:**
> Let's completely remove the ATI driver now and see if we can get you back to using the open source one.  I'm very surprised what we did did not work, despite the external monitor.

Take a look at the following URL.  Look at the section about removing the proprietary ATI driver.  You will have to do this from the recovery mode so you will have a command line.

Aw, dung.  I forgot to add the URL.  Let me find it again.


[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


EDIT:  I just happened to think that there is no xorg.conf by default, and initializing the ATI driver would have created  one.  To avoid problems, follow the  instructions above, but before you leave the terminal, execute the following command:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_BAK
```

That will effectively rename the xorg.conf file so it won't interfere with starting the open source driver.

Hmm, before I read this post, I already re-installed Ubuntu. It means that Ubuntu is brand new again (also no updates installed) and that the video driver is not installed.

It means that I can skip the part about removing and that I have to follow the instructions of the manual? And do I still have to use the line which you wrote down in your edit?

Thank you so much for your help! Really appreciated!

---

### Post by QIII on 2010-10-11
If you already installed, leave well enough alone.

You are using the open source driver by default.

This will give me a chance to ruminate a bit.

May I ask why you installed 9.10 instead of 10.04 or the brand new 10.10?

---

### Post by Aardappelschijfje on 2010-10-11
> **QIII said:**
> If you already installed, leave well enough alone.

You are using the open source driver by default.

This will give me a chance to ruminate a bit.

May I ask why you installed 9.10 instead of 10.04 or the brand new 10.10?

Alright :) Then I will leave everything the way it is until you give instructions.

I tried 10.04, but installing it didn't work because the screen went black after I would press "install Ubuntu". I tried the alternative CD and the installation was actually successful, but after the installation was done and I wanted to start Ubuntu, it didn't work and the screen went black again.

10.10 I didn't try, because I actually just heard today that this new version is out already. Do you think I should give it a try?

---

### Post by sendblink23 on 2010-10-11
> **Aardappelschijfje said:**
> Alright :) Then I will leave everything the way it is until you give instructions.

I tried 10.04, but installing it didn't work because the screen went black after I would press "install Ubuntu". I tried the alternative CD and the installation was actually successful, but after the installation was done and I wanted to start Ubuntu, it didn't work and the screen went black again.

10.10 I didn't try, because I actually just heard today that this new version is out already. Do you think I should give it a try?
 It won't bother trying it out.. since your system is actually clean new... you won't be losing anything giving it a try a newer distro version install

---

### Post by QIII on 2010-10-11
Since you have something working for now, I'd just play around with it for a bit and see if you like it.  Like taking a car for a test drive.  Just because it is last year's model doesn't mean you shouldn't.

You may not end up liking Ubuntu's Gnome interface and want to change to KDE or Xfce.

You may want to try a different Linux distribution entirely.

Just use what you have working for now and see if it suits you.

---

### Post by QIII on 2010-10-11
> **sendblink23 said:**
> It won't bother trying it out.. since your system is actually clean new... you won't be losing anything giving it a try a newer distro version install

Except that the OP had problems with Lucid and may have similar frustrations with Maverick.  It won't hurt to just take Jaunty for a drive.

---

### Post by Aardappelschijfje on 2010-10-11
I must say that I am very happy with the Ubuntu interface until now. Everything is very fast and it's so much better than Vista, which used to be on this laptop.

I have tried to install other Linux distributions (Manivra, Linux Mint, and another one), but they all had the same problem: black screen when pressing the install button.

---

### Post by bobwyajnr on 2010-10-11
Hi sorry to butt in to this thread. But I just wanted to add my $0.02.

My experience of the ATI blob driver is it sucks big-time. By some miracle I did manage to get it working my laptop (which has a 4650M card).

I remember going through fun and frolics when Ubuntu 9.04 came out and all the older ATI cards (X1950 and below) were wiped out completely (so you had to use the open source driver). I had an ATI X1950 Radeon Pro at the time so felt a bit screwed!! I tried swapping in an Nvidia 8800 GTX 768Mb card I had purchased (for another project). This card was so much easier to use. Nvidia just appear to produce much better Linux GPU blob drivers than ATI.

So in general when buying new hardware I will stick to Nvidia products (probably for at least 2+ years)...

You just get the latest Nvidia blob driver and bam!! you can get a whole bunch of Steam games to run under WINE. I've even got the Folding@Home GPU client to run under WINE with an older version of Nvidia's Linux-version of CUDA. Also with newer cards you get the option of Nvidia's GPU-based video decode acceleration under Linux: VDAPU, ATI's version of this appears to be a bit broken (given my recent attempts to run it on a 4870 desktop card).

Bob

---

### Post by bobwyajnr on 2010-10-11
> **Aardappelschijfje said:**
> 
I have tried to install other Linux distributions (Manivra, Linux Mint, and another one), but they all had the same problem: black screen when pressing the install button.

Is the external monitor connected by a VGA (15-pin socket) lead? If so then the graphics card may not be able to tell that an external monitor is attached and may try to use the laptops built-in screen. You probably want to rummage about in the laptops BIOS and see if you can force the GPU to output to the VGA port by default.

FYI DVI and HDMI ports tend to more reliable because, in addition to being digital - therefore having practically lose-less transfer, they will feedback information, about an attached display/monitor, to the computers graphics card.

Anyway good luck with your efforts!! I have to say (personally) that after I saw Windows 7 blue screen for the first time I finally saw the light... MS will never produce a good OS... GNU/Linux will eventually catch up in the desktop space :popcorn:

Bob

---

### Post by QIII on 2010-10-11
Your two cents is recognized.

However, NVIDIA also legacied a number of cards.

AMD/ATI provides fine support for cards not in the legacy pile.  The open source driver covers the rest.  I've had no trouble with AMD/ATI cards since 2007.  I've had no problems with NVIDIA cards.

Put yourself in AMD/ATI's position:

1.  You bought ATI in 2007, and now find yourself as AMD/ATI trying to support cards that were made when ATI couldn't give a rat's patoot about Linux.

2.  X is changing, which requires changes to drivers.

3.  You have a number of cards that are getting as common as Edsels in the Linux community because the community avoided them like the plague when ATI didn't give a d*mn.

4.  Those cards have practically reached their expected mechanical lifetimes.

5.  Maintaining the drivers would require substantial resources.

6.  You know the open source community still supports the cards.

7.  You (AMD) are a member of the Linux foundation and you want to support Linux on all of your current products.

Think about your business model.

---

### Post by alphacrucis2 on 2010-10-11
I wonder if the OP has been zapped by a problem with a kernel security patch which has broken fglrx. Suggest trying to download the ATI hotfix that is supposed to address this problem.

See here:

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

First purge the fglrx driver you already installed to get back to square one. Then download and extract the above hotfix installer and follow the binary driver howto adjusting the instruction to cater for your Ubuntu version and the different name of the hotfix installer. You step through the buildpkg method and when done install the created deb files via sudo dpkg -i *.deb. Here's the link to the howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

[COLOR="Red"][B]
NOTE ********* DON'T ATTEMPT TO INSTALL THE ATI HOTFIX VERSION IN MAVERICK. IT IS NEITHER COMPATIBLE NOR REQUIRED FOR MAVERICK MEERCAT.[/B][/COLOR]

---

### Post by QIII on 2010-10-11
Bravo on a good catch!  I'll have to keep that one in mind.

CVE-2010-3081 was pretty important, but if it broke the driver it is counterproductive.

At this point the OP is running on the open source driver, having just reinstalled.

---

### Post by QIII on 2010-10-11
[]("http://ubuntuforums.org/member.php?u=1158218")Aardappelschijfie ...

Given this new information, it might be worth giving 10.10 a go.

---

### Post by bobwyajnr on 2010-10-11
> **QIII said:**
> Your two cents is recognized.

However, NVIDIA also legacied a number of cards.

AMD/ATI provides fine support for cards not in the legacy pile.  The open source driver covers the rest.  I've had no trouble with AMD/ATI cards since 2007.  I've had no problems with NVIDIA cards.
...

Sorry I wasn't trying to start an Nvidia vs. ATI debate. I certainly applaud ATI for starting to release details of the API for their GPU range - which will hopefully lead (in the longer-term) to an open-source driver with full 3D acceleration capabilities.

I had particular problems at the time of the Ubuntu 9.04 release. I couldn't get the 8.04/8.10 releases to install on my server rig (because it was lacking working kernel driver support for Silicon Image SATA port-multipliers). So I was stuck with the 9.04 release which had the Si PM driver support through being based on a newer Linux kernel. The ATI blob driver wouldn't support my X1950 card due to the Ubuntu 9.04 X-Server upgrade and ATI's dropping of support for <X2000 cards in the newer drivers (coincidentally the only ones that supported the newer X-Server version). I bet most Ubuntu users don't find themselves in such a Catch-22 situation!!

I just happened to be taking my first faltering steps into water-cooling at the time and was not finding this particularly easy (e.g. having destroyed a very expensive X1950 XTX card some months earlier)!! :-({|= Hence the fact that I was using a rather ancient graphics card (just bought an X1950 Pro replacement card to match my existing full-coverage GPU block)... 

@Op - Sorry for the off-topic ramble... 

Bob

---

### Post by QIII on 2010-10-11
No debate intended.  I use both.

---

