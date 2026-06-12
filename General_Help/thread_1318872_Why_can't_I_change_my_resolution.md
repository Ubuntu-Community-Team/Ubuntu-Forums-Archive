---
title: "Why can't I change my resolution?"
date: 2009-11-07
forum: General Help
---

### Post by hackerlife on 2009-11-07
Hello world.

So I recently transfered over my two Hdds over to a different computer, because the other computer is faster, has more ram, and... well, not broken lol.

I didn't really expect it to even boot to be honest, and was mightly surprised when it did.

Only problem is my resolution is 640x480... And my monitor (viewsonic G90fb) is capable of MUCH higher resolutions.

I tried quite a few things now, almost screwed myself over, but am now at a loss.

I think one of the main reasons I can't edit my resolution is because I no longer have ownership of /etc/x11...

I'm not really all that new to Ubuntu (9.04), but I am pretty confused now!
Is my problem the driver?
Is my problem the permissions?

How do I change these permissions?
Which driver can I change to???
Thanks for any and all help!!!!1

ps.
I have the nvidia 96 driver enabled, my card is an integrated nvidia gforce4... if I think of anything else, I'll post it
thanks again!

---

### Post by hackerlife on 2009-11-07
Output of lspci | grep VGA
> 
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)


nvidia-xconfig:
> Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.


nvidia-settings:
> ERROR: Cannot open display 'wtmi-compie:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 19 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 20 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 21 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 22 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 23 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 24
       of configuration file '/home/william/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 25
       of configuration file '/home/william/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 26 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 27 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 28 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 29 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 30 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 31 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line
       32 of configuration file '/home/william/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 33 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 34 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 35 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 36 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 37 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 38 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 39 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 40 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 41 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 42 of
       configuration file '/home/william/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on
       line 43 of configuration file '/home/william/.nvidia-settings-rc'
       (no Display connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on
       line 44 of configuration file '/home/william/.nvidia-settings-rc'
       (no Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 45
       of configuration file '/home/william/.nvidia-settings-rc' (no
       Display connection).




But the settings manager does open.
So thats why I think its a permissions thing... But I can't find any solid info on how to change permissions... I've done it before I think tho...
Thanks again again!

---

### Post by hackerlife on 2009-11-08
Did I tell you guys that I'm a bloody idiot??

I though if I sudo chmod 666 /etc/X11 I could get the permission to edit xorg.conf

The files disappeared

Then, like the idiot I am, I decided to do the same to /

I have nooooo idea why I did that.

Anyways, I've lost permission to do anything at all. I can't even sudo now.
 
I tried this[http://ubuntuforums.org/showthread.php?t=942717&page=2]("http://ubuntuforums.org/showthread.php?t=942717&page=2") but to no avail.
Now it doesn't even start up.

I should have just reinstalled on the other computer, instead of moving the hdd over and expecting it to work.

Please save me!

---

### Post by hackerlife on 2009-12-07
Does bumping work here?

---

