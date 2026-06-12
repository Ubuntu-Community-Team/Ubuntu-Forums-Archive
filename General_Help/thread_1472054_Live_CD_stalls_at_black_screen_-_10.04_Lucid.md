---
title: "Live CD stalls at black screen - 10.04 Lucid"
date: 2010-05-04
forum: General Help
---

### Post by bumblestiltskin on 2010-05-04
I'm trying to do a clean install of 10.04 Lucid Lynx using the Live CD onto a Toshiba Satellite M35X-S309 laptop.

I boot from the CD, it goes through the startup process, gets passed the 'Ubuntu' screen with the progress dots and then hangs on a black screen right after. There is no more CD activity and it doesn't seem responsive to any input.

I have checked the media from the 10.04 CD boot menu and it checks fine. I have tried both the standard Ubuntu and also the Kubuntu discs and both hang in the exact same spot. I tried both discs on other computers and they boot fine and get me to a working desktop.

I had this machine working just fine with 9.10, but borked it when trying to do an update install.

Here are the specs for the laptop:

Toshiba Satellite M35X-S309
Intel Pentium M 
1gb RAM
60GB HD, DVD/CD-RW, 
Intel 1394abg wireless
Intel 855GME video 

Maybe it's something obvious. I'm thinking it's choking on the graphics, but I really don't know for sure.

---

### Post by dino99 on 2010-05-04
like you i think thats a graphic issue, try to boot with video=vesa on the boot line

---

### Post by GSF1200S on 2010-05-04
> **bumblestiltskin said:**
> I'm trying to do a clean install of 10.04 Lucid Lynx using the Live CD onto a Toshiba Satalitte M35X-S309 laptop.

I boot from the CD, it goes through the startup process, gets passed the 'Ubuntu' screen with the progress dots and then hangs on a black screen right after. There is no more CD activity and it doesn't seem responsive to any input.

I have checked the media from the 10.04 CD boot menu and it checks fine. I have tried both the standard Ubuntu and also the Kubuntu discs and both hang in the exact same spot. I tried both discs on other computers and they boot fine and get me to a working desktop.

I had this machine working just fine with 9.10, but borked it when trying to do an update install.

Here are the specs for the laptop:

Toshiba Satellite M35X-S309
Intel Pentium M 
1gb RAM
60GB HD, DVD/CD-RW, 
Intel 1394abg wireless
Intel 855GME video 

Maybe it's something obvious. I'm thinking it's choking on the graphics, but I really don't know for sure.

This is an issue alot of people have been having. When you boot the liveCD, select your language and highlight but DONT hit enter the "Try Ubuntu Without Installing" option. Then, hit ESC and look for the line that ends in:
```
ro quiet splash
```
and change it to:
```
ro i915.modeset=0
```

For other users who see this thread, the above applies to an intel graphics device. If you are using an Nvidia card you would do:
```
ro nomodeset
```
instead of:
```
ro i915.modeset=0
```

To the OP, I cant gaurantee this will work- it does for some and not for others. It doesnt work for me- I installed 10.04 with the alternate CD and chrooted into the install to make these changes (nomodeset works, but for some reason NOT when I just edit the grub boot line- makes no sense to me).

As dino99 suggested, you can try:
> xdriver=vesa
after whatever modeset option you use.

---

### Post by bumblestiltskin on 2010-05-04
The ubuntu proper live cd jumps straight to the splash when installing (no language select or option screen). I can't figure how to get to the boot options in it.

BUT... The Kubuntu cd is setup like the installs I'm used to. I chose my language and highlighted the 'Try Kubuntu without installing' option. Hitting escape takes me to the command line "boot:" prompt. Unfortunately, I don't know what to put in ahead of the i915.modeset=0 command to boot the kernel...

BUT... Hitting F6 on the options screen pops up a boot options line on the options screen, which I can edit. It reads:

```
file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
```

I tried replacing the 'quiet splash' at the end with 'ro 915.modeset=0', 'video=vesa' and 'xdriver=vesa', but it still hangs on a black screen.

Maybe I'm entering the mode options in the wrong spot?

---

### Post by bumblestiltskin on 2010-05-04
Anyone else have an idea how to get beyond the black screen?

---

### Post by Rubi1200 on 2010-05-04
Yes!!! It worked for me at least.

Just to be clear, this is only for the LiveCD and getting to the desktop in 10.4

Once there I am not sure what you would have to do if you install and want to make this a permanent install.

So, here we go:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameters in this order:

xforcevesa noapic noapci nosplash irqpoll

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04

As I said this is only good for the LiveCD and I do not know where to go from here for a permanent install.

Please note that this worked for me after much frustration and looking around for solutions.

So, how did I get here?

I downloaded the latest RC of LinuxMint, based of course on Lucid. The first attempt failed as it had done for Ubuntu. Then I restarted and used Compatibility Mode; which worked!
Then I went to the syslinux.cfg file, looked at the parameters for compatibility mode and used them on the Ubuntu boot; and voila!

Good luck and I really hope this works for others who, like me, have been having this issue.
Just to be clear, I have an Intel graphics card i8xx series about which the release notes speak as being a known bug in 10.04.

---

### Post by Rubi1200 on 2010-05-04
I want to add that I used UNetbootin to load the LinuxMint RC onto a USB drive and it is from there that I was able to look at the syslinux.cfg file that UNetbootin uses to store the boot parameters.
I also removed one of the parameters because I didn't think it was relevant.
Again, I hope this works for some people.

---

### Post by Macchi on 2010-05-04
I know that machines with Intel graphics i85x etc have had problems with the latest kernel 2.6.32-21 for Lucid. The Beta 1 and Beta 2 releases had ealier kernels and worked ok.
The problem seems to be an interaction between the Kernel Mode Setting.

There are some workarounds for installed systems on:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I did not manage to get Lucid final running on one of my test systems and had to install with Beta 2, upgrade, and apply the first workaround mentioned on the link above. Sorry I have no better answer and I am upset with this serious problem on a Lon term Support release.

---

### Post by philinux on 2010-05-04
To get the normal menu hit any key as soon as the splash screen appears. See forum sticky re lucid.

---

### Post by bumblestiltskin on 2010-05-04
Thanks everyone for the possible solutions for getting the CD to boot. Before the replies came through, I decided try a clean 9.10 install and then upgrade to 10.04. I know this didn't work great last time, but that 9.10 install had been on there several months, with lots of package installs, removals and upgrades. I figured this way would be a lot more straight forward for the upgrade installer.

> **Macchi said:**
> I did not manage to get Lucid final running on one of my test systems and had to install with Beta 2, upgrade, and apply the first workaround mentioned on the link above. Sorry I have no better answer and I am upset with this serious problem on a Lon term Support release.

Thanks much for the info. After the upgrade install finishes, I'll try the first solution and re-enable KMS. Hopefully that will do the trick. I'll know in about a half-hour or so.

I also think it's pretty frustrating that this was an issue in the LTS. There are so many odd and half backed items included in the LTS this time around. Dropping support for a popular Intel graphics chipset is not one of the things that should have been done. If this were a normal six-month refresh, it might be okay, if were to later be fixed with an update. But this is the LTS which a lot of users choose so we don't need to go through the upgrade cycle in another six months. The energy that was put into getting some of the questionable items together in time for this LTS, could have been put toward fixing items like the chipset issue and others that have crept up. The way I view the LTS is it's supposed to be a rock-solid release that is fine tuned for committed deployment. For me it's been frustrating, and somewhat embarrassing, as I've been touting this version to people as THE ONE to settle on or try out for Ubuntu. I think 9.l0 would have made a better LTS now that I've had a chance to play with 10.04. 

Sorry for the rant. I'll post back with an update on how the workaround went after the upgrade finishes.

---

### Post by Dragonbite on 2010-05-04
I've been getting this issue and putting ```
i915.modeset=0
``` has done nothing for me so far. At least I have a few more possibilities thanks to this thread.  Wish me luck!

---

### Post by bumblestiltskin on 2010-05-04
> **Rubi1200 said:**
> Yes!!! It worked for me at least. ...
... Good luck and I really hope this works for others who, like me, have been having this issue.
Just to be clear, I have an Intel graphics card i8xx series about which the release notes speak as being a known bug in 10.4.

Success!!! I tried the steps you outlined and they worked perfectly. The only thing that I needed to do differently was hit enter at the "keyboard/stickman" graphic which pops up before the Ubuntu splash logo. If I tried it at the splash logo it would attempt to go through the boot process and hang. Anyway, I followed the steps and altered the boot parameters. I am now currently staring at a 10.04 Live CD desktop over on the Toshiba laptop.

I also followed through with the clean 9.10 > 10.04 install and it worked fine. The update to 10.04 requires a reboot, so before I did that, I followed the instructions for 'Workaround A' in [Macchi's post]("http://ubuntuforums.org/showpost.php?p=9236835&postcount=8") for re-enabling the graphics. 

> Workaround A: Re-enable KMS

For release we made the decision to blacklist KMS for 8xx hardware. If you had found that beta1 and earlier Ubuntu had been working fine, this may be an effective workaround for you.

To turn KMS back on, run this command in a Terminal window and reboot:

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
```


I would imagine that after completing the install from the Live CD, and before rebooting, you (collective you) could point the terminal at the current installation and proceed with the above instructions. I'm not sure how you make sure the above instructions work on the new install while logged in as the Live CD user, but I bet it's pretty straightforward and someone will chime in. 

In fact, would someone please chime in and give some clear instructions as how to enter the above code so that it fixes the new hard drive install while still being logged into the Live CD user? THANKS!

---

### Post by Rubi1200 on 2010-05-05
I am so glad it worked for you bumblestiltskin. I, like you, agree that it is rather odd that support for Intel graphic cards was dropped/changed etc. or whatever the decision entailed.

As far as the KMS workaround is concerned; I wonder if installing 10.4, restarting and using the parameters I suggested at boot, then using the workaround would work?

> Workaround A: Re-enable KMS

For release we made the decision to blacklist KMS for 8xx hardware. If you had found that beta1 and earlier Ubuntu had been working fine, this may be an effective workaround for you.

To turn KMS back on, run this command in a Terminal window and reboot:

Code:
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

Anyway, I am really pleased that you got to at least see the new version!

I have decided, for the moment, to stick with Karmic, which has support, until; April 2011.

I am going to wait and see if these issues are worked out or redefined in the next release in October.
:)

---

### Post by bumblestiltskin on 2010-05-05
> **Rubi1200 said:**
> I am so glad it worked for you bumblestiltskin. 

... As far as the KMS workaround is concerned; I wonder if installing 10.4, restarting and using the parameters I suggested at boot, then using the workaround would work?

I have decided, for the moment, to stick with Karmic, which has support, until; April 2011.

I am going to wait and see if these issues are worked out or redefined in the next release in October.
:)

Thanks Rubi1200. 

I'm tempted to reinstall the Toshiba from straight from CD media (no upgrading) to make sure it can be done. Right now, everything seems to work fine, but everything seems kludged together compared to 9.10 which was soooo close to a perfect polished OS. 

I've fooled around with 10.04 for a few days now and it's just not prime time ready. For now I'm going to do what you did and stick with 9.10. Most developers update their PPA's through multiple versions, so I think the software I use should be maintained at least through April of 2011.

Anyway, I think I'll reinstall it from scratch knowing everything we know now. If I'm successful, I'll mark this thread solved and add a post to the sticky for Lucid at the top of the page.

---

### Post by Rubi1200 on 2010-05-05
No problem!

I think with so many issues in this release it is worthwhile waiting a little bit until things are dealt with.

I already posted the workaround to the sticky at the top, but you are more than welcome to let people know that it works :-)

---

### Post by bumblestiltskin on 2010-05-05
> **Rubi1200 said:**
> No problem!

I think with so many issues in this release it is worthwhile waiting a little bit until things are dealt with.

I already posted the workaround to the sticky at the top, but you are more than welcome to let people know that it works :-)

Finished the 10.04 Lucid install from CD just now. Decided to see if it would boot on it's own after the install. Expected it to crash and instead it booted right to the desktop. I didn't even need to enter the workaround in the terminal. Everything seems to work just fine. It shows as Intel 855GM graphics when polled.

It appears -- and this is only from my personal experience -- that the problem is with the Live portion of the CD only and ends up installing the drivers correctly.

It would be nice to hear more input on this. I'm marking this as solved so others can try out the solution.

Thanks to everyone for all the help.

---

### Post by doundounba on 2010-05-05
Hi all,

Kudos to everyone on this thread. I had the same problem trying to do a clean install of Kubuntu on a Dell 700m laptop.

Using Rubi1200's workaround of changing the boot options on the liveCD to
> 
file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --


I was able to boot the liveCD and install the OS. However, the resolution after the install was fixed at 1024x768, rather than the correct 1280x800. Upon checking, I was able to see that the install had forced the use of the Vesa driver (as per the boot options of the liveCD). What I did then was:

First, remove the 'Driver "vesa"' line from /etc/X11/xorg.conf:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

```

Then follow the instructions [here]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") in order to re-enable KMS (whatever that is):

> 
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u


Reboot, and now things are fine.  Dunno why they did this - very annoying. But at least I'm running now.

---

### Post by Rubi1200 on 2010-05-06
Excellent! I am so glad this is helping people.
It seems that the solution is to use my workaround to boot the LiveCD and then the fix for KMS.
Good question, though, about the logic of this move by the developers.
Oh well, that is why we are here; to learn and to help each other.

---

### Post by Dragonbite on 2010-05-06
I must be cursed.. I haven't gotten any further than before with the suggestions.

I never get to the keyboard/stick person splash screen and after that shows up it just continues to boot.

I've tried the "xforcevesa" and "i915.modeset=0" and "ro i915.modeset=0" and "xdriver=vesa" and "video=vesa" and "xforcevesa noapic noapci nosplash irqpoll".

One caveat, though, is that I am trying this from a USB thumb drive which I verified on another system that it works properly.  Nice thing is that booting up, I can get right into the bootup command before the splash screen which is where I put these various commands.

EDIT: all may NOT be lost. Just ran across this [_thread _]("http://ubuntuforums.org/showthread.php?p=9239776#post9239776")which he is using the same model laptop I am having trouble (D400).  His suggestions is using "i915.modeset=1" (I was setting to "0").  I'll be trying this tonight!

---

### Post by Rubi1200 on 2010-05-06
Hi Dragonbite,
sorry to hear you are still having problems.
Did you set things up using UNetbootin?
If the answer is yes, then browse the drive and open the syslinux.cfg file.
There, you should find UNetbootin's boot menu entries and under (I think it is called Default or maybe the next entry) add the boot parameters I showed earlier in the post. Close and save the file, then reboot and see if that works.
Let me know please.
:)

---

### Post by Rubi1200 on 2010-05-06
Okay,
so maybe this is a laptop specific issue.
Did you try "i915.modeset=1"?
Good luck!

---

### Post by Dragonbite on 2010-05-06
> **Rubi1200 said:**
> Hi Dragonbite,
sorry to hear you are still having problems.
Did you set things up using UNetbootin?
If the answer is yes, then browse the drive and open the syslinux.cfg file.
There, you should find UNetbootin's boot menu entries and under (I think it is called Default or maybe the next entry) add the boot parameters I showed earlier in the post. Close and save the file, then reboot and see if that works.
Let me know please.
:)

Will do when I get the chance.  

Nice thing about Unetbootin is that to boot up you hit Enter to get into the default (USB drive) boot loader, and then hitting "Tab" gets you right into the bootup command.

Somebody else, who has a Dell D400 just like me, said to set the modeset to "1" instead of the "0" mentioned in most places.```
i915.modeset=_**1**_
```

If I can go into the boot menu and save it with this change, that will make things easier (I have 3 hard drives for this laptop ;) ).

Either way I'll post my results in case anybody else runs across this issue too.

---

### Post by Rubi1200 on 2010-05-06
Ok, I did some more testing and it seems that using i915.modeset=1 on the boot line works just as well as the other stuff I posted (except it took slightly longer to get to the desktop I think).
It seems there is a  solution then for all tastes.
Hope this was useful.
:-)

---

### Post by Dragonbite on 2010-05-06
I haven't done extensive testing, but initially it works. It booted up!

---

### Post by Unicast on 2010-05-06
I started out using the i915.modeset=1 kernel option on my D400 but found that every so often X would crash and try (unsuccessfully) to restart in low res mode.

The only fix that's proved robust for me was upgrading to a mainline kernel - kernel version in sig.

Not the most elegant of solutions but it's working very well for me and has proved to be very stable so far.

---

### Post by Dragonbite on 2010-05-06
Oh well, when I tried playing the sample video that came with the Live session, it crashed on me.  Maybe the newer kernel will work with that too.

I'm just surprised it has gotten this far already.  I mean, it's gotten this far and with Fedora coming out in less than 2 weeks, it will be interesting to see if they address this or not.

---

### Post by Unicast on 2010-05-07
Just noticed that there's a kernel update in the list of updates when Update Manager popped up this morning.

I'm thinking my system will revert to the kernel version in the update, so I'll report back and let you know how things go.

---

### Post by Rubi1200 on 2010-05-07
Glad you got things moving forward (sort of) Dragonbite. I have decided to stick with Karmic for the time being and wait to see what will happen once the first major bugs have been taken care of. Personally, I see no reason to rush into Lucid, especially since Karmic is supported until April 2011.
Good luck!

---

### Post by Unicast on 2010-05-07
Update....

The new kernel in this morning's update didn't help at all.

As well as the mainline kernel I have these two listed in grub:

2.6.32-21
2.6.32-22

Neither of them will allow my laptop to boot into X without the "i915.modeset=1" kernel option.

---

### Post by indifference on 2010-05-09
I've also got this problem while booting the live cd.
I could boot only with "xforcevesa". After install, the same.
So I tried to install a different kernel 2.6.33 from ppa. For my surprise verything works like a charm! [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

Try it!

---

### Post by sasaenator on 2010-05-09
> **indifference said:**
> I've also got this problem while booting the live cd.
I could boot only with "xforcevesa". After install, the same.
So I tried to install a different kernel 2.6.33 from ppa. For my surprise verything works like a charm! [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

Try it!

Hallo!I have a similar problem with intel graphics,so I want to try this solution with new kernel.Which files do I need to download and how to install them,through Synaptic?Thanx!7

---

### Post by indifference on 2010-05-09
Hello! You should install [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb) or the amd64 version if is that the case! Hope it works for you :P

You just download it and double click it ;)

> **sasaenator said:**
> Hallo!I have a similar problem with intel graphics,so I want to try this solution with new kernel.Which files do I need to download and how to install them,through Synaptic?Thanx!7

---

### Post by Catharsis on 2010-05-09
> **sasaenator said:**
> Hallo!I have a similar problem with intel graphics,so I want to try this solution with new kernel.Which files do I need to download and how to install them,through Synaptic?Thanx!7

Please try replacing "quiet splash" with "i915.modeset=1" and "i915.modeset=0" first before upgrading your kernel. Using a mainline kernel poses some problems:
1) Ubuntu-specific patches aren't applied, such as ureadahead, which is required for the lightning-fast boot speed.
2) Proprietary drivers won't work (System->Administration->Hardware Drivers).
3) The kernel won't update itself automatically, so you constantly need to check for a new kernel version to get security and stability fixes.

That said, to upgrade to the latest mainline kernel:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
```

---

### Post by sasaenator on 2010-05-09
Thanks!I did it with "i915 modeset",and now everything looks OK!The problem is I did the same thing few days ago and after the system update,after downloading all of the programs and setting up the system to my taste it suddenly crashed and I couldn't boot it up till few minutes ago.BTW I had some problems with grub2 meanwhile:)!Guess I have no choice than to do that all over again,and see,maybe this time it will be better!Thanks again,people for those quick replies!7

---

### Post by Catharsis on 2010-05-09
> **sasaenator said:**
> Thanks!I did it with "i915 modeset",and now everything looks OK!The problem is I did the same thing few days ago and after the system update,after downloading all of the programs and setting up the system to my taste it suddenly crashed and I couldn't boot it up till few minutes ago.BTW I had some problems with grub2 meanwhile:)!Guess I have no choice than to do that all over again,and see,maybe this time it will be better!Thanks again,people for those quick replies!7

Adding i915.modeset=1 through the grub menu doesn't get saved, fyi. So if the only problem is that the fix reverses when you reboot, just follow the first terminal command in Workaround A:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by sasaenator on 2010-05-09
> **Catharsis said:**
> Adding i915.modeset=1 through the grub menu doesn't get saved, fyi. So if the only problem is that the fix reverses when you reboot, just follow the first terminal command in Workaround A:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I did it,but now when I hit "e" in grub menu it shows only quiet splash at the and of the line.Is that OK?And just a minute ago Lucid crashed and showed a message "running in low graphics mode",or something like that,then offered a menu with some options to view log,to restart X and some other things.At the end of the log it says:"Fatal server error:failed to submit batchbuffer:input/output error"!Also saved it somewhere but I cannot remember where.If it happens again I will remember:)!BTW I have a Toshiba laptop with Intel 82852/855GM integrated graphic card.:(

---

### Post by Catharsis on 2010-05-09
What is the output of
```
cat /etc/modprobe.d/i915-kms.conf
```
?

---

### Post by sasaenator on 2010-05-09
"options i915 modeset=1"
Looks like it is OK,or?

---

### Post by Catharsis on 2010-05-09
If it crashes again, see if removing your xorg.conf helps (if you have one)
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If this messes stuff up, you can revert it with:
```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by sasaenator on 2010-05-09
Ijus have a xorg.conf.failsafe file in the X11 directory,but I think it was not there right after installation,I think it is created after the crash.Any other ideas?Not that I am not thankfull :)!

---

### Post by Catharsis on 2010-05-09
Try removing your nvidia drivers. This worked for a couple people.
```
sudo apt-get remove --purge nvidia*
```
Just make sure you check what it wants to remove before you agree.

Reboot, and see if it freezes again.

---

### Post by sasaenator on 2010-05-09
> **Catharsis said:**
> Try removing your nvidia drivers. This worked for a couple people.
```
sudo apt-get remove --purge nvidia*
```
Just make sure you check what it wants to remove before you agree.

Reboot, and see if it freezes again.

I did it,also did the update,everything looks OK,I will continue setting the system up to my needs,and if it crashes again I will inform you!Thanks again!7

---

### Post by sasaenator on 2010-05-09
It happened again when I tried to do a Administration>System Testing>video test with color bars and static.System crashed to a screen which is usualy displayed during boot proccess but now it can&#324;ot go past that screen it just stands there and every second or two it switches to only cursor line and then back to the screen which looks like this:
fsck from util-linux-ng 2.17.2
/dev/sda1:clean, 160082/642112 files,671105/2563476 blocks
*starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox          (OK)

*Setting sensor limits                                                (OK)
*Speech-dispatcher cofigured for user sessions                        
*Starting Common Unix Printing System: cupsd                          (OK)
*PulseAudio cofigured for per-user sessions
*Enabling additional executable binary formats binfmt-support         (OK)    
*Checking battery state...                                            (OK)

_

---

### Post by Catharsis on 2010-05-09
This is another X crash, unfortunately. If it happens again, you can try getting it back by typing "startx". If it doesn't send you to a terminal, you can get one by typing Ctrl+Alt+F2.

Try reconfiguring xserver-xorg. First, log into a TTY by typing Ctrl+Alt+F2. Then:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by sasaenator on 2010-05-09
Maybe I should try Workaround E and/or F from this page:[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) ,but I do not know if I can do that with xorg.conf.failsafe file.

---

### Post by sasaenator on 2010-05-09
We were writing at the same time,I will try that now!

---

### Post by sasaenator on 2010-05-09
Nope!It doesn`t work.This time I ended up with a black screen with just one white line like a cursor but without blinking.Couldn`t get to the terminal!Manually restarted.

---

### Post by Catharsis on 2010-05-09
> **sasaenator said:**
> Maybe I should try Workaround E and/or F from this page:[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) ,but I do not know if I can do that with xorg.conf.failsafe file.

You can absolutely try them. First, make the failsafe xorg.conf a usable one too:
```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```
Then edit it with:
```
gksudo gedit /etc/X11/xorg.conf
```
Just make sure you also change
```
	Driver		"fbdev"
```
to
```
	Driver		"intel"
```
in the "Device" section.

---

### Post by sasaenator on 2010-05-09
Tried workaround F still the same crash when trying video test!Should I use the command to reconfigure xorg to put things where they were?

---

### Post by Catharsis on 2010-05-09
If you want to keep playing with xorg.conf, you can just edit it again. If you want to revert back to before you were playing with it, remove it with:
```
sudo rm /etc/X11/xorg.conf
```

You could also try updating your intel driver:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
sudo apt-get upgrade
```

Upgrading to the mainline kernel will also almost definitely solve your problem.

---

### Post by sasaenator on 2010-05-09
> **Catharsis said:**
> If you want to keep playing with xorg.conf, you can just edit it again. If you want to revert back to before you were playing with it, remove it with:
```
sudo rm /etc/X11/xorg.conf
```

You could also try updating your intel driver:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
sudo apt-get upgrade
```

Upgrading to the mainline kernel will also almost definitely solve your problem.

 Tried updating driver,system freezes after video test,but it doesn't crashes to that screen I posted before.Still have to manually reboot.
Unfortunately mainline kernel is out of the question because the laptop is my brother's and he is using it for work.I'll have to go now will continue tomorrow and post results if I find anything.Thanx!Goodbye!7:popcorn:

---

### Post by sasaenator on 2010-05-10
OK,I'm back!I tried this:[]("http://ubuntuforums.org/showthread.php?t=1472159")
it is better now,when I try to test my hardware the system doesn't crash,it just stops the program,and I can't see color bars and static,but I can continue to the next test.

---

### Post by Hobodavel on 2010-05-11
I have the same problem so I updated the driver and it gives me two errors one which says:

[LIST=1]
[*]No kernal modesetting driver
[*]Screen found but none known suitable config
[/LIST]
So any suggestions from here...

Thanks

---

### Post by sasaenator on 2010-05-11
> **Hobodavel said:**
> I have the same problem so I updated the driver and it gives me two errors one which says:

[LIST=1]
[*]No kernal modesetting driver
[*]Screen found but none known suitable config
[/LIST]
So any suggestions from here...

Thanks

Did you try with i915.modeset=1 ?
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Workaround A

---

### Post by Hobodavel on 2010-05-11
I did that and now when i boot in failsafe graphics it throws me with the following errors:

[LIST=1]
[*]Failed to submit batch buffer
[*]Could not create pixmap for fbcon
[/LIST]
And if i boot normally it shows the load up page and then gives an error: failed user id

Thanks

---

### Post by sasaenator on 2010-05-11
> **Hobodavel said:**
> I did that and now when i boot in failsafe graphics it throws me with the following errors:

[LIST=1]
[*]Failed to submit batch buffer
[*]Could not create pixmap for fbcon
[/LIST]
And if i boot normally it shows the load up page and then gives an error: failed user id

Thanks

I don't know, i915.modeset=1 works for my 82852/855GM intel integrated graphics,except I cannot play any video,system freezes when I try.
Maybe you should try some of the solutions posted before in this thread if not already and if you have intel graphics.

---

### Post by sasaenator on 2010-05-11
OK,people mainline kernel works great!I downloaded rc6 first,then updated to rc7,all test till now are ok!Here is the code,but beware that this is the mainline kernel,whatever that means :):
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb
```

---

### Post by Dragonbite on 2010-05-11
> **sasaenator said:**
> OK,people mainline kernel works great!I downloaded rc6 first,then updated to rc7,all test till now are ok!Here is the code,but beware that this is the mainline kernel,whatever that means :):
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb
```

So what is a "mainline kernel"? And will  this mess up with regular Ubuntu updates?

Be nice if they would produce a fix, then respin the CDs so people with Intel don't go through this.

---

### Post by Catharsis on 2010-05-11
> **Dragonbite said:**
> So what is a "mainline kernel"? And will  this mess up with regular Ubuntu updates?

It just adds another kernel to grub. Since it'll be a higher version number than the others installed, grub will automatically boot into it. 

If you try it and don't like it, just hold down Shift while booting and select the old kernel instead. You can also remove the mainline kernel through Synaptic-- just search for 2.6.34 and mark it as Completely Remove (just make sure you've booted from a different kernel before removing it; it's not good to remove the kernel you're currently booted into :P).

---

### Post by sasaenator on 2010-05-11
[QUOTE=Catharsis;9269805] Using a mainline kernel poses some problems:
1) Ubuntu-specific patches aren't applied, such as ureadahead, which is required for the lightning-fast boot speed.
2) Proprietary drivers won't work (System->Administration->Hardware Drivers).
3) The kernel won't update itself automatically, so you constantly need to check for a new kernel version to get security and stability fixes.

This too!Thanks,Catharsis for all the help on this issue!7

---

### Post by Dragonbite on 2010-05-12
> **sasaenator said:**
> Did you try with i915.modeset=1 ?
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Workaround A

Ok, since using i915.modeset=1 works, I went to that site and did Workaround A.  So far, it seems to work.

I haven't tried video yet though.

---

### Post by sasaenator on 2010-05-13
> **Dragonbite said:**
> Ok, since using i915.modeset=1 works, I went to that site and did Workaround A.  So far, it seems to work.

I haven't tried video yet though.

See if the video works,and maybe you should also try system testing utility,video section.I couldn´t get video to run nor could I get past that test without the mainline kernel,which I am using for a few days now and it works great.I´ve had just one crash because I experimented with Compiz too much!

---

### Post by Dragonbite on 2010-05-13
> **sasaenator said:**
> See if the video works,and maybe you should also try system testing utility,video section.I couldn´t get video to run nor could I get past that test without the mainline kernel,which I am using for a few days now and it works great.I´ve had just one crash because I experimented with Compiz too much!

Right after I posted that, I tried the Example video that comes included.... crash.

I'm not sure how deep of a crash it is, though.  It seemed like there was a comatose pulse going on but I couldn't revive it.

So, maybe that's part of the business focus... "keep your employees working, not watching videos" ;)

---

### Post by sasaenator on 2010-05-13
> **dragonbite said:**
> right after i posted that, i tried the example video that comes included.... Crash.

I'm not sure how deep of a crash it is, though.  It seemed like there was a comatose pulse going on but i couldn't revive it.

So, maybe that's part of the business focus... "keep your employees working, not watching videos" ;)

:p

---

### Post by Dragonbite on 2010-05-18
Sounds like they have a patch out.
> [_855GM - fixed kernel modules_]("https://launchpad.net/~glasen/+archive/855gm-fix")
This package contains the source of the kernel modules "i915.ko" and "intel-agp.ko" packaged with approriate configuration for DKMS to build new modules dynamically.

The kernel modules contain a patch (See bug-report below) which should fix the lockups on 855GM-based hardware. A known side-effect is slowdown of some Gtk+-functions.

For more informations please read the following bug report :

[http://bugs.freedesktop.org/show_bug.cgi?id=27187](http://bugs.freedesktop.org/show_bug.cgi?id=27187)

Update :

The package "855gm-fix-exp" improves the graphics performance dramatically, but the system could be more unstable. If you experience crashes with this package and the non-experimental package cure the crashes, than please install the non-experimental package.

Plus somebody did a re-mix CD including this patch.  Go to the page itself for all of the links, I only added the torrent link.

> [_Live-CD of Ubuntu 10.04 with updated Intel-drivers and 855gm-patched kernel-modules_]("https://launchpad.net/~glasen/+archive/855gm-fix")
As I promised in one of my (german) comments, i’ve made a remastered live-CD of Ubuntu 10.04. This live-CD can be downloaded by using a Bittorrent-client :

[_ubuntu-10.04-855gm-desktop-i386.iso_.torrent_]("http://glasen-hardt.de/wp-content/uploads/2010/05/ubuntu-10.04-855gm-desktop-i386.iso_.torrent")

The remastered live-CD was updated with the latest packages (May 7th) including the latest Lucid kernel version “2.6.32-22.33&#8243;. I’ve also installed the intel-driver and the needed libdrm-packages from my own PPA.

The CD also includes the 855gm-patched kernel-modules i’ve made, to improve stability on 845/855-chipset-based systems. The CD includes the normal, more stable “855gm-fix-dkms”-package and not the experimental one.

The CD and later the installed system, boot automatically in KMS-mode. There is no need to fiddle around with configuration files to get KMS running. In addition i’ve activated the integration of Plymouth into the initrd-file to improve the eye-candy of the system boot.

To make room for this changes, i had to remove some of the preinstalled packages :

    * All Mono- and Mono-based packages (F-Spot, Tomboy & Gbrainy)
    * The package “binfmt-support” (Allows to run Mono-based applications as native programs)
    * All GNOME games
    * The files “wubi.exe” and “autorun.inf” which are for a windows based installation

If you want to reinstall this packages after a successful installation, you can use this command :

sudo aptitude reinstall --with-recommends ubuntu-desktop

May not be idea, but may work.

---

### Post by sasaenator on 2010-05-18
> **Dragonbite said:**
> Sounds like they have a patch out.


Plus somebody did a re-mix CD including this patch.  Go to the page itself for all of the links, I only added the torrent link.



May not be idea, but may work.

Hm,don´t know what to do now.I have a mainline kernel now and it works OK,it is too big trouble now to reinstall the system.Do you (or anybody) know is there a way to implement this fix without the reinstall of ubuntu,something similar as the mainline kernel implementation.Thank you for the update anyway!

P.S. Should this thread be marked as solved?

---

### Post by Catharsis on 2010-05-18
> **sasaenator said:**
> Hm,don´t know what to do now.I have a mainline kernel now and it works OK,it is too big trouble now to reinstall the system.Do you (or anybody) know is there a way to implement this fix without the reinstall of ubuntu,something similar as the mainline kernel implementation.Thank you for the update anyway!

P.S. Should this thread be marked as solved?

Sources:
[http://glasen-hardt.de/?p=568](http://glasen-hardt.de/?p=568)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/168](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/168)
[https://launchpad.net/~glasen/+archive/855gm-fix](https://launchpad.net/~glasen/+archive/855gm-fix)
[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)
[https://launchpad.net/~glasen/+archive/libdrm](https://launchpad.net/~glasen/+archive/libdrm)

WARNING: The following patch is experimental. Use at your own risk. Mileage may vary.

To enable the patch, reboot into the 2.6.32-22 kernel (hold Shift while booting to enter the grub menu where you can choose).
```
sudo add-apt-repository ppa:glasen/855gm-fix
sudo add-apt-repository ppa:glasen/intel-driver
sudo add-apt-repository ppa:glasen/libdrm
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install dkms linux-headers-generic 855gm-fix-dkms
```
The final command didn't work for me (just said "Abort."), so I had to install each package separately. It worked fine then (except that "linux-headers-generic" was already installed, but that's nothing to worry about).

Reboot into the 2.6.32-22 kernel. This patch will only be applied to the kernel you are running when you install it (which is why you should boot into the current Lucid kernel (2.6.32-22) before enabling it).

---

### Post by sasaenator on 2010-05-18
> **Catharsis said:**
> Sources:
[http://glasen-hardt.de/?p=568](http://glasen-hardt.de/?p=568)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/168](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/168)
[https://launchpad.net/~glasen/+archive/855gm-fix](https://launchpad.net/~glasen/+archive/855gm-fix)
[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)
[https://launchpad.net/~glasen/+archive/libdrm](https://launchpad.net/~glasen/+archive/libdrm)

WARNING: The following patch is experimental. Use at your own risk. Mileage may vary.

To enable the patch, reboot into the 2.6.32-22 kernel (hold Shift while booting to enter the grub menu where you can choose).
```
sudo add-apt-repository ppa:glasen/855gm-fix
sudo add-apt-repository ppa:glasen/intel-driver
sudo add-apt-repository ppa:glasen/libdrm
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install dkms linux-headers-generic 855gm-fix-dkms
```
The final command didn't work for me (just said "Abort."), so I had to install each package separately. It worked fine then (except that "linux-headers-generic" was already installed, but that's nothing to worry about).

Reboot into the 2.6.32-22 kernel. This patch will only be applied to the kernel you are running when you install it (which is why you should boot into the current Lucid kernel (2.6.32-22) before enabling it).

Tried to install it into 2.6.32-22,dkms and linux-headers-generic went OK,but 855gm-fix-dkms reported error 10.During the installation process I saw that it tried to install in the mainline kernel also,don´t know why!Now I cannot boot into 2.6.32-22,only into the mainline.

---

### Post by sasaenator on 2010-05-18
> **sasaenator said:**
> Tried to install it into 2.6.32-22,dkms and linux-headers-generic went OK,but 855gm-fix-dkms reported error 10.During the installation process I saw that it tried to install in the mainline kernel also,don´t know why!Now I cannot boot into 2.6.32-22,only into the mainline.

"E: 855gm-fix-dkms: subprocess installed post-installation script returned error exit status 10"
This is the error that I´ve got in the update process after booting back to the mainline kernel and after running an update which offered me to install something to do with intel,nouveu,and ati,can´t remember exactly!7

---

### Post by sasaenator on 2010-05-18
And her is the log of the 855gm-fix-0.6.2-dkms:

DKMS make.log for 855gm-fix-0.6.2 for kernel 2.6.34-020634rc7-generic (i686)
Wed May 19 00:28:47 CEST 2010
make: Entering directory `/usr/src/linux-headers-2.6.34-020634rc7-generic'
  LD      /var/lib/dkms/855gm-fix/0.6.2/build/agp/built-in.o
  CC [M]  /var/lib/dkms/855gm-fix/0.6.2/build/agp/intel-agp.o
In file included from /var/lib/dkms/855gm-fix/0.6.2/build/agp/intel-agp.c:13:
/var/lib/dkms/855gm-fix/0.6.2/build/agp/intel-agp-add.h:11: error: static declaration of ‘wbinvd_on_all_cpus’ follows non-static declaration
/usr/src/linux-headers-2.6.34-020634rc7-generic/arch/x86/include/asm/smp.h:139: note: previous declaration of ‘wbinvd_on_all_cpus’ was here
make[2]: *** [/var/lib/dkms/855gm-fix/0.6.2/build/agp/intel-agp.o] Error 1
make[1]: *** [/var/lib/dkms/855gm-fix/0.6.2/build/agp] Error 2
make: *** [_module_/var/lib/dkms/855gm-fix/0.6.2/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.34-020634rc7-generic'

I´m not sure if I´ll be able to boot into this kernel again!

---

### Post by Catharsis on 2010-05-18
You might want to remove the mainline kernel through Synaptic and then try again. You can reinstall the mainline by using the same commands you did to install them originally, so there's nothing to worry about (updated instructions at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)).

To remove it, go to Synaptic and search 2.6.34 and mark all for Complete Removal and then Apply. Make sure you're not in the mainline kernel when you remove it, as that would be bad :)

If you don't want to mess with your mainline kernel, I would contact Stefan Glasenhardt at [email]stefan@glasen-hardt.de[/email] (from [https://launchpad.net/~glasen](https://launchpad.net/~glasen)) and ask him how to install the patch while the mainline is also installed. You might also want to tell him about your issue just so he knows it causes problems for those who use the mainline kernel as a workaround.

---

### Post by sasaenator on 2010-05-19
> **Catharsis said:**
> You might want to remove the mainline kernel through Synaptic and then try again. You can reinstall the mainline by using the same commands you did to install them originally, so there's nothing to worry about (updated instructions at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)).

To remove it, go to Synaptic and search 2.6.34 and mark all for Complete Removal and then Apply. Make sure you're not in the mainline kernel when you remove it, as that would be bad :)

If you don't want to mess with your mainline kernel, I would contact Stefan Glasenhardt at [email]stefan@glasen-hardt.de[/email] (from [https://launchpad.net/~glasen](https://launchpad.net/~glasen)) and ask him how to install the patch while the mainline is also installed. You might also want to tell him about your issue just so he knows it causes problems for those who use the mainline kernel as a workaround.

OK,I´ve informed Stefan because I didn´t want to uninstall the mainline since it is the only way for me to communicate at this time!Hopefully we will hear from him soon!

---

### Post by James Keating on 2010-05-19
Lucid has been the biggest disaster for me in ten years of using Linux. I am used to having problems, especially with upgrades, but this is the first time I have been unable to boot, even from the CD. I did read the release notes more than once, but I didn't recognize the Intel 8xx problem as relevant to my machine. I really didn't expect such a basic failure on a machine that has worked until now.

My laptop has an Intel 82852/82855 graphics controller. After upgrading to Lucid, booting ended in a frozen black screen. Booting from the CD was the same, but I could boot with the 9.10 CD and fix configuration files. 

Once I got that fixed, thanks to the Ubuntu forums, running any video outside a browser completely froze the machine, requiring a hard reset. Some other programs, like Firefox, would start but immediately hang, leaving trails all over the screen if I moved them. Opera ran OK, and video inside it was fine.

I have tried nearly every kind of suggestion in a number of posts and in the [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) page. A change to GRUB let me boot, and a newer kernel finally stop my machine from crashing whenever I tried to run a video.

If, like me, you can't boot after upgrading to Lucid, and can't boot off a Lucid CD, you need to

A) get a CD for a Ubuntu version before Lucid 10.04
B) change your boot parameters
C) optionally, install a newer kernel that fixes the Intel 8xx graphics problem 

I have tried everything in [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and a number of other suggestions. I have only had success with this method. 

A)
1. Go to the Ubuntu Releases site, [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
2. Choose Karmic or 9.10 and download one of the desktop CD .iso files.
3. Burn its contents to a 700 Mb CD.

B)
Boot from that CD.

You must edit a boot file as root. Nautilus has no options for editing files as root, so you must use commands. 

1. Open a terminal.

2. The easiest way to go from here is to start Nautilus as root with "sudo nautilus" and edit files the usual way, without running each editing command below.

You will need to edit the boot file on your hard drive, not on the CD. The CD makes this confusing, since directories will not be in their usual places.
From the command line, your hard drive will be under /media/(long-nonsensical-name)
From Nautilus, it will show under Places as "106 GB Filesystem" or something.
If you have multiple partitions and there is more than one such listing, find the one that contains your home directory.

3. Navigate to /etc/default on your hard drive

4. Edit the file called grub 
sudo gedit grub
On the line that begins GRUB_CMDLINE_LINUX_DEFAULT, add i915.modeset=1
GRUB_CMDLINE_LINUX_DEFAULT="splash i915.modeset=1"

If your /etc/default/grub doesn't exist, you are using the old Grub. 
In that case, go to /boot/grub/ on your hard drive
and edit the file called menu.lst
There is one line that begins with # defoptions. Add i915.modeset=1"
# defoptions=quiet splash i915.modeset=1

5. Save and run the command 
sudo update-grub

If gedit doesn't work, try another text editor. At the very least, nano should be present (control-o saves; control-x exits).

6. Reboot.

C)
1. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and find the newest directory (I used v2.6.34-rc7-lucid)
2. Download the kernel image and header files
3. Install them from a terminal with the command 
sudo dpkg -i (kernelfilename.deb) (headersfilename.deb)
or run sudo gdebi-gtk
3. reboot and choose that kernel.

---

### Post by glasen on 2010-05-19
Hi,

sasaenator wrote an email to me, to inform me about this thread.

Some explanations to "my" patch :

[LIST]
[*]My DKMS-packages are based on the original patch from the [bug-report]("http://bugs.freedesktop.org/show_bug.cgi?id=27187"). I've only backported it to the Lucid-kernel and wrote a DKMS-package so i could easily install the updated-modules on my hardware.

[*]My DKMS-packages only work with the original Lucid-Kernels. They don't work with kernel version 2.6.32.12+ (Lucid-kernel is based in 2.6.32.11), 2.6.33.x, 2.6.34.x and all above (This means all current vanilla versions). So you have to compile your own kernel (which is btw very easy) to include the patch.

[*]I've made [two patches]("http://glasen-hardt.de/?p=623") for kernel sources 2.6.32.13 and 2.6.33.4. If i find some spare time, i will also port the patch to kernel-version 2.6.34.

[*]The intel-drivers from my PPA could help to improve stability on 855-based hardware but they mustn't. For me, they work nearly perfectly but other people suffer from more crashes when using KMS (Which is needed for driver-version 2.10+) than when using UMS. In most cases it seems that using the DKMS-package and stick to original Lucid-driver (2.9.1) is the best solution.

[*]A newer kernel-version could improve the situation but mustn't. There are enough people out there where an updated kernel doesn't improve the situation. Sometimes it's getting even worse, because newer kernels are specialized to use KMS and not the old UMS-code.
[/LIST]

I hope i could clarify some things. I'm sorry that my blog is mainly written in german. I've written an article some days ago, which explains how to install Lucid on 855-based hardware and i haven't found the time to translate it.

Greetings Stefan

---

### Post by glasen on 2010-05-19
Deleted

---

### Post by glasen on 2010-05-19
Deleted

---

### Post by glasen on 2010-05-19
Deleted

---

### Post by Dragonbite on 2010-05-19
The patch steps I received were summarized as 

summarized from [http://glasen-hardt.de/](http://glasen-hardt.de/)

[list=1][*]**install the 855gm-patched kernel-modules**
[list=1]
[*]include the 855gm-patched kernel-modules ```
sudo add-apt-repository ppa:glasen/libdrm
sudo add-apt-reposority ppa:glasen/855gm-fix
```
[*]update, upgrade repo```
sudo apt-get update
sudo apt-get upgrade
```
[*]install the 855gm-patched kernel-modules```
sudo apt-get install dkms linux-headers-generic 855gm-fix-dkms
```
[*](OPTIONAL) Plymouth to Initial-Ramdisk, repare colour ```
echo "FRAMEBUFFER=yes" | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
```[/list]
[*]**purge the 855gm-patched kernel-modules**
[list=1][*]```
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6_all.deb
```
[*]```
sudo dpkg -i ppa-purge_0.2.6_all.deb
```
[*]```
sudo ppa-purge ppa:glasen/intel-driver
```
[*]```
sudo ppa-purge ppa:glasen/libdrm
```
[*]```
sudo ppa-purge ppa:glasen/855gm-fix
```[/list][/list]

NO WARRANTY!!  I am going to be testing this out at the DACS (computer club in Danbury, CT) Linux SIG meeting tonight!

---

### Post by glasen on 2010-05-19
You've made one error :

```
sudo add-apt-repository ppa:glasen/libdrm
sudo add-apt-reposority ppa:glasen/855gm-fix
```

You'll only need the "855gm-fix"-PPA to install the fixed kernel-modules. The "libdrm"-PPA includes an updated libdrm which is necessary to install the updated intel-driver from the PPA.

If you want to install the updated driver, you also have to include the driver PPA :

```
sudo add-apt-repository ppa:glasen/intel-driver
```

The updated intel-driver is no "must", it's nice to have.

The updated intel-driver works only with KMS and will crash if the kernel is booted without it (i915.modeset=1).

To get around the black-screen-issue you have to use KMS or, when using UMS , you have to use a modified xorg.conf-file with the following content :

```
Section "Monitor"
    Identifier "VGA"
    Option "Ignore" "true"
EndSection
```

These lines tell the Xserver to ignore the external VGA-adapter when initializing the driver. You can't use an external monitor any longer but the crash (Black screen) at startup disappears.

_Additional notes to the package "855gm-fix-dkms" :_

The patch included in the updated kernel modules slows down the graphics performance. In most cases you will only notice that e.g. scrolling in Firefox is somewhat slower. OpenGL and SDL-based applications seems not to be affected.

I've made an experimental package (named "855gm-fix-exp") which disables a function in the patched modules. This functions normally ensures that the cache is correctly written. The function is also the main source for the slowdown. Without this function graphics performance is nearly normal again.

On my notebook the modules with the disabled function work normally. This means it had no crash in two weeks, but i can't insure that it will also work stable on other hardware.

You can test the package but if your hardware is less stable than with the normal package, please stick to the normal package.

If you don't want to fiddle around with the configuration, you can try my custom Live-CD :

[Live-CD of Ubuntu 10.04 with updated Intel-drivers and 855gm-patched kernel-modules]("http://glasen-hardt.de/?p=568")

---

### Post by Dragonbite on 2010-05-19
Thank you for all of your work.  Those of us with this issue, I'm sure, are VERY grateful to not be left out!

My above steps were included in a mailing from [email]541511@bugs.launchpad.net[/email] which I received yesterday, from Thoer, so I am not going to be the only one trying this out I assume.

Just to make sure I have this right, I'll want to

```

## Add repositories
sudo add-apt-reposority ppa:glasen/855gm-fix
sudo add-apt-repository ppa:glasen/intel-driver #(optional)

## Update 
sudo apt-get update
sudo apt-get upgrade

## Install 
sudo apt-get install dkms linux-headers-generic 855gm-fix-dkms 

## use only if using KMS (i915.modeset=1) and is optional
sudo apt-get install intel-drivers
```
And then to get around the black-screen issue, have to use KMS (i915.modeset=1) or if using UMS you have to modify the xorg.conf file with```
Section "Monitor"
    Identifier "VGA"
    Option "Ignore" "true"
EndSection
```

And while this works, there is still some slow-down with things like scrolling in Firefox, which may be remedied by the experimental "855gm-fix-exp".  Is this part of the glasen/855gm-fix PPA?

And then, there is the Live-CD with changes here : [_Live-CD of Ubuntu 10.04 with updated Intel-drivers and 855gm-patched kernel-modules_]("http://glasen-hardt.de/?p=568")

Thank you again for your work, and willingness to correct me here!

---

### Post by glasen on 2010-05-19
> **Dragonbite said:**
> [CODE]## Add repositories
sudo add-apt-reposority ppa:glasen/855gm-fix
sudo add-apt-repository ppa:glasen/libdrm (Needed for intel-driver) <- You forgot this
sudo add-apt-repository ppa:glasen/intel-driver #(optional)

> Is this part of the glasen/855gm-fix PPA?

Yup. There are two packages in this PPA :

"855gm-fix-dkms" and "855gm-fix-exp-dkms"

---

### Post by Dragonbite on 2010-05-19
> **glasen said:**
> Yup. There are two packages in this PPA :

"855gm-fix-dkms" and "855gm-fix-exp-dkms"

Thanks again!

---

### Post by Catharsis on 2010-05-19
First, I'll wholeheartedly echo the thanks for Stefan. He's really gone out of his way to provide support here.

I think I understand the 855gm-fix-dkms patch better now. It doesn't directly patch the kernel, but works more like a package in that it's loaded separately on boot and then interacts with whatever kernel is loaded. So to switch between the default Lucid kernel and the mainline, you'd have to remove it every time you loaded the mainline and reinstall it every time you loaded the default kernel.

For those who care, Daniel Baumann applied the patch directly to the Lucid kernel and uploaded the patched kernel to his PPA:
[https://launchpad.net/~dnjl/+archive/kernel](https://launchpad.net/~dnjl/+archive/kernel)
It'll remove the current -22 kernel and install his patched kernel in its place. The benefit here is that it won't affect the mainline kernel, so you can still try them separately.
To install:
```
sudo add-apt-repository ppa:dnjl/kernel
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by glasen on 2010-05-19
> It doesn't directly patch the kernel, but works more like a package in that it's loaded separately on boot and then interacts with whatever kernel is loaded. So to switch between the default Lucid kernel and the mainline, you'd have to remove it every time you loaded the mainline and reinstall it every time you loaded the default kernel.

This is not entirely correct :

[DKMS]("http://linux.dell.com/projects.shtml") is a tool with allows to build a kernel-module a installation time of a new kernel. With DKMS a developer has not to pack a compiled version of a kernel-module into a package. He only needs to ensure that the source-code compiles cleanly on every commonly used kernel-version. The rest of the work gets done by DKMS automatically. For example VirtualBox uses this technique to update the vbox.ko-module every time a new kernel-version is installed.

My packages do basically the same :

DKMS compiles the modules "intel-agp.ko" and "i915.ko" at installation time of the package and then installs them to the corresponding kernel-modules directory.
Because the two modules only compile correctly with the Lucid kernel, they also only get installed under the kernel-module directory of the Lucid kernel.

If DKMS can't compile the modules for another kernel, it will not stop the whole installation process but continue with the next installed kernel. It will only try to install modules which were compiled without an error (No ko-file, no try to install it)
The newly installed kernel-modules are installed in a separate directory (updates/dkms), so they don't overwrite any original module.
The module-loader in Linux is intelligent enough to load onl< the newest installed modules on startup, so only the updated modules are loaded.

This means :

My PPA-packages don't interfere with an installed mainline-kernel. Because the modules can't compile, they don't exist and therefore don't modify the mainline-kernel.

---

### Post by Catharsis on 2010-05-19
Really cool stuff. I've got it now. Thanks again.

---

### Post by sasaenator on 2010-05-20
> **Catharsis said:**
> For those who care, Daniel Baumann applied the patch directly to the Lucid kernel and uploaded the patched kernel to his PPA:
[https://launchpad.net/~dnjl/+archive/kernel](https://launchpad.net/~dnjl/+archive/kernel)
It'll remove the current -22 kernel and install his patched kernel in its place. The benefit here is that it won't affect the mainline kernel, so you can still try them separately.
To install:
```
sudo add-apt-repository ppa:dnjl/kernel
sudo apt-get update && sudo apt-get upgrade
```

Should I try this from mainline kernel or?7

---

### Post by Dragonbite on 2010-05-20
Last night I ran through the patch process using what I had here as a basis (after correcting the misspelled "reposority" ;) ).

It does work.  I am now able to watch video on my system, though the external monitor signal is all messed up and I cannot turn on desktop effects.  These were known issues.

So it is much more usable, for me, than it was before.

It also seems like the people from Fedora and openSUSE are looking for the patch as Fedora comes out next week and openSUSE in a month or two.

Thanks for all your work glasen.

---

### Post by glasen on 2010-05-20
> Should I try this from mainline kernel or?7 

It's basically the same thing as using the original Lucid kernel and my DKMS-packages. If you want to use other kernel-version and don't want to "mess around" with DKMS, you should try the kernel from the PPA.

**P.S. :**

I've just made a small update to my PPAs :

[Aktualisiertes PPA “intel-driver” / Updated PPA “intel-driver”]("http://glasen-hardt.de/?p=657")

---

### Post by Dragonbite on 2010-05-20
So, if there is a kernel update I will need to run through the whole patch process again?  If so, then I'm thinking of putting it into a shell script to make it easier.

---

### Post by glasen on 2010-05-20
No. That's the cool thing about DKMS-based packages :

When the kernel is updated, DKMS automatically compiles and installs the modules provided by the package. In most cases you don't even notice that the modules are rebuild.

The only thing i have to insure is that my packages work with a new kernel version and upload them to my PPA.

---

### Post by fanum on 2010-05-31
Great work on the patch, works perfectly. Any idea why the desktop effects will not work? I know it is a known issue, but is there a possible work around?

---

### Post by Dragonbite on 2010-06-13
I figured I would try Fedora and see how they handle this issue.

Surprisingly, other than taking 15-20 minutes to boot up, it works!  I had graphical screen, webcam and video playback out of the box! Only thing that doesn't work is Desktop effects, but I can live with that!

So what is so different between the two, and when can Ubuntu line up?

---

### Post by ontwowheels on 2010-06-16
> **glasen said:**
> No. That's the cool thing about DKMS-based packages :

When the kernel is updated, DKMS automatically compiles and installs the modules provided by the package. In most cases you don't even notice that the modules are rebuild.

The only thing i have to insure is that my packages work with a new kernel version and upload them to my PPA.

WELL DONE.  I was FINALLY to get the live CD (USB) to boot using your patched remix.  Is this a concern?

"The only thing i have to insure is that my packages work with a new kernel version and upload them to my PPA."

Will your fixes ever make it into the official Ubuntu repos?

Thanks again.

---

### Post by Dragonbite on 2010-06-18
> **Dragonbite said:**
> I figured I would try Fedora and see how they handle this issue.

Surprisingly, other than taking 15-20 minutes to boot up, it works!  I had graphical screen, webcam and video playback out of the box! Only thing that doesn't work is Desktop effects, but I can live with that!

So what is so different between the two, and when can Ubuntu line up?

From what I've learned, Fedora included the "big hammer patch" (whatever that is).

In Ubuntu, whatever updates have come down the situation is getting better and better.  I now have multi-monitor support and webcam (Cheese) in Ubuntu.  I even have Desktop effects, though I haven't noticed anything different, but it didn't freeze up when tried to turn them on.  We'll see after a reboot.

Does anybody know if any of these patches are going to make it into the 10.04.1 release?  I think that comes out in July and it would be great if these patches make their way into it so we would have a full-functioning CD to burn and use.

I would definitely prefer to not have to worry whether or not people I give CDs out tohave the affected Intel GPU and are going to have a negative experience (and write-off Linux).  I am one of the Linux "ambassadors" to my computer club and just handed out a lot of 10.04 CDs  earlier this month.

For the record, I have used glasen's patch.

---

### Post by joronkamon on 2010-07-30
I have used the experimental patch of GLasen on Amilo Pro V2000 with 82blabla/855GM chip.
It fixed things with blan(c)k screen, but my computer completely hanged 2 times already in less than a day. Well, I have limited experience in LInux, what crash report I can provide? When hangs, it can not enter text console Alt+CTRL+Fx either, only hard reset helps.

My question is, how do I uninstall the experimental patch and try the normal patch(855gm-fix-dkms) instead? 

I have followed instructions on [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes), wchich makes the things more sad because thats official solution and causes unexplainable hangs. Honestly, my first experiences are far from positive, but I need Ubuntu for a software precompiled for it. I expected to be able to work with the system, not debug it for a week.

---

### Post by Catharsis on 2010-07-30
> **joronkamon said:**
> I have used the experimental patch of GLasen on Amilo Pro V2000 with 82blabla/855GM chip.
It fixed things with blan(c)k screen, but my computer completely hanged 2 times already in less than a day. Well, I have limited experience in LInux, what crash report I can provide? When hangs, it can not enter text console Alt+CTRL+Fx either, only hard reset helps.

The bug report containing that patch is [here](http://bugs.freedesktop.org/show_bug.cgi?id=27187) Post a comment with your experiences using it.


> **joronkamon said:**
> My question is, how do I uninstall the experimental patch and try the normal patch(855gm-fix-dkms) instead?

```
sudo apt-get remove 855gm-fix-exp-dkms
sudo apt-get install 855gm-fix-dkms
```

> **joronkamon said:**
> I have followed instructions on [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes), wchich makes the things more sad because thats official solution and causes unexplainable hangs. Honestly, my first experiences are far from positive, but I need Ubuntu for a software precompiled for it. I expected to be able to work with the system, not debug it for a week.

The freezes are not a bug in the patch. They're the original symptom that the patch is supposed to fix. i8xx chips have been freezing unexplainably ever since Jaunty.

---

### Post by joronkamon on 2010-07-30
Thanks for the command help.
I'll try the ordinary patch to see what happens.

Do you know whether the problem with 855 chips persists also in Debian distros? I know Ubuntu superseeds Debian, but it may be still very different experience.

Edit: One question though, when installing the patch the dkms option was used. Why not use it this time with both the uninstall and install commands?

---

### Post by Catharsis on 2010-07-31
> **joronkamon said:**
> Do you know whether the problem with 855 chips persists also in Debian distros? I know Ubuntu superseeds Debian, but it may be still very different experience.

I do not, sorry.

> **joronkamon said:**
> Edit: One question though, when installing the patch the dkms option was used. Why not use it this time with both the uninstall and install commands?

'dkms' wasn't an option, it was another package that you installed. You installed the 'dkms' package and the '855gm-fix-dkms-exp' package.

---

### Post by joronkamon on 2010-07-31
Is there any reason why the Window manager justs shuts off? I watched a movie, it stoped in the middle, all the windows headers (the bars above the windows, with the close, max and minimize buttons) dissapered from all windows, and when I clicked the 'show desktop' icon, it bailed: "Can not show desktop because there is no window manager running"? This happens erratically, sometimes without anything special that I do.

Just a clue where to look and what to patch. (This all happens with the non-experimental patch, with the experimental the system hangs and window problems are still present).

If I restart the window manager will it solove the problem? How do I do that without reboot?

Are these problems common with Linux, or I've messed up something as a newbie (though I don't see what, it is just fresh install on 3 days)

---

### Post by joronkamon on 2010-07-31
So, any advice as how to change/configure my window manager, so it doesn't crash?

Meanwhile, I have found that Intel provides driver support for the 82xxx here:
[http://downloadcenter.intel.com/detail_desc.aspx?agr=N&Inst=Yes&ProductID=922&DwnldID=8211&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/detail_desc.aspx?agr=N&Inst=Yes&ProductID=922&DwnldID=8211&strOSs=39&OSFullName=Linux*&lang=eng)

It is in .rpm, so should be converted into .deb using *alien, *for example. Has anybody actually tested this solution from Intel? Shall I try it, or it is that solution which is originally included in the UBUNTU distro and the Glasen patch (855gm-fix-dkms) tries to fix? I'll appreciate very much any response on that. My ubuntu distro is really useless with all these window manager crashes, without or with any of the two patches.

---

### Post by Catharsis on 2010-07-31
That file is already included in Ubuntu. It's just the Intel driver.   

So some ground to cover: 
 1) This is not a bug report. It is a support forum. Please see the bug reports for providing feedback.
2) i8xx cards have been very buggy for years; it's not your fault. There are some radical patches in the works for Maverick that I'll probably post around for greater awareness later this week when I get time.

---

### Post by jorkolino on 2010-10-11
> **Catharsis said:**
> ....
Just make sure you also change
```
	Driver		"fbdev"
```
to
```
	Driver		"intel"
```
in the "Device" section.

WHen I changed that upon reboot the system complained and entered into safe mode. it is not stable with "intel", or I am missing something? (with fbdev the performance is slugish, but stable)

Meanwhile, any news on whether Ubuntu 10.10 is stable with 855 chipset?

---

### Post by kumaryu on 2010-10-11
I had a similar issue with a Thinkpad X40 with Intel 855GME chipset. Its a known issue w/ Lucid.

**X/Bugs/Lucidi8xxFreezes:**
X freezes (GPU lockups) are being experienced on i845, i855 and other 8xx chips.
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)


The first method, "GTT Incoherency Patch" worked for me.

---

### Post by kumaryu on 2010-10-11
Oops, didn't realise this was already discussed... :oops:

---

### Post by jorkolino on 2010-10-12
> **kumaryu said:**
> ....


The first method, "GTT Incoherency Patch" worked for me.

Did it work for you in the long run? When I tried it a month ago, it allowed me to boot and work for some time, but it was crashing intermittently, sometimes w/o any input from me (i.e. i watch a movie and bang). Is it stable?

---

### Post by Superkuh on 2011-08-22
Sorry to revive this slightly old thread, but I have a Toshiba Satellite 5105-S607 I'm trying to install xubuntu 10.04 32bit on. It has a Geforce4 440 video card.

Default booting of the live CD led to the screen slowly fading to blank white during the boot splash. This was bypassed by setting 'nomodeset' in the boot parameters. 

Unfortunately now when it does finish booting and start X the screen simply switches to blank black.

Other than setting the boot paramter nomodeset (since it's nvidia), what can I do to get X to work?

[edit] I burned an ubuntu (instead of xubuntu) liveCD and it worked with nomodeset. I guess it's an xubuntu thing. Nevermind.

---

