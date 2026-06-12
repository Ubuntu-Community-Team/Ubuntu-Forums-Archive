---
title: "ERROR in syslog file every few seconds."
date: 2011-02-07
forum: General Help
---

### Post by JoeFriday49 on 2011-02-07
AMD64, Ubuntu 10.10 64bit os, with onboard video...  Works really well all the way to 1680X1050 resolution, but I get this error every 10 seconds added to my syslog... (Using a lower resolution doesn't help)

Any idea's?

Feb  7 09:22:04 AMD-64 kernel: [ 2386.746569] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 62
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746571] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746573] <3>0f 03 03 03 03 01 03 03 03 01 03 03 03 03 03 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746575] <3>03 03 03 03 03 01 03 03 03 01 01 01 03 03 03 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746577] <3>03 03 03 01 03 01 01 01 01 01 03 03 03 03 03 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746579] <3>03 01 03 01 01 01 03 01 01 01 03 03 03 03 03 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746581] <3>03 03 03 03 03 03 03 01 03 03 01 01 01 01 03 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746584] <3>03 03 03 03 03 03 03 03 03 03 03 01 01 01 01 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746586] <3>03 03 03 03 03 03 03 03 03 01 03 03 03 03 01 01  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746590] <3>03 03 03 03 03 03 03 03 03 01 03 01 01 01 01 03  ................
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746591] 
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746594] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
Feb  7 09:22:04 AMD-64 kernel: [ 2386.746597] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID

---

### Post by JoeFriday49 on 2011-02-07
As an afterthought, does anyone know how to tell the OS not to look for: drm:radeon_dvi_detect?  It's never gonna' find one as this Motherboard does not have anything but a VGA port...  No HDMI or digital ports at all.  Can't understand why it keeps lookin' for 'em...

lspci reports: 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100

---

### Post by JoeFriday49 on 2011-02-07
Another afterthought...  Is there a video card I could install that won't cause these errors?

---

### Post by dcstar on 2011-02-08
> **JoeFriday49 said:**
> As an afterthought, does anyone know how to tell the OS not to look for: drm:radeon_dvi_detect?  It's never gonna' find one as this Motherboard does not have anything but a VGA port...  No HDMI or digital ports at all.  Can't understand why it keeps lookin' for 'em...


The ATI chipset supports a DVI port even though there is not one actually installed, the chipset is erroneously reporting to the video driver that there is a DVI port and the system is trying to get the EDID from a connected DVI monitor which obviously does not exist.

Report it as a bug because the driver probably needs to be fixed to stop this occurring.

---

### Post by JoeFriday49 on 2011-02-08
> **dcstar said:**
> The ATI chipset supports a DVI port even though there is not one actually installed, the chipset is erroneously reporting to the video driver that there is a DVI port and the system is trying to get the EDID from a connected DVI monitor which obviously does not exist.

Report it as a bug because the driver probably needs to be fixed to stop this occurring.

Thanks David...  Spent the last couple of hours trying to figure out how to submit a bug report...  Guess I'm too dense to even accomplish even that...  

I did get far enough into the system to "see" a lot of reports where people were getting the same error as I am, but for sightly different reasons...  Couldn't find one where there was no digital video device connected at all like I have...

Since that system is still fairly new I may just drop back to 10.04 and try that...

---

### Post by P4man on 2011-02-08
You could try adding 
```
Option      "UseEDID"         "False"
```

in to your xorg.conf.

---

### Post by JoeFriday49 on 2011-02-08
> **P4man said:**
> You could try adding 
```
Option      "UseEDID"         "False"
```in to your xorg.conf.

These are the only files I have with that name and none of them look like they contain this sort of info...

xorg.conf it only contains the following text: 
# Minimal xorg.conf for the Nouveau driver

Section "Device"
    Identifier    "Default screen"
          Driver        "nouveau"
EndSection

xorg.conf.d is a directory that contains half dozen files and the other is xorg.conf.5.gz

Should I just edit the xorg.conf file and add the code after the EndSection line?

---

### Post by P4man on 2011-02-08
*Before *the endsection line, like this:

```
Section "Device"
Identifier "Default screen"
Driver "nouveau"
Option      "UseEDID"         "False"
EndSection
```

There is also another option:
Option     "IgnoreEDID"            "1"

I dont know what the difference between either is, unless someone else knowns, I guess you could give both a shot.

---

### Post by JoeFriday49 on 2011-02-08
> **P4man said:**
> *Before *the endsection line, like this:

```
Section "Device"
Identifier "Default screen"
Driver "nouveau"
Option      "UseEDID"         "False"
EndSection
```There is also another option:
Option     "IgnoreEDID"            "1"

I dont know what the difference between either is, unless someone else knowns, I guess you could give both a shot.

Well, can chalk that one up as a dead end...  Neither one changed the log behaviour at all...  I still think maybe I'm not editing the correct file though.  The path to it is:

/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf

Sort of looks like it's in some sort of "example" directory instead of an actual working area, but that's the only xorg.conf file I have...

---

### Post by JoeFriday49 on 2011-02-08
Found this info:
**Recommended configuration for X.org**

 No  configuration is necessary for ATI driver in the modern versions of  Ubuntu.  You can safely take away your xorg.conf and your computer will  run fine.  
 
**Customized configuration for X.org, the new way**

 Ubuntu  Karmic Koala 9.10 and later supports Kernel Mode Settings (KMS) in ATI  driver.  This mode allows to automatically detect all necessary settings  for your hardware, as well as to provide for better viewing experience.   Notably, KMS eliminates "tearing" and "blinking" of video, including  flash, and 3D windows, such as games.  The configuration file xorg.conf  is not required using KMS. 

It was posted here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) 

Sounds like I may have been editing the wrong file...

---

### Post by P4man on 2011-02-08
the file should be

```
/etc/X11/xorg.conf
```

Its optional nowadays, just create/copy the file if it isnt there.

---

### Post by JoeFriday49 on 2011-02-08
I'll give that a try...  Thanks...

---

### Post by JoeFriday49 on 2011-02-08
> **P4man said:**
> the file should be

```
/etc/X11/xorg.conf
```Its optional nowadays, just create/copy the file if it isnt there.

Now that was strange...  Boots to no monitor at all...  Booted from CD and axed the new file...

Was really hoping I would have reason to shout from the rooftops...

---

### Post by JoeFriday49 on 2011-02-10
Hmmm...  I don't guess you can really change a thread title, just a post title.  Tried to add the MB type to the thread and it didn't work...

---

### Post by JoeFriday49 on 2011-02-11
Anyone else think these fellows may be onto something?...  They are way above anything can understand, but so are most Linux users...

[LINK]("http://us.generation-nt.com/answer/patch-drm-sysfs-provide-per-connector-control-drm-kms-polling-help-200375571.html?page=1")

---

### Post by P4man on 2011-02-11
> **JoeFriday49 said:**
> Anyone else think these fellows may be onto something?...  They are way above anything can understand, but so are most Linux users...

[LINK]("http://us.generation-nt.com/answer/patch-drm-sysfs-provide-per-connector-control-drm-kms-polling-help-200375571.html?page=1")

They are kernel developers, of course us mere human beings have trouble following :). But yes, they are definitely talking about the issue you reported, but it seems they didnt patch it yet, because they dont like patching around buggy firmware problems. Now the patch is public if you are feeling truly adventurous, you could compile your own kernel and apply it, but dont ask me how :)

However, a simpeler solution is possible. For some reason I thought you had an nVidia card, and the xorg.conf you posted and implemented will not work with your ATI card, since it tries loading nvidia drivers. You could try again, but using a correct xorg.conf file. Perhaps its best you let ubuntu create one, but running this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```



Then edit /etc/X11/xorg.conf and try adding these options in the "screen" section:
```
Option      "IgnoreEDID"       "1"
Option      "UseEDID"         "False"
Option      "ModeValidation"   "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck"

```

If it doesnt work, you already know how to nuke the file again :)

---

### Post by JoeFriday49 on 2011-02-11
I'll have to try it later on tonight or tomorrow sometime...  The xorg.conf file I found on my system was just an example and I didn't copy it over to the x11 directory, I just created an empty one there and added the code to it later...

---

### Post by JoeFriday49 on 2011-02-13
> **P4man said:**
> They are kernel developers, of course us mere human beings have trouble following :). . Perhaps its best you let ubuntu create one, but running this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then edit /etc/X11/xorg.conf and try adding these options in the "screen" section:
```
Option      "IgnoreEDID"       "1"
Option      "UseEDID"         "False"
Option      "ModeValidation"   "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck"

```If it doesnt work, you already know how to nuke the file again :)

Well, another dead end...  After trying your code and it failing to run I did a little snooping and discover that command has been "Depreciated"  Here's a link to the post I found [HERE]("http://ubuntuforums.org/showthread.php?t=1360628")  

Do you think maybe I could just create the file and add the text to it manually?  That's what I did before when it completely killed the video, but I had no idea of what the text should look like.  I just copied and pasted your line into an empty file.

Edit...  I don't have a "Screen" section in this empty file.  Should the syntax just be "Screen:"

---

### Post by monkeyMonk on 2011-02-13
Joe,
  I have the same mother board, so have exact same problem. 
  I did some research on the Internet. Here is what I find.

  1. This is an kernel issue, or say the driver issue. The problem has been reported on the Internet over 1 year at least.
  2. So far I didn't see any good easy resolution. There are bunch of tweak on config, but seems to bring other issue.
  3. I had seen some patch on source code, the approaching is: Add a static flag in the driver, if find the same Error has been reported, then don't do it over again. As the result, the log file will be only showing once the complain instead of endless repeating.  However, obviously, the patch never been merged into either Linus published kernel or Ubuntu tuned kernel. 
  4. I find this bug reported in Ubuntu bug tracking board, almost a year. see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539851](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539851) . The progress is so slow. Currently its status is confirmed, but not been assigned, not even to decide the importance.  So, find a way to yell louder, let the kernel maintainer hear. LOL

---

### Post by JoeFriday49 on 2011-02-13
> **monkeyMonk said:**
> Joe,
  I have the same mother board, so have exact same problem. 
    Currently its status is confirmed, but not been assigned, not even to decide the importance.  So, find a way to yell louder, let the kernel maintainer hear. LOL  

[SIZE=3]**HELP... HELP...**[/SIZE]  I don't think that did any good...  LOL

Take a look at the last few posts in this thread. I'm flying blind here with no knowledge of what I'm doing, but if I could stop this by adding a few lines of code to a xorg.conf file I'd sure give it a try.  Now as far as compiling a new kernel, I'd be so totally out of my league I can't even think of a comparison...

I may try purchasing a video card of a different type and installing that, but I'm afraid the system would still see the one that's built in to my motherboard and keep generating the spam reports anyway.  

Hmmm...  I wonder if there is a way to just turn off error reporting altogether?

---

### Post by monkeyMonk on 2011-02-13
> **JoeFriday49 said:**
> [SIZE=3]**HELP... HELP...**[/SIZE]  I don't think that did any good...  LOL

Take a look at the last few posts in this thread. I'm flying blind here with no knowledge of what I'm doing, but if I could stop this by adding a few lines of code to a xorg.conf file I'd sure give it a try.  Now as far as compiling a new kernel, I'd be so totally out of my league I can't even think of a comparison...

I may try purchasing a video card of a different type and installing that, but I'm afraid the system would still see the one that's built in to my motherboard and keep generating the spam reports anyway.  

Hmmm...  I wonder if there is a way to just turn off error reporting altogether?

Well, here is my thoughts.
1. Get a new video card should be a resolution. To the concern of your Linux kernel will keep generating those spam, I believe that you should turn your onboard video card off in the BIOS, then should be all fine.
    However, one thing need to be sure, don't take another Radeon, check linux hardware list to find a suggested. 

2. Build kernel is kind of challenge. However, by following some blog instructed, I did it compiled and installed.  But I think it was overkilled. Instead of replacing whole kernel image and all set of modules with it, I believe by replacing only radeon.ko at /lib/modules/2.6.3x-xx-generic/kernel/drivers/gpu/drm/radeon should fix the problem, or few bunch of .ko and .bin under /lib/modules/2.6.3x-xx-generic/kernel/drivers/gpu/drm/radeon and /lib/firmware/2.6.3x-xx-generic/radeon/*.bin?  A kernel guy may able to fix it less than hour, Sigh.

---

### Post by JoeFriday49 on 2011-02-13
> **monkeyMonk said:**
> Well, here is my thoughts.
I believe that you should turn your onboard video card off in the BIOS, then should be all fine.
    
Build kernel is kind of challenge. However, by following some blog instructed, I did it compiled and installed.  A kernel guy may able to fix it less than hour, Sigh.

I could see no where in my system's BIOS to turn off the onboard video, but I wasn't looking specifically for that switch...

So after building a new kernel won't the next update just overwrite all your work and put your system back to square one?  I would have a lot of learning to do before I could modify the linux kernel.  I think I will just remain an appliance operator and leave the coding to those that enjoy that sort of stuff...  

I just looked at my log directory.  It is growing at about 5MB per hour...  Good thing I opted for the 1TB drive when I put this thing together...

---

### Post by P4man on 2011-02-14
> **JoeFriday49 said:**
> Well, another dead end...  After trying your code and it failing to run I did a little snooping and discover that command has been "Depreciated"  Here's a link to the post I found [HERE]("http://ubuntuforums.org/showthread.php?t=1360628")  

You're right. The correct way to do it now is a bit more complex. You have to stop X. Press control+alt+F1 and then tun

```
sudo service gdm stop
```

```
sudo X -configure
```

which will create an xorg.conf.new file in your home folder (or possibly /root). Copy that to /etc/X11/xorg.conf.

TO be safe, reboot (sudo reboot)and see if everything still works. It shouldnt change anything. If it still works, try the EDID tricks.

---

### Post by JoeFriday49 on 2011-02-14
> **P4man said:**
> You're right. The correct way to do it now is a bit more complex. You have to stop X. Press control+alt+F1 and then tun

```
sudo service gdm stop
``````
sudo X -configure
```which will create an xorg.conf.new file in your home folder (or possibly /root). Copy that to /etc/X11/xorg.conf.

TO be safe, reboot (sudo reboot)and see if everything still works. It shouldnt change anything. If it still works, try the EDID tricks.

Well I gave it the ole college try...  Once I get the ctrl+alt+F1 the window keeps scrolling all those errors every few seconds and I can't get anything entered before it disappears off the top of the screen.  It also doesn't appear to accept my password either.  When I enter a sudo command it asks for the password and mine doesn't work.  It just says incorrect password.  I have no problems using sudo commands in terminal through the GUI, but it won't accept it on the big screen?...

I also looked into my bios when rebooting and there doesn't appear to be a place to disable the onboard video.  It may show up if I install another card.  I'll try that before I give up and part this thang out...

Thanks for the help...

---

### Post by P4man on 2011-02-14
You could do it in recovery mode > root shell. Just be aware that the file will be created in the home folder of the root user, which is /root.

---

### Post by JoeFriday49 on 2011-02-14
> **P4man said:**
> You could do it in recovery mode > root shell. Just be aware that the file will be created in the home folder of the root user, which is /root.

Doooh!...  Well I did that, and now I seem to be stuck there.  I changed the boot option in System>Administration>Login to boot in Recovery mode and it just does that.  I get a little white box on a black screen and by pressing ctrl+alt+F1 I get a large terminal window.  But from there the error messages scroll by so fast I can't enter anything.  If I reboot and just enter "sudo service gdm stop" in the little white window I get a terminal screen that won't allow me to enter anything.  (But the error messages still scroll by)

Is there a way to get back to the GUI from here or will I have to reinstall the OS?

---

### Post by JoeFriday49 on 2011-02-14
Exit in the little window brings me to a login screen with my name, but no other menu options.  Enter will take me straight back to the little white window...

---

### Post by P4man on 2011-02-14
:confused:

I meant to select recovery mode from the grub menu. It ought to be there by default. If you dont have a grub menu upon booting, then hold down the shift key right after bios post.

If you are getting error messages in the terminal without x even running, then.. Id be curious to see what they are. Surely not about edid?

---

### Post by JoeFriday49 on 2011-02-14
> **P4man said:**
> :confused:

I meant to select recovery mode from the grub menu. It ought to be there by default. If you dont have a grub menu upon booting, then hold down the shift key right after bios post.

If you are getting error messages in the terminal without x even running, then.. Id be curious to see what they are. Surely not about edid?

I don't have a grub menu.  It just always booted straight into the gui desktop.  I told it to remember JoeFridays password.  

The little white screen doesn't show the errors,  but I can't get out of there.  Exit takes me to a login screen with no options.  Login takes me back to the little white window.

When I enter the "sudo service gdm stop" command string in the little white window I go to a full size screen, and am unable to enter anything because of the scrolling errors.

Time for the install CD?

---

### Post by P4man on 2011-02-14
Hold down the shift key to get the grub menu. Press it when you see your BIOS splash/post and keep it pressed. It will show.

---

### Post by JoeFriday49 on 2011-02-14
> **P4man said:**
> Hold down the shift key to get the grub menu. Press it when you see your BIOS splash/post and keep it pressed. It will show.

Apparently on my keyboard I have to use the right shift key to get to the menu...  But even when I do there are 4 or 5 selections and all of 'em take me back to either a little white screen or the big terminal window...  Guess the gui is gone...  Bad timing too, as the video card I ordered for my other Ubuntu machine came in today.  It's a Nvida 8400 and should work...

I wonder if there is another flavour of Linux that doesn't have these problems?  The only other one I've messed with is Mint and I understand it's just Ubuntu with a different sort of eye candy so it probably wouldn't be any better...

---

### Post by monkeyMonk on 2011-02-14
> **JoeFriday49 said:**
> I could see no where in my system's BIOS to turn off the onboard video, but I wasn't looking specifically for that switch...

So after building a new kernel won't the next update just overwrite all your work and put your system back to square one?  I would have a lot of learning to do before I could modify the linux kernel.  I think I will just remain an appliance operator and leave the coding to those that enjoy that sort of stuff...  

I just looked at my log directory.  It is growing at about 5MB per hour...  Good thing I opted for the 1TB drive when I put this thing together...
Try to answer your question:
1. I hope when a video card plug-in, the BIOS will show you a option to turn onboard video off. I hope so but only the manufacture can tell.
2. Any kernel update will losing your private fix, so it needs to get the new kernel source, apply the fix patch, then build and install. It took me about 40 mins.  That is the situation whoever use private built kernel.  The good thing is, as I have mentioned before, it does not really necessary to rebuild whole kernel image and install it; The problem should only in radeon.ko or few more kernel modules, located at /lib/modules/2.6.35-xx... , so only recompile those kernel module and replace them should works. That will be only take less than 5 min. I'm still trying to figure out the options that been used to compile radeon.ko. Once I find it out, my private fix will be only take 5 minutes.:D

---

### Post by P4man on 2011-02-15
> **JoeFriday49 said:**
> Apparently on my keyboard I have to use the right shift key to get to the menu...  But even when I do there are 4 or 5 selections and all of 'em take me back to either a little white screen or the big terminal window...  Guess the gui is gone...  Bad timing too, as the video card I ordered for my other Ubuntu machine came in today.  It's a Nvida 8400 and should work...

THe idea was to get you back to a full screen terminal (recovery mode, root terminal). From there you can nuke your xorg.conf again

```
sudo rm /etc/X11/xorg.conf
```

Im not entirely sure how to undo the default login mode, but I suspect from the grub menu selecting the regular kernel should give you a GUI again (after nuking the xorg.conf), then you can set the default setting again the way you changed it (system > administration > login)

> I wonder if there is another flavour of Linux that doesn't have these problems?  The only other one I've messed with is Mint and I understand it's just Ubuntu with a different sort of eye candy so it probably wouldn't be any better...

No other distro will help I fear, as this is a kernel issue. OTOH, if the cause of it is your current ATI card (and not the onboard video), then just plugging in the nVidia card might solve it.

---

### Post by JoeFriday49 on 2011-02-15
> **P4man said:**
> THe idea was to get you back to a full screen terminal (recovery mode, root terminal). From there you can nuke your xorg.conf again

```
sudo rm /etc/X11/xorg.conf
```Im not entirely sure how to undo the default login mode, but I suspect from the grub menu selecting the regular kernel should give you a GUI again (after nuking the xorg.conf), then you can set the default setting again the way you changed it (system > administration > login)



No other distro will help I fear, as this is a kernel issue. OTOH, if the cause of it is your current ATI card (and not the onboard video), then just plugging in the nVidia card might solve it. 

I never did get to the part where I could create the xorg.conf file...  The errors kept scrolling too fast and it never would take a sudo command, but I'll try your suggestion for deleting one just in case my folly in permanently entering recovery mode may have created one.  I doubt I can enter that line and my password before I get scrolled off screen though.

I've selected every one of the grub options by rebooting many times, and they all take me back to what I think is called x window.  The little white window on a black background.  The exit command from there always takes me to a login screen with my user name highlighted.  There is an "Other" button below that, but selecting that shows no other user's.  By clicking the user name or the Login button I go back to the little white window.  This happens everytime I try, regardless of which grub option I selected when I rebooted.  I thought your login options were supposed to show up in the bottom bar on the bottom of my screen, but the only things there are a little man icon for keyboard assistance, a clock and a stop icon that only gives me a shutdown, suppend and I think reboot option...  (I've used 'em all)

Oh, I almost forgot.  The onboard card is ATI.  I don't currently have a video card installed, I just want to try one...

Think what I'll do this morning is install the new video card, boot from CD and move the files I have on the machine's local HD over to NAS.  I can also check to see if the new card stops the spam logging...  I won't reload the OS though until I can come up with a replacement video card for that machine.  If the onboard ATI video can't be turned off I may have to come up with a new MB altogether...

Think I'll do some searching on exiting recovery mode...  Never can tell, I may not be the first person to do this...

---

### Post by P4man on 2011-02-15
Im not sure I understand whether or not you managed to boot in to recovery mode or not. Does grub show a recovery option? If it does, booting it ought to give you a menu where you can choose between fail safe X some other options and a root terminal. But perhaps that menu (which is not graphical, but in blue and red text if I recall) also gets hidden by the error messages?

One more thing to try: boot with  ```
ro single nomodeset
``` as (only) kernel parameters. The link in my signature explains how to set kernel parameters in grub.

---

### Post by JoeFriday49 on 2011-02-15
> **P4man said:**
> Im not sure I understand whether or not you managed to boot in to recovery mode or not. Does grub show a recovery option? If it does, booting it ought to give you a menu where you can choose between fail safe X some other options and a root terminal. But perhaps that menu (which is not graphical, but in blue and red text if I recall) also gets hidden by the error messages?

One more thing to try: boot with  ```
ro single nomodeset
``` as (only) kernel parameters. The link in my signature explains how to set kernel parameters in grub.

Just came back up from "the dungeon", (my pet name for my downstairs laundry room/computer workshop)...  I'm still stuck.  I can't even make it boot grub menu anymore, it just goes straight into the little white window without asking me anything, and holding down shift keys no longer works at all...  Must have booted a dozen times trying to get back to the menu, but no workie for me...

I did find a post that tells a user how to quit recovery mode, but that was also a dead end...

I would love to try the:  boot with  ```
ro single nomodeset
``` suggestion, but it won't go to any menu screens at all anymore...

---

### Post by P4man on 2011-02-15
Can you post a pic of that of that "little white window"? Do you mean cursor? Anyway, if grub isnt loading anymore, then you have some serious problems. If you want, you can try reinstalling grub from a livecd:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But Id start by backing up your stuff.

---

### Post by JoeFriday49 on 2011-02-15
> **P4man said:**
> Can you post a pic of that of that "little white window"? Do you mean cursor? Anyway, if grub isnt loading anymore, then you have some serious problems. If you want, you can try reinstalling grub from a livecd:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But Id start by backing up your stuff.

Oh, everything's backed up...  

The little white window is about 3" square on a black screen and has a "command line" in it.  It comes up already logged in as JoeFriday49.  If I ctrl+alt+F1 out of the little box I go to a regular full screen terminal, but have to login again...

---

### Post by JoeFriday49 on 2011-02-22
Update...  Reloaded 10.10 and got it up and running and installed a new video card.  This time a Nvidia so there should be no problems with the Radeon, right?...  Couple of problems though.  I can't make the Nvidia work, and I can't turn the Radeon off...

Anybody wanna' buy a good motherboard?

---

### Post by JoeFriday49 on 2011-02-25
One more try, with another video card...  This one worked and disabled the onboard video!...  No more errors...  I'm gonna' mark this as closed even though I don't really think throwing money at the problem was a proper resolution, but in this case it worked...

---

### Post by HunkirDowne on 2011-07-03
I see this thread is marked '[SOLVED]' but for the life of me I cannot parse the solution.  If it is in here, please clue me in.  If not, can you shed some light on the solution?


Thanks!

---

### Post by JoeFriday49 on 2011-07-03
>>  I'm gonna' mark this as closed even though I don't really think  throwing money at the problem was a proper resolution, but in this case  it worked...<<

Well it really isn't solved, but in this case I just kept switching video cards until I ran across one that allowed me to turn off the onboard video card which was the source of "my" errors...  I realize that anyone having this problem with a system where different video cards could not be tried would simply be at a loss and still stuck.  

As it turned out I purchased a card from Tiger Direct they were running a closeout sale on for 29 bucks.  Got free shipping and a 35 dollar rebate card, so I made 5 bucks for my trouble...

You may also want to check out this thread:  [http://ubuntuforums.org/showthread.php?p=10995067#post10995067](http://ubuntuforums.org/showthread.php?p=10995067#post10995067)  It's a bunch discussing stuff WAAAY over my head, but it seems as if they may come upon a real solution.  Now if I could just understand it I'd be all set...

---

### Post by HunkirDowne on 2011-07-04
> **JoeFriday49 said:**
> 
You may also want to check out this thread:  [http://ubuntuforums.org/showthread.php?p=10995067#post10995067](http://ubuntuforums.org/showthread.php?p=10995067#post10995067)  

I was on there earlier and tried the /etc/modprobe.d/options.config trick (which didn't work) but noticed the rest of the files (and typically are) ".conf" (even though we say "config"), but got "interrupted" by family before I could try it out.  Will try again later this week.

Thanks for the clarification and although my sanity may still be in question, this is a datum in the positive.

---

### Post by JoeFriday49 on 2011-07-23
Well it doesn't appear that even the new kernel release will help this problem...  

[https://lkml.org/lkml/2011/7/21/455](https://lkml.org/lkml/2011/7/21/455)

---

### Post by HunkirDowne on 2011-07-25
I saw Torvald's post and understand the change in kernel version numbers is primarily cosmetic.  But on the other hand, I have recently upgraded my sid installation (aptosid) and the problem seems to have abated.  I still get a brief DRM message but I am now able to operate in tty mode without the drm spam.

So hope holds out and the fix, whatever it was, should appear in testing (and as such, Ubuntu) relatively soon.

---

