---
title: "Black Screen After Install"
date: 2010-07-28
forum: General Help
---

### Post by rypicken on 2010-07-28
I just got done installing Ubuntu on a new harddrive and set it up to dual boot with grub loader. However, when I boot into Ubuntu, the screen goes black. I can however login (blind) by hitting enter and typing password. The login sound goes and it logs in, however, the screen stays black. I am running a NVIDIA Quadro NVS 295 Video Card. Any suggestions?

Thanks

---

### Post by rypicken on 2010-07-28
I just finished installing a copy of Ubuntu on a new harddrive. Going to dual boot using grub loader between windows and Ubuntu. However, after the install completed, I restart and choose Ubuntu and it will only display black screen. I can log in however, by pressing enter and typing password and then the boot sound comes through speakers. I believe this is probably a problem with graphics driver but not sure. Running a NVIDIA Quadro NVS 295 vid card on an Intel Xenon processor.

Thanks for any help

---

### Post by philinux on 2010-07-28
> **rypicken said:**
> I just finished installing a copy of Ubuntu on a new harddrive. Going to dual boot using grub loader between windows and Ubuntu. However, after the install completed, I restart and choose Ubuntu and it will only display black screen. I can log in however, by pressing enter and typing password and then the boot sound comes through speakers. I believe this is probably a problem with graphics driver but not sure. Running a NVIDIA Quadro NVS 295 vid card on an Intel Xenon processor.

Thanks for any help

Does the desktop work as normal once you're logged in.

---

### Post by rypicken on 2010-07-28
Possibly? lol i can't see anything so I'm not sure. Screen is completely black.

---

### Post by philinux on 2010-07-28
> **rypicken said:**
> Possibly? lol i can't see anything so I'm not sure. Screen is completely black.

So that means no it doesn't.

Is this a clean install, and you've not installed any graphics driver.

---

### Post by davidmohammed on 2010-07-28
suggest - press e to edit your grub.

find the line with quiet splash

remove quiet splash and boot.

do you see any errors?

other boot options you can use 

nomodeset
noapic
nolapic

i.e.

add one or more of these BEFORE quiet splash

---

### Post by rypicken on 2010-07-28
Correct. Clean install from the downloaded ISO burned to a CD.

---

### Post by philinux on 2010-07-28
> **rypicken said:**
> Correct. Clean install from the downloaded ISO burned to a CD.

I'm assuming this install is 10.04 lucid lynx?

When you ran the live cd did you check it for defects? It's one of the menu options. Mind you you have to hit any key as soon as the graphics appears to get the full menu options.

Ok one thing to try. Reboot and at grub select the recovery mode option. This will take you to a command line.

Use this command
```
sudo apt-get install nvidia-current
```

Then

```
sudo reboot
```

---

### Post by sikander3786 on 2010-07-28
> **rypicken said:**
> I just got done installing Ubuntu on a new harddrive and set it up to dual boot with grub loader. However, when I boot into Ubuntu, the screen goes black. I can however login (blind) by hitting enter and typing password. The login sound goes and it logs in, however, the screen stays black. I am running a NVIDIA Quadro NVS 295 Video Card. Any suggestions?

Thanks

Hi.

This is a known problem with the open source drivers for NVIDIA. Boot into Ubuntu the way davidmohammed has mentioned above. Once you install the proprietary drivers, you'll be able to login normally.

And you just need to remove "Quite Splash" and adding "nomodeset" instead.

---

### Post by rypicken on 2010-07-28
Still displays black screen even in recovery mode. Going to download ISO and create another CD and run check and try reinstalling. See if that fixes the problem.

Thanks

---

### Post by philinux on 2010-07-28
> **rypicken said:**
> Still displays black screen even in recovery mode. Going to download ISO and create another CD and run check and try reinstalling. See if that fixes the problem.

Thanks

Dont forget the md5sums and burn at 4x no faster.

---

### Post by lpcustom on 2010-07-28
I highly doubt it's a bad install since everything went through without a hitch. You're issue is video driver related.

I have this same problem anytime I install Ubuntu. You may want to try the legacy driver. I like compiz effects just as much as the next guy but it shouldn't be enabled by default even if the detected card can support it. This is what happens.

---

### Post by philinux on 2010-07-28
> **lpcustom said:**
> I highly doubt it's a bad install since everything went through without a hitch. You're issue is video driver related.

I have this same problem anytime I install Ubuntu. You may want to try the legacy driver. I like compiz effects just as much as the next guy but it shouldn't be enabled by default even if the detected card can support it. This is what happens.

He's got a totally black screen at GDM and after loggin on. And he's got a totally black screen in recovery mode. Not easy to install anything in that situation. Could be the nouveau driver doesn't work well with that card.

His card is fairly new so nvidia-current would be the appropriate driver if it could be installed. Maybe a chroot from the livcd might sort it.

---

### Post by stinkeye on 2010-07-28
I was just reading this in one of my ubuntu feeds.
Worth a try.

> The NVidia graphics black screen install issue
There have been some cases where using particular NVidia graphics cards have lead to black screens (or out of sync) problems when trying to run the live CD or installing Ubuntu. There is a way around this. Here are the steps:
At the startup of the installation screen hit F6 and select nomodeset and install as usual.
Upon first boot (after installation) press the “e” key when you see the GRUB bootloader.
Delete quiet and splash from the boot command and add nomodeset.
Hit <Ctrl>x to save and boot.
Now, once booted,  you need to add the NVidia proprietary driver by doing the following:
1. Click System > Administration > Hardware Drivers.
2. Select the proprietary driver that is recommended to you.
3. Upon completion, reboot your machine and your graphics should look great.

---

### Post by philinux on 2010-07-28
Stinkeye,
nomodeset could well be it.

---

### Post by cariboo on 2010-07-28
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by rypicken on 2010-07-28
Sorry about the repost. Was not sure which board was appropriate for this topic. Will try these ideas and see what happens. 

Thanks for the advice!

---

### Post by elfbj97 on 2011-06-15
> **philinux said:**
> I'm assuming this install is 10.04 lucid lynx?
 
When you ran the live cd did you check it for defects? It's one of the menu options. Mind you you have to hit any key as soon as the graphics appears to get the full menu options.
 
Ok one thing to try. Reboot and at grub select the recovery mode option. This will take you to a command line.
 
Use this command
```
sudo apt-get install nvidia-current
```
 
Then
 
```
sudo reboot
```
 
Switched to an antique asus graphic card(32mb). Everything ok. Installed nvidia succesfully with above mentioned commands. Switched back cards. No luck....
 
Still black screen...

---

