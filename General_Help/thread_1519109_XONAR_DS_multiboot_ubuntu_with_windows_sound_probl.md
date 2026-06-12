---
title: "XONAR DS multiboot ubuntu with windows sound problem[BUG] NEED FIX!!!!!!!!!!!!!"
date: 2010-06-27
forum: General Help
---

### Post by Ranger21 on 2010-06-27
So I just installed Ubuntu 10.04 and set up ALSA and got my DS working perfectly.

I booted back into Windows with the intention of playing some BC2, and discovered anytime sound tries to play, it's all screwed (I can still make out some of what is being said but it's pretty bad). Naturally my first reaction would be to go into the Xonar audio center, which I did, and made sure nothing was wrong there. I changed settings around (sample rate and changing from headphone to 2 channel) but nothing worked. Turned off the D3SD GX and that didn't work either. Removed the drivers, rebooted, reinstalled, rebooted. No change.

One thing I noticed is under the Windows sound control panel it doesn't show I'm playing anything when I am. However when I go into advanced and use the test option (and set it to the highest option available) it sounds fine.

Under Ubuntu it also sounds fine. I've got volume set to around 50% in Ubuntu. I noticed when I muted it under Ubuntu and rebooted it was muted under Windows, hence my thought that the volume settings were messing things up. Didn't work though.

Pulled the card out and left it out for a few minutes worked. Quite strange.

It's a rip off of post from there [http://hardforum.com/showthread.php?t=1514124](http://hardforum.com/showthread.php?t=1514124)

This is the only thing which keeps me from using of UBUNTU!

Im using Windows 7 64 bit!

---

### Post by uberlube on 2010-08-18
i can confirm this problem with my xonar DS and win 7 / ubuntu dual boot, and uuuuuugh to that gawd aweful noise it makes after you boot windows with it after using ubuntu. i also hear a weird clicking noise coming from the card when i boot the computer now, this didnt happen when it was just booting into windows. so anyways ya this device needs better support or there is a major bug in the new alsa 1.0.23

---

### Post by manjiboy on 2010-08-20
Am having the same problem, help!

---

### Post by w1ntermute on 2010-08-23
I can also confirm I am having this issue.

The sound in Windows now is INCREDIBLY loud no matter what setting I have the system volume at, and is incredibly distorted and fuzzy (I jumped 6 feet in the air when I had my headphones on the first time I experienced this!)

I can also hear clicking coming from the card now too.


I vaguely remember hearing clicking when tinkering with some of the channels in alsa-mixer, so I will tinker and experiment and see if any of these settings are interfering with the card in some way.

---

### Post by chronozphere on 2010-08-26
Having exactly the same issue here. :cry:

After I booted windows, the sound was all messed up. What I noticed was that only the front-left and front-right channels were messed up. The rest still sounded ok.

I'm quite suprised by the fact that this could be caused by a dual boot. The two OSses should have nothing to do with eachother. I'm running Win7 32bit and Ubuntu 9.10.

I believe that hearing clicks in alsa-mixer is not something to worry about. I know my card clicks when I change my input device from mic to line-in or back (not 100% sure whether this is normal).

I recieved my Xonar DS yesterday, so I can still get a refund (unless a hero with a fix appears ofc).

Edit: The problem only occurs when you quit ubuntu, restart and boot right into windows. AFAIK Audio is good when you shutdown and boot again manually.

Edit: The computer seems to remember some settings from the last ubuntu run, when booting into windows. If I mute the sound in ubuntu, I can't get it to work in windows. Complete silence, no matter what I try. Just rebooting windows fixes the issue.

I suspect it's ALSA getting messy with the sound card. :?

Update: I contacted the author of the Xonar driver. He said that the windows driver doesn't properly reset the card when it loads. Nevertheless he will take a look at the issue. :D

---

### Post by w1ntermute on 2010-08-27
You're a lifesaver chronozphere. I have no idea why I didn't try this before!

Thanks, I can finally use my Windows install to play Quake again! Hopefully a fix to the drivers will be released soon though.

And, just maybe, some working ATI drivers!

---

### Post by chronozphere on 2010-08-31
Hey guys, good news:

Clemens Ladisch, the author of the ALSA driver emailed me a patch to fix the dual-boot issue. I can now reboot from Ubuntu into Windows without having sound issues. :D

He said the following about the fix:[INDENT]*The reboot fix will go into the stable kernel series, so it should*
* eventually show up in some kernel update.*

[/INDENT]If some of you don't want to wait for that, I can post some details on how to apply the patch. Just shout. :)

We are now working out front panel support for the headphones. 

Take care. ;)

---

### Post by dld on 2010-09-06
I have just learned about the "power down, boot to Windows" workaround of the Ubuntu Xonar DS driver to Windows driver problem.  But a fix to the Ubuntu driver would be much better.  Care to post it?   Or send me an e-mail?   Use [email]dldietmeyer@charter.net[/email].

---

### Post by chronozphere on 2010-09-07
Hi everyone,

I'll explain how to fix the driver. 

What you need:

> Some "updated" source files (attachement)
> The ALSA update script (It's [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")). It's a good idea to read the instructions of the script first.

**Warning**: By using the alsa update script, your version of alsa will be out-of-sync with the package-manager. For more info, see the thread of the update script.

**Warning: Use at your own risk!** The fixes will eventually be released officially. If you mess something up, you can try to restore alsa by doing  everything again (except step 2). This'll give you a clean ALSA 1.0.23  install.

Instructions:

Step 1: Download the script and run it with the -d option. This will download the files for the latest alsa release (this should be 1.0.23). "cd" to the download directory and do:

```

sudo ./<alsa update script name here> -d

```Step 2: Now copy the files to their place. The files are attached in an archive. 

Kconfig must be copied into /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/ and
the other files must be copied into /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/.

Note: On my PC /usr/src/alsa/ doesn't exist. Instead I have /usr/src/Alsa-1.0.23/

Note: It's a good idea to make backups of the files you are going to replace. Rename the files to <filename>.bak or something. Again, using this fix is at your own risk.


Step 3: Now you can compile alsa by running:
```

sudo ./<alsa update script name here> -c

```That'll take a while. ;)

Step 4: Finally install the new alsa version:
```

sudo ./<alsa update script name here> -i

```Step 5: Reboot. 

This patch should fix the dual boot bug and should also enable front panel support for your headset. ;)

Hope this works for you!

**Update:** The previous version didn't work correctly. The new version does solve the problem for me. As a bonus, you get HDA frontpanel support and better stereo upmixing (A two-channel source will now be played through sub/center aswell). :D

---

### Post by dld on 2010-09-08
Chrono,  It did work!!  Thank you very much.  I don't know anything about front panel support or stereo  mixing though.

---

### Post by Ranger21 on 2010-09-18
Wow! I thought this topic is dead. 

In which one stable release of kernel we can wait full support of  "errorless" dual-boot and front-panel for headphones?

When this done, i will use mine ubuntu-based linux system a lot more than now. Because linux have some great sides for me, which one windows7 doesn't have.

---

### Post by Ranger21 on 2010-09-19
Is there anyway to enable front panel microphone? I need to use skype with my headsets:D 

Frontpanel sound works fine.

---

### Post by chronozphere on 2010-09-19
> **Ranger21 said:**
> Wow! I thought this topic is dead. 

In which one stable release of kernel we can wait full support of  "errorless" dual-boot and front-panel for headphones?

When this done, i will use mine ubuntu-based linux system a lot more than now. Because linux have some great sides for me, which one windows7 doesn't have.

I don't know in which kernel the updates will be included. srry.

> 
Is there anyway to enable front panel microphone? I need to use skype with my headsets:grin: 

Frontpanel sound works fine. 	


It should work when you install this fix. If it doesn't, please take another carefull look at the alsa settings. In the capture section, there is a "Front mic" switch, which you must enable. Also make sure that the input level is high enough.

Hope this helps. ;)

---

### Post by Ranger21 on 2010-09-20
Yes, i have front mic and have sound input on max and red dot.

But i think it's a bug of skype.

Also when i load firefox (youtube) i can't hear music in exaile player and i can't hear sound in skype. 

I installed fix.

---

### Post by chronozphere on 2010-09-21
You should test with recording software like Audigy. There's also a cool command that allows you to test alsa's recording capabilities but I forgot it. Just search the forums. ;)

---

### Post by Ranger21 on 2010-09-25
Yay, everything works fine, i use mix of pulseaudio with Firefox, Skype, Exaile , but Audacity uses different way of playing, so don't work.
I think it's just need pulseaudio plugin, like for flash :)

---

### Post by Ranger21 on 2010-10-04
Mic doesn't work normally. Very bad :(

---

### Post by Ranger21 on 2010-10-05
New kernel in ubuntu 10.10 doesn't fix this problem. ;( And can't install this patch

---

### Post by Ranger21 on 2010-10-11
Any ideas?

---

### Post by dino99 on 2010-10-11
have you installed 2.6.36 kernel and use the edgers ppa ? Maybe time to fill a bug report if not yet done.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Ranger21 on 2010-10-11
Edgers for what? I installed 2.6.36 rc7 and nvidia xorg couldn't startup, loading only console-mode.

And i'm not sure that 2.6.36 kernel include fix which Chronozphere posted here on first page.

---

### Post by Ranger21 on 2010-11-03
Anything new? Guys

---

### Post by chronozphere on 2011-01-02
I'm happy to say that this works on 10.4 aswell. :) I did download a fresh set of files, then added the patch and compiled/installed. Works fine here!

---

### Post by n0fxk03 on 2011-01-23
> **chronozphere said:**
> Hi everyone,
 
I'll explain how to fix the driver. 
 
What you need:
 
> Some "updated" source files (attachement)
> The ALSA update script (It's [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")). It's a good idea to read the instructions of the script first.
 
**Warning**: By using the alsa update script, your version of alsa will be out-of-sync with the package-manager. For more info, see the thread of the update script.
 
**Warning: Use at your own risk!** The fixes will eventually be released officially. If you mess something up, you can try to restore alsa by doing everything again (except step 2). This'll give you a clean ALSA 1.0.23 install.
 
Instructions:
 
Step 1: Download the script and run it with the -d option. This will download the files for the latest alsa release (this should be 1.0.23). "cd" to the download directory and do:
 
```

sudo ./<alsa update script name here> -d

```Step 2: Now copy the files to their place. The files are attached in an archive. 
 
Kconfig must be copied into /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/ and
the other files must be copied into /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/.
 
Note: On my PC /usr/src/alsa/ doesn't exist. Instead I have /usr/src/Alsa-1.0.23/
 
Note: It's a good idea to make backups of the files you are going to replace. Rename the files to <filename>.bak or something. Again, using this fix is at your own risk.
 
 
Step 3: Now you can compile alsa by running:
```

sudo ./<alsa update script name here> -c

```That'll take a while. ;)
 
Step 4: Finally install the new alsa version:
```

sudo ./<alsa update script name here> -i

```Step 5: Reboot. 
 
This patch should fix the dual boot bug and should also enable front panel support for your headset. ;)
 
Hope this works for you!
 
**Update:** The previous version didn't work correctly. The new version does solve the problem for me. As a bonus, you get HDA frontpanel support and better stereo upmixing (A two-channel source will now be played through sub/center aswell). :D
 
 
:KS  dual boot bug is solved
[[FONT=Calibri][SIZE=3][COLOR=#0000ff]http://ubuntuforums.org/showthread.php?p=10390759#post10390759[/COLOR][/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?p=10390759#post10390759")

---

