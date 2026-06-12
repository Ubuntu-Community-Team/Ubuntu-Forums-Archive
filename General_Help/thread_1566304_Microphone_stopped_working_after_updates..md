---
title: "Microphone stopped working after updates."
date: 2010-09-02
forum: General Help
---

### Post by PaddyWangTheGG on 2010-09-02
Hi guys,

Very strange, my microphone was working two days ago. But after installing some updates, it stopped working. I didn't really check what updates it was tho. Just the update manager asked me to update, so I did so. I tried many solutions on the forum, but none worked. 

Many thanks.

---

### Post by PaddyWangTheGG on 2010-09-07
It has been nearly a week. My microphone is still not working. In my sound preferences--> input--> input level, shows it captures something. Because the bars keep moving up and down. So i presume there is input sound. But when I tried to use sound recorder to test it, it did not record anything but some sort of noise. Please help!

Many thanks!

---

### Post by hrafninn on 2010-09-07
It seems that I have the exact same problem.  I'm running Ubuntu 10.04 on a Dell Precision M4300 with a HDA Intel sound card, chip SigmaTel STAC9205.

Sound is generally working fine except that I cannot record sound, neither with the sound recorder nor with say recordMyDesktop.

I tried [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) without success.  After upgrade I have:
# ALSA Version

# Driver version: 1.0.23

# Library version: 1.0.23

# Utilities version: 1.0.23 

Any ideas to try?

---

### Post by baddnady23 on 2010-09-07
Is your mic built in or is a USB connection?

---

### Post by hrafninn on 2010-09-07
My mic is built in.

I just installed linux-backports-modules-alsa-lucid-generic and now I can capture (both sound recorder and recordMyDesktop work) :p  However, the recording is very "noisy".

---

### Post by supermario641996 on 2010-09-07
This was a for now fix for my microphone.First and I mean first go to sound preferences and then input and set the bar at 100% then  get alsa mixer from ubuntu software center then open it and all the way on the right were it says capture, there sould be a vertical and a horizontal slider bar.  slide the horizontal bar all the way to the right.  The microphone will be a little crackly but it worked for me and I have the same microphone.

---

### Post by PaddyWangTheGG on 2010-09-07
> **supermario641996 said:**
> This was a for now fix for my microphone.First and I mean first go to sound preferences and then input and set the bar at 100% then  get alsa mixer from ubuntu software center then open it and all the way on the right were it says capture, there sould be a vertical and a horizontal slider bar.  slide the horizontal bar all the way to the right.  The microphone will be a little crackly but it worked for me and I have the same microphone.

Thanks for the suggestion. I did what you said, but no luck. It's still not working. While searching for all sort of the solutions, I found a page which shows alsa supported sound card lists.
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA](http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA)
My sound card is VIA VT2020, which is not on the list. Is that why my microphone is not working? But the funny thing is my microphone was working before the update.

---

### Post by hrafninn on 2010-09-08
> **hrafninn said:**
> My mic is built in.

I just installed linux-backports-modules-alsa-lucid-generic and now I can capture (both sound recorder and recordMyDesktop work) :p  However, the recording is very "noisy".

I'm afraid I announced victory to soon:(

Now suddenly, I have the same problem again, i.e. can't capture sound. The annoying problem is that I have no idea why it worked yesterday (after the linux-backports-modules-alsa-lucid-generic install) but not today.

---

### Post by hrafninn on 2010-09-08
After some searching I executed Step 4 of this guide: [URL="https://help.ubuntu.com/community/SoundTroubleshootingProcedure"]
https://help.ubuntu.com/community/SoundTroubleshootingProcedure
[/URL]

Result: Microphone works again!

Can anyone tell me why?

---

### Post by cespinal on 2010-09-13
bumping this.....heck... I got the feeling I was pulled back to Hardy Heron...

Mine is an hpdv9000, internal mic not working after some updates. Even made a fresh install and things led me nowhere. I have to say I opened my laptop to change the broken hinges, I was afraid that I should have severed some cable but that's highly improbable since the webcam, which runs trhough the same path as the mic, runs perfectly. 

Here is the output of my Alsa dmesg: 
[   19.202488]   alloc kstat_irqs on node 0
[   19.202500] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   19.202503] hda_intel: Disable MSI for Nvidia chipset
[   19.202553] HDA Intel 0000:00:07.0: setting latency timer to 64
[   21.362166] vboxdrv: Trying to deactivate the NMI watchdog permanently...
--
[   21.654991] ppdev: user-space parallel port driver
[   21.670191] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   29.430031] eth1: no IPv6 routers present

I'm gonna try the backports thingy.... wish me luck :P

Update: intalled alsa backports. Managed to record some sounds but everything sounds very low and noisy. At least I can confirm that my mic has not been damaged. 

sigh....got tired of clapping in front of the mic...

---

### Post by supermario641996 on 2010-09-21
[http://ubuntuforums.org/showthread.php?t=1461287](http://ubuntuforums.org/showthread.php?t=1461287)

This was a fix for the same sound card that was working funny.

---

### Post by cespinal on 2010-10-09
Thanks pal... but Im still totally stuck... I starting to thing my internal mic could have been physically damaged...

---

