---
title: "Multi-Monitors: Can ATI + Nvidia Video Cards Co-Exist?"
date: 2011-04-08
forum: General Help
---

### Post by CyborgNinja111 on 2011-04-08
Hi Everyone,

As described in further detail below I am looking for some help in Ubuntu 10.10 with a multi-monitor + multi-gpu setup using both ATI and Nvidia video cards installed within the same system (que scoffs and jeers).

Any help and patience will be appreciated. Also, if/when replying to me please pretend you're talking to a total Linux/Ubuntu NooB with a hot wife who hates me. In fact, don't pretend. 

Go easy. 

**My question: **

*Is it possible to sucessfully run both ATI and NVidia GPU's and Drivers simultaneously in Ubuntu 10.10 (think multi-monitor environment)?*

I am asking b/c I am having trouble figuring out how to manage my video cards - particularly ATI - within a multi-monitor + multi-gpu video card environment.

Here's the setup:


[LIST]
[*]Ubuntu 10.10 Maverick Meerkat
[*]x2 - NVidia 6800XT SLi GPU's + 2 DVI outputs/per card [SIZE=1](Serviceable card for my needs)[/SIZE]
[*]x1 - ATI Rage XL PCI Card + 1 VGA output ([SIZE=1]Yes, ancient hardware...I know)[/SIZE]
[*]x5 - LCD Monitors
[*]Xinerama Enabled[SIZE=1]*[/SIZE]
[/LIST]
[SIZE=1]*Compiz can/will not be enabled under the array  (unless divided by two's through each 6800XT using   twin-view) as I am aware of the  compositing confict with Xinerama - but that's a whole other subject.[/SIZE]

**The Theory:**

I am shooting for maximum screen real estate here. In this case, using a total of 5 lcd monitors for some major ADD-induced tangents, gambling and watching loads of Cytheria girl-on-girl pr0nz - you know, the normal daily things we use our pc's for! =D>8-[

**My Problem(s):**

**Installation:**

Initial installation of Ubuntu 10.10 (USB Pendrive via Universal USB Installer) will HANG or FREEZE very shortly after the installers Main Menu and selecting the option: 'Install Ubuntu onto Hard Disk...'

The install will 'freeze' at a wall of text while *presumably* attempting to install/initialize the Nvidia nouveau drivers - not entirely sure here; only speculation as the word 'nouveau' is plastered all over this wall of text when the install freezes.

I've also attempted a CD install to no avail. The install freezes @ a splash screen.

My Noob workaround for the freezing? Removed both Nvidia 6800XT GPU's before doing the USB install. The Ubuntu installation then proceeded perfectly with the ATI Rage XL PCI card installed and connected to one monitor. 

I know this probably isn't the best way of getting around the freeze so I would appreciate a real solution if any exist for this problem. 

Solutions?

**Nvidia Drivers + 4-Monitor Array:**

Following the succesfull installation of Ubuntu, I shutdown the pc and re-installed both 6800XT cards just to see if Ubuntu would *accept* the Nvidia cards (as if adding/upgrading with new hardware) and do it without freezing while loading the desktop. Also thinking that if Ubuntu did indeed load that maybe I could force the drivers to install either automatically or manually.

**Result: **No success. Ubuntu would Hang during startup at a black screen with a flashing cursor. There was output from the BIOS through the ATI card only followed by the black screen and cursor. There was no output from the Nvidia cards.

Next, I tried connecting only a *single* Nvidia 6800XT card. The ATI Rage XL card also remained installed. I connected two additional monitors to the single 6800XT and Ubuntu started just fine and to my surprise with one monitor initialized from the 6800XT card. There was no output from the ATI card. Note: "At this time "PCI-e" was selected to initialize first within the BIOS.

At this point, I believed that since I was getting an output from the Nvidia card then I must have been using an open-source driver. I am unsure as to whether this driver was auotmatically detected and enabled by Ubuntu or if I the driver being used was for the ATI card and it somehow functioned with the Nvidia card - clarify? 

I attempted to 'manage' the two monitors connected to the single 6800XT under System > Preferences > Monitors but to no avail. Where I expected 2 monitors to appear available there was only one. Detect displays did not detect any new monitors.

The next move was to try the proprietary drivers. I download the Additional Nvidia Proprietary drivers (Version 173). Restarted and...

**Result: **No dice. The Nvidia X Server Settings app did not show up under System > Administration. Without the Nvidia App I had _no_ way of enabling and configuring any of 6800's - at least to my limited knowledge.

So, I then downloaded the (version current) Nvidia drivers, restarted the system and then...[B]

Result: [/B]*Success!* The NVidia X Server app installed. At this time, I shutdown  Re-installed the 2nd 6800XT card and connected both cards using the SLi  bridge connector. Connected 4 monitors to the 6800's and the Ubuntu started up perfectly without a hitch; both cards were recognized within the Nvidia X Server App.

Using the Nvidia X Server Settings I managed to enable and succesfully setup a 4-monitor array using both 6800XT cards with Xinerama enabled. I am able to move windows across all 4 monitors just the way I would like.

Now the dilemma...

**ATI Drivers + the 5th Monitor:**

This is where I am at a stand-off. The Nvidia cards work perfectly but the ATI Rage card now no longer outputs to a desktop. It's as if it was disabled altogether.

I've gained some progress when within the BIOS I've changed and enabled 'PCI' to initialize first (as opposed to 'PCI-e'). The ATI card does indeed initialize during the BIOS check all the way up to the purple Ubuntu splash screen. At this point, the 4-monitor Nvidia array 'goes green' and initializes with the logon screen. However, the ATI connected monitor displays a solid purple screen only - _NO_ desktop, wallpaper, logo, cursor, text, etc. Strange.

Is there some sort of conflict when using a combination of ATI *and* Nvidia cards within Ubuntu? Do you have to use one or the other when using multiple-gpu's for multi-monitors?

I can confirm that the 'ATI r128' Rage-Specific drivers were downloaded at installation. I can also confirm that 'lspci' shows both sets of Nvidia cards and the ATI card:

02.00.0 VGA compatible controller: nVidia Corporation NV42 [GeForce 6800XT] (rev a2)
02.00.0 VGA compatible controller: nVidia Corporation NV42 [GeForce 6800XT] (rev a2)
06:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

However, there seems to be no mention of the ATI card within xorg.conf and probably b/c itself was generated by the Nvidia app. 

My next approach was to download the ATI equivalent of the Nvidia app (I guess) which is the ATI Catalyst software. I figure this would finally give me control over the ATI Rage card. The software installed but I cannot seem to locate it under any menu. I also tried accessing System > Preferences > Monitors and get the message: 'RANDR is not present.'

**At this point...**


[LIST]
[*]Can ATI and Nvidia drivers + cards co-exist under Ubuntu?
[*]If so, how do I enable and manage the ATI Rage XL Card and enable the 5th monitor?
[*]Am I limited to using 4-monitors under these circumstances?
[*]I am willing to re-install Ubuntu especially if there is a viable workaround to the freezing as mentioned early post.
[*]I'll be happy to upload the xorg details at request.
[*]I am willing to forget the whole thing ever happened and go back to watching Cytheria on Windows. I just won't be as happy there as I would here in Ubuntu land.
[/LIST]
Thanks in advance for the help and the patience (especially w/ the sarcasm)!

---

### Post by C.S.Cameron on 2011-04-08
I once tried getting both Nvidia and ATI drivers working on the same computer, back around 8.04 or 8.10.
I could not even get proprietary drivers working with a persistent, (usb-creator), install.
I then tried with a full install to pendrive, no problem with either Nvidia or ATI, but not both.
I then found "switchconf" in the repositories.
This would allow me to choose between a variety of xorg.conf files at boot.
I could choose to load for my big screen tv, Dual screens, etc.
I could choose to load either proprietary or generic drivers but I could not install Nvidia and ATI at the same time.
I tried everything, even hand installing the individual files to the appropriate folders, (that was a huge time consuming mess).
Nowadays xorg.conf does not even load video files at startup so switchconf is not working for video.
Good luck, I will be following this thread just in case there are any other responses.

---

### Post by CyborgNinja111 on 2011-04-09
> **C.S.Cameron said:**
> I once tried getting both Nvidia and ATI drivers working on the same computer, back around 8.04 or 8.10.
I could not even get proprietary drivers working with a persistent, (usb-creator), install.
I then tried with a full install to pendrive, no problem with either Nvidia or ATI, but not both.
I then found "switchconf" in the repositories.
This would allow me to choose between a variety of xorg.conf files at boot.
I could choose to load for my big screen tv, Dual screens, etc.
I could choose to load either proprietary or generic drivers but I could not install Nvidia and ATI at the same time.
I tried everything, even hand installing the individual files to the appropriate folders, (that was a huge time consuming mess).
Nowadays xorg.conf does not even load video files at startup so switchconf is not working for video.
Good luck, I will be following this thread just in case there are any other responses.

Thank you for the Feedback and for detailing your experience in trying to run both ATI and Nvidia drivers. It's good to know that I am not alone in the fight. And 'wow...' installing those drivers by hand deserves big ups +100pts for persistence!

Getting ATI, Nvidia and Ubuntu living in harmony seems like a long shot, no? I bet there's plenty of us out there that are trying to accomplish this same feat. 

So what it is all of you Linux/Ubuntu veterans? Who's got the magic beans? 

We await your wisdom...

---

### Post by aj7360 on 2011-04-24
Heck... I can't even get two nVidia cards to work together under 10.04 even though they were working fine with 9.04 (I think) using the 173 drivers.

Might be a good reason to try Windows 7, then run Ubuntu in a Virtual Box vm.

But no... I want linux and have my weather station software (the linux version sux) running in an XP vm. 

I too am puzzled by the lack of replies. 

Guess it can't be done.

---

### Post by 3Miro on 2011-04-24
The prop Nvidia driver does not coexist with other drivers (it does some strange things). The prop Nvidia drivers even conflicts with the FOSS Nvidia driver (sometimes). I am not sure about ATI, they may behave better, but Nvidia will break things for sure.

In order to get anything meaningful with Nvidia, you do need the prop driver, so my guess is that you have to get another Nvidia video card. 

The FOSS Nvidia driver has been improving a lot, so in 11.10, you may be able to get the three cards working together.

---

