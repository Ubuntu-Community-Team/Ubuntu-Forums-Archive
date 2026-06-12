---
title: "Error message on screen due to monitor Ubuntu 12.04"
date: 2012-09-24
forum: General Help
---

### Post by tehforum on 2012-09-24
Hi,

I installed Ubuntu 12.04 yesterday, but when I just turned the computer on right now, the following came up.

I will now say that the same thing did happen yesterday, however, the screen re adjusted itself, but now I'm having no luck!
I  can't even see the boot phase.

The message displayed on the screen is
D-SUB

OUT OF RANGE

92.6KHz/58Hz

The monitor is an LG IPS235 Flatron and I have a driver disk...but that's for Windows only.

Please help!

---

### Post by tehforum on 2012-09-24
Some googling if it helps

"We regret the trouble you have experienced with this monitor. An &#8220;Out of Range&#8221; message typically means that a setting has been configured on the computer that may not be compatible with the monitor. With a resolution of 1920x1080, the refresh rate of the computer must be at 60Hz. If it is not, then you will receive this error message. If you have additional questions about this unit, please contact our Customer Interactive Center at 800-243-0000."

---

### Post by carranty on 2012-09-24
If you can't even see your bios screen then I think there must be a hardware fault somewhere (ubuntu doesn't even load until after this point).

---

### Post by tehforum on 2012-09-24
> **carranty said:**
> If you can't even see your bios screen then I think there must be a hardware fault somewhere (ubuntu doesn't even load until after this point).

Hi,

The weird thing is that when I plug in my Ubuntu 12.04 bootable usb stick, everything works fine.

Should I post my xorg.conf?

---

### Post by tehforum on 2012-09-24
I don't have a xorg.conf file...

I first looked in the standard /etc/X11/xorg.conf

not found

then I ran the command locate xorg.conf

it led me to

/usr/share/X11/zorg.conf.d

There are many files including

10-evdev.conf
11-evdev-quirks.conf
11-evdev-trackpoint.conf
50-synaptics.conf
50-vmmmouse.conf
50-wacom.conf
51-synaptics-quirks.conf

---

### Post by tehforum on 2012-09-24
Okay, I found out that xorg.conf isn't used anymore.

I used xrandr, to change the refresh rate to 50Hz - edit, the setting didn't save .

I still get the little error message before the login screen comes up, then it refreshes and it works.

Ideally, I would like to get rid of the error message completely!

---

### Post by Favux on 2012-09-24
Hi tehforum,

The xrandr command is a runtime command, which means it only applies to the current session.  If you want to do it through a xrandr command you'll need to add it to a startup script:  [http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent](http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent)

It may be that Xorg isn't correctly detecting and configuring your monitor or it may also have something to do with your video chipset:
```
lspci |grep VGA
```
and driver.  In other words posting your video chipset and video driver would be a good idea.

Either way the more traditional thing to do is to then configure things in xorg.conf, which you can still do.  Or now days you could do an identical, or nearly so, configuration in a custom xorg.conf.d .conf file at /etc/X11/xorg.conf.d.

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> Hi tehforum,

The xrandr command is a runtime command, which means it only applies to the current session.  If you want to do it through a xrandr command you'll need to add it to a startup script:  [http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent](http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent)

It may be that Xorg isn't correctly detecting and configuring your monitor or it may also have something to do with your video chipset:
```
lspci |grep VGA
```
and driver.  In other words posting your video chipset and video driver would be a good idea.

Either way the more traditional thing to do is to then configure things in xorg.conf, which you can still do.  Or now days you could do an identical, or nearly so, configuration in a custom xorg.conf.d .conf file at /etc/X11/xorg.conf.d.

Hi, thanks for replying.

The results from the command:

```


00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

```

Also, when I went to system settings, and clicked on Additional drivers, it lists 4 drivers including

NVIDIA accelerated graphics driver (version current) [recommended]

there are 3 other ones, but the point is that none of them are activated.

When I do try and activate them it says

Cannot change driver
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid

---

### Post by Favux on 2012-09-24
lol  I just went through a struggle with a very similar card:
```
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
```
So the mobile version.  I'm no video guru but I learned a couple of things dealing with it.  See:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=111779](http://forums.linuxmint.com/viewtopic.php?f=42&t=111779)

It should be on the nouveau driver if it isn't on the proprietary Nvidia driver.  Let's check:
```
lsmod |grep nouveau
```
> Cannot change driver
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid 
Nvidia settings is suppose to generate a xorg.conf file when you activate the proprietary driver.  Is there an xorg.conf file at /etc/X11?  Maybe you just need to create an empty file called xorg.conf at /etc/X11 and that would make it happy?

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> lol  I just went through a struggle with a very similar card:
```
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
```
So the mobile version.  I'm no video guru but I learned a couple of things dealing with it.  See:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=111779](http://forums.linuxmint.com/viewtopic.php?f=42&t=111779)

It should be on the nouveau driver if it isn't on the proprietary Nvidia driver.  Let's check:
```
lsmod |grep nouveau
```

Nvidia settings is suppose to generate a xorg.conf file when you activate the proprietary driver.  Is there an xorg.conf file at /etc/X11?  Maybe you just need to create an empty file called xorg.conf at /etc/X11 and that would make it happy?
It is destiny.

When I enter that command, I get no response. I think that's the error, right?

edit

Ok, I edited the grub file, and updated it.

And I typed in the command again, and I still get no response.

---

### Post by Favux on 2012-09-24
I suspect so.

And then the problem is likely you are using the VESA failsafe driver and that's why the monitor isn't being handled correctly.  So unless you can live with only 2 GB RAM you want the Nvidia proprietary driver activated and working.

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> I suspect so.

And then the problem is likely you are using the VESA failsafe driver and that's why the monitor isn't being handled correctly.  So unless you can live with only 2 GB RAM you want the Nvidia proprietary driver activated and working.

Please see the previous edited post.

I've only got 2GB of RAM on this computer.

I remember the driver was activated yesterday (NVIDIA accelerated graphics driver (version 173) so I don't know what went wrong.

---

### Post by Favux on 2012-09-24
Oh, then that's different.  The Nvidia driver probably blacklisted Nouveau and that's why it isn't available.

If it was activated yesterday see if there is an xorg.conf file in /etc/X11.  Nvidia settings should have also generated a backup xorg.conf when it installed.

Was there a Nvidia driver update recently or did you have a hard shutdown or some such?  If the driver is really activated you may just need to use the command to regenerate the xorg.conf if it is damaged.

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> Oh, then that's different.  The Nvidia driver probably blacklisted Nouveau and that's why it isn't available.

If it was activated yesterday see if there is an xorg.conf file in /etc/X11.  Nvidia settings should have also generated a backup xorg.conf when it installed.

Was there a Nvidia driver update recently or did you have a hard shutdown or some such?  If the driver is really activated you may just need to use the command to regenerate the xorg.conf if it is damaged.

I made a xorg.conf file, and now I'm downloading and installing the recommended drivers.

edit: error still appears after restart.
the computer doesn't like the "recommended drivers", compiz failed to launch and no menus are showing.

Now there's a window:

'precise' is no longer under development blah blah...

now the screen went black, with lots of multicoloured lines. great

However, that still doesn't solve the problem of the lsmod grep nouveau command giving no feedback, even when I edited the grub files.

Cheers for any help

---

### Post by Favux on 2012-09-24
Good, sounds like you are set.  :)

The Nvidia driver blacklists the nouveau driver so it isn't available to a system that has installed the Nvidia proprietary driver.  When you deactivate it it removes the blacklisting.

That's because the two weren't able to coexist until recently.  Now supposedly they are.  And with the new 302 Nvidia driver (out in May) the Nvidia proprietary driver is supposedly finally RandR compliant.

Edit:  So still not working?

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> Good, sounds like you are set.  :)

The Nvidia driver blacklists the nouveau driver so it isn't available to a system that has installed the Nvidia proprietary driver.  When you deactivate it it removes the blacklisting.

That's because the two weren't able to coexist until recently.  Now supposedly they are.  And with the new 302 Nvidia driver (out in May) the Nvidia proprietary driver is supposedly finally RandR compliant.

Please see edited post.

Everything got screwed up lol

---

### Post by Favux on 2012-09-24
Post your xorg.conf please.

Alright so some sort of Nvidia proprietary mess.  But now you have key words to google with.  The error messages and the chipset.

Nvidia has a complete HOW TO for linux on their site.
[http://manpages.ubuntu.com/manpages/oneiric/en/man1/nvidia-settings.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nvidia-settings.1.html)
[http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html)
[http://ubuntuforums.org/archive/index.php/t-1101445.html](http://ubuntuforums.org/archive/index.php/t-1101445.html)

First thought is to check /var/log/apt and see if the recent history.log has a Nvidia update.  You might want to role back to the previous version.  Or the other way is to see if a updated driver is in the proposed repo. or check xorg-edgers if they have recent one they are pushing.

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> Post your xorg.conf please.

Alright so some sort of Nvidia proprietary mess.  But now you have key words to google with.  The error messages and the chipset.

Nvidia has a complete HOW TO for linux on their site.
[http://manpages.ubuntu.com/manpages/oneiric/en/man1/nvidia-settings.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nvidia-settings.1.html)
[http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html)
[http://ubuntuforums.org/archive/index.php/t-1101445.html](http://ubuntuforums.org/archive/index.php/t-1101445.html)

First thought is to check /var/log/apt and see if the recent history.log has a Nvidia update.  You might want to role back to the previous version.  Or the other way is to see if a updated driver is in the proposed repo. or check xorg-edgers if they have recent one they are pushing.

Section "Device"
Identifier	"Default Device"
Driver	"nvidia"
Option	"NoLogo"	"True"
EndSection

That was all that was there from memory.

How do I roll back to the (NVIDIA accelerated graphics driver (version 173)? I can't access anything, the only thing I can see is a Trash icon.

---

### Post by Favux on 2012-09-24
If you comment out the Device section (a # in front of every line) it should boot with the VESA driver.  Use nano from Recovery Mode.  Also Recovery Mode should let you boot with the failsafe, i.e. VESA, driver.

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> If you comment out the Device section (a # in front of every line) it should boot with the VESA driver.  Use nano from Recovery Mode.  Also Recovery Mode should let you boot with the failsafe, i.e. VESA, driver.

I can't load the recovery mode as the original error message means I can't see anything.

Can I fix it via a ubuntu 12.04 bootable usb?

---

### Post by Favux on 2012-09-24
At boot when you arrow to select the Recovery Mode options should appear after a bit.  That's a non-graphical (command line) display so your video driver doesn't enter into it.  One of the options is failsafe video and another is boot to command line.  Command line is where you enter:  **nano /etc/X11/xorg.conf** and comment out the section.  Or if you boot with failsafe then you can edit it in the gui.

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> At boot when you arrow to select the Recovery Mode options should appear after a bit.  That's a non-graphical (command line) display so your video driver doesn't enter into it.  One of the options is failsafe video and another is boot to command line.  Command line is where you enter:  **nano /etc/X11/xorg.conf** and comment out the section.  Or if you boot with failsafe then you can edit it in the gui.

This is a nightmare.

I'll tell you what happens.

Switch on computer
At the bottom left, there's two options
press Del for setup, and f11 for boot settings e.g selecting to boot from usb

Then as soon as that loads, the original error messages come up, meaning I can't press escape to access the recovery mode.

I have also tried to boot from USB, then press ESC when it loads up.

I did get to a black screen with just the following

boot::

I tried to type in a command, but nothing happened.

---

### Post by Favux on 2012-09-24
Ouch.

Wandering way out of my comfort zone.

I'm guessing you hosed Grub at some point.  Are you seeing the normal startup screen where it lets you select which release and kernel to boot in.  Windows boot included, etc.?  Recovery Mode is something you should see with Grub working correctly.  It is with the selection list of kernels and so on.  Not something you need to hit keys for.

You should try to reinstall Grub using a live CD and see if that doesn't get you Recovery Mode:  [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by tehforum on 2012-09-24
> **Favux said:**
> Ouch.

Wandering way out of my comfort zone.

I'm guessing you hosed Grub at some point.  Are you seeing the normal startup screen where it lets you select which release and kernel to boot in.  Windows boot included, etc.?  Recovery Mode is something you should see with Grub working correctly.  It is with the selection list of kernels and so on.  Not something you need to hit keys for.

You should try to reinstall Grub using a live CD and see if that doesn't get you Recovery Mode:  [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Nah I can't see any of that.

At the moment I'm installing boot repair, but this is taking ages.

currently scanning systems (os-prober) this may require several minutes .... or an hour

---

### Post by tehforum on 2012-09-24
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 68, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 68, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory

(glade2script:5473): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.CLDHLW': No such file or directory

(glade2script:5473): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by tehforum on 2012-09-24
That's what appeared in the terminal when I used boot-repair

[http://paste.ubuntu.com/1224887/](http://paste.ubuntu.com/1224887/)

I give up.

I'm just going to reinstall Ubuntu 12.04

---

### Post by Wim Sturkenboom on 2012-09-24
I'm not familiar enough with the modern grub to advise how to circumvent your issues. One way might be to add a nomodeset in /boot/grub/grub.cfg on the harddisk (using the liveCD / liveUSB)

```

menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root 2e61cbc5-d982-4ada-8af7-cbdea09bb295
[COLOR="Red"]        linux   /boot/vmlinuz-3.2.0-31-generic root=UUID=2e61cbc5-d982-4ada-8af7-cbdea09bb295 ro   quiet splash _nomodeset_ $vt_handoff[/COLOR]
        initrd  /boot/initrd.img-3.2.0-31-generic
}

```
Add 'nomodeset' to the line in red (as shown underlined) and see if the boot situation improves. You can also remove the 'quiet splash'. I don't expect you to get the grub menu, but it might help to get to a 'normal' login screen.
That's probably how far I will be able to help.

> **tehforum said:**
> The monitor is an LG IPS235 Flatron and I have a driver disk...but that's for Windows only.
This is the only Windows 'driver' disk that I'm aware of that is actually usefull under Linux. For the simple reason that it's **[COLOR="Red"]not[/COLOR]** a driver disk.

The disk contains an inf file that specifies the resolution(s). You will find something like the below (which is for my Acer X243W).
```

[X243W_Analog.AddReg]
HKR,"MODES\1920,1200",Mode1,,"30.0-82.0,56.0-76.0,+,-"
HKR,,PreferredMode,,"1920,1200,60"
HKR,,ICMProfile,0,"X243W.icm"

```

An explanation can be found at [http://msdn.microsoft.com/en-us/library/windows/hardware/ff568432%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/ff568432%28v=vs.85%29.aspx)

For the example above, 30.0-82.0 is the range for horizontal refresh rate while 56.0-76.0 is the range for the vertical refresh rate.
You can use these values in a xorg.conf file in the monitor section.

---

### Post by tehforum on 2012-09-24
> **Wim Sturkenboom said:**
> I'm not familiar enough with the modern grub to advise how to circumvent your issues. One way might be to add a nomodeset in /boot/grub/grub.cfg on the harddisk (using the liveCD / liveUSB)

```

menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root 2e61cbc5-d982-4ada-8af7-cbdea09bb295
[COLOR="Red"]        linux   /boot/vmlinuz-3.2.0-31-generic root=UUID=2e61cbc5-d982-4ada-8af7-cbdea09bb295 ro   quiet splash _nomodeset_ $vt_handoff[/COLOR]
        initrd  /boot/initrd.img-3.2.0-31-generic
}

```
Add 'nomodeset' to the line in red (as shown underlined) and see if the boot situation improves. You can also remove the 'quiet splash'. I don't expect you to get the grub menu, but it might help to get to a 'normal' login screen.
That's probably how far I will be able to help.

This is the only Windows 'driver' disk that I'm aware of that is actually usefull under Linux. For the simple reason that it's **[COLOR="Red"]not[/COLOR]** a driver disk.

The disk contains an inf file that specifies the resolution(s). You will find something like the below (which is for my Acer X243W).
```

[X243W_Analog.AddReg]
HKR,"MODES\1920,1200",Mode1,,"30.0-82.0,56.0-76.0,+,-"
HKR,,PreferredMode,,"1920,1200,60"
HKR,,ICMProfile,0,"X243W.icm"

```

An explanation can be found at [http://msdn.microsoft.com/en-us/library/windows/hardware/ff568432%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/ff568432%28v=vs.85%29.aspx)

For the example above, 30.0-82.0 is the range for horizontal refresh rate while 56.0-76.0 is the range for the vertical refresh rate.
You can use these values in a xorg.conf file in the monitor section.

Hello,

I re-installed Ubuntu 12.04 and I'm back and running.

OK, I found the .inf file and this is what I've got

```


;=============================================================== 
; [IPS235.INF] 
; Revision 1.0   March-11-2011
; Copyright(c)1998~2011 LG Electronics Inc.,All Rights Reserved.
;===============================================================
;
[Version]
signature="$CHICAGO$"
Class=Monitor
ClassGuid={4D36E96E-E325-11CE-BFC1-08002BE10318}
Provider=%LG%
CatalogFile=IPS235.cat
DriverVer=03/11/2011,1.0

[ControlFlags]
ExcludeFromSelect.NT=Monitor\GSM587C
ExcludeFromSelect.NT=Monitor\GSM587D
ExcludeFromSelect.NT=Monitor\GSM587E

[DestinationDirs]
DefaultDestDir = 11
IPS235_Analog.CopyFiles = 23
IPS235_Digital.CopyFiles = 23
IPS235_HDMI.CopyFiles = 23

[SourceDisksNames]
1=%DiskName%,,,

[SourceDisksFiles]
IPS235.ICM=1

[Manufacturer]
%LG%=LG,NTamd64

[LG]
%IPS235_Analog%=IPS235_Analog.Install,Monitor\GSM587C
%IPS235_Digital%=IPS235_Digital.Install,Monitor\GSM587D
%IPS235_HDMI%=IPS235_HDMI.Install,Monitor\GSM587E

[LG.NTamd64]
%IPS235_Analog%=IPS235_Analog.Install,Monitor\GSM587C
%IPS235_Digital%=IPS235_Digital.Install,Monitor\GSM587D
%IPS235_HDMI%=IPS235_HDMI.Install,Monitor\GSM587E

[IPS235_Analog.Install]
DelReg=DEL_CURRENT_REG
AddReg=IPS235_Analog.AddReg,1920,DPMS
CopyFiles=IPS235_Analog.CopyFiles

[IPS235_Digital.Install]
DelReg=DEL_CURRENT_REG
AddReg=IPS235_Digital.AddReg,1920,DPMS
CopyFiles=IPS235_Digital.CopyFiles

[IPS235_HDMI.Install]
DelReg=DEL_CURRENT_REG
AddReg=IPS235_HDMI.AddReg,1920,DPMS
CopyFiles=IPS235_HDMI.CopyFiles

[DEL_CURRENT_REG]
HKR,MODES
HKR,,MaxResolution
HKR,,DPMS
HKR,,ICMProfile

[1920]
HKR,,MaxResolution,,"1920,1080"

[DPMS]
HKR,,DPMS,,1

[B][IPS235_Analog.AddReg]
HKR,"MODES\1920,1080",Mode1,,"30.0-83.0,56.0-75.0,+,+"
HKR,,PreferredMode,,"1920,1080,60"
HKR,,ICMprofile,0,"IPS235.ICM"[/B]

[IPS235_Digital.AddReg]
HKR,"MODES\1920,1080",Mode1,,"30.0-83.0,56.0-75.0,+,+"
HKR,,PreferredMode,,"1920,1080,60"
HKR,,ICMprofile,0,"IPS235.ICM"

[IPS235_HDMI.AddReg]
HKR,"MODES\1920,1080",Mode1,,"30.0-83.0,56.0-61.0,+,+"
HKR,,PreferredMode,,"1920,1080,60"
HKR,,ICMprofile,0,"IPS235.ICM"

```

The relevant part (I'm guessing) is in bold. do that means 30-83 is the range for the horizontal refresh, and 56-75 is the range for the vertical refresh rate.

I opened up my xorg.conf file and all I got was this

```


Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

How would I go about adding my settings to this file?

Thanks

---

### Post by Favux on 2012-09-24
Now that you're back into Ubuntu run the command **xrandr** in a terminal and post the output.

---

### Post by Wim Sturkenboom on 2012-09-25
> **tehforum said:**
> 
How would I go about adding my settings to this file?


```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "X243W"
    _HorizSync       30.0 - 82.0_
    _VertRefresh     56.0 - 76.0_
    Option         "DPMS"
[COLOR="Red"]    Modeline "_1920x1200@50_" 164.50 1920 1952 2576 2608 1200 1225 1235 1261
[/COLOR]EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "Intel"
[COLOR="Blue"]#   Option         "UseEDID" "False"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
[COLOR="Red"]        Modes      "_1920x1200@50_"
[/COLOR]        Depth       24
    EndSubSection
EndSection

```
This is part of an old xorg.conf of mine. You can use the program _cvt_ to calculated a modeline and replace the first red line. Next adjust the second red line to reflect the new 'name' (underlined in both red lines). There is one more option that can be added to prevent the driver from probing the monitor capabilities; I've marked it in blue in the device section and it's currently commented out (so not used).

---

### Post by tehforum on 2012-09-25
> **Favux said:**
> Now that you're back into Ubuntu run the command **xrandr** in a terminal and post the output.

```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0     51.0* 
   1680x1050      52.0     53.0  
   1600x1024      54.0  
   1440x900       55.0  
   1400x1050      56.0     57.0  
   1360x768       58.0     59.0  
   1280x1024      60.0     61.0  
   1280x960       62.0  
   1152x864       63.0     64.0     65.0     66.0  
   1024x768       67.0     68.0     69.0  
   960x600        70.0  
   960x540        71.0  
   896x672        72.0  
   840x525        73.0     74.0     75.0     76.0  
   832x624        77.0  
   800x600        78.0     79.0     80.0     81.0     82.0     83.0  
   800x512        84.0  
   720x450        85.0  
   680x384        86.0     87.0  
   640x512        88.0     89.0  
   640x480        90.0     91.0     92.0     93.0  
   576x432        94.0     95.0     96.0     97.0  
   512x384        98.0     99.0    100.0  
   416x312       101.0  
   400x300       102.0    103.0    104.0    105.0  
   320x240       106.0    107.0    108.0  

```


The error message displayed on the screen is
D-SUB

OUT OF RANGE

92.6KHz/58Hz

---

### Post by Wim Sturkenboom on 2012-09-25
You just stated that Ubuntu is up and running. But you also state the error message. So is it running (with incorrect resolution), or do you get the above error message currently.

I'm totally confused at this moment.

Also note the 92.6kHz; it's outside the spec of 83kHz and that's why you get the error.

---

### Post by Favux on 2012-09-25
Hi Wim, thanks for riding to the rescue.  So tehforum, since Wim knows more about video than I do, make sure he approves of any suggestion I make.

Before you do anything else do you know how to make a backup of your current working xorg.conf and how to restore it from the command line?  And are you now able to access the Recovery Mode option in Grub when you boot?

You use Recovery Mode to get to a command line to restore the xorg.conf in case a change breaks X.

We should be able to specify the horizontal and vertical resolutions now.  I have a Nvidia dual monitor xorg.conf that should show us the proper syntax.  Also we should check the manuals and see if nvidia-settings or nvidia-xsettings let us specify them.


Edit:  Wim is a Screen section required when a Monitor section is added?

---

### Post by tehforum on 2012-09-25
> **Wim Sturkenboom said:**
> You just stated that Ubuntu is up and running. But you also state the error message. So is it running (with incorrect resolution), or do you get the above error message currently.

I'm totally confused at this moment.

Also note the 92.6kHz; it's outside the spec of 83kHz and that's why you get the error.

It's running with incorrect refresh rates - I want the 1920x1080 resolution to work.

I need to need to do all this xorg.conf stuff, and edit the xrandr settings, but I need help on that.

---

### Post by Favux on 2012-09-25
Is the Nvidia proprietary driver activated?  Why isn't there a **Driver "nvidia"** line in the Device section if it is activated?

Are you able to set horiz and vert freq using the Nvidia Control Panel?


This is the preliminary candidate xorg.conf I have:
```
Section "Device"
    Identifier "Default Device"
    Driver "nvidia"
    Option "UseEDID" "False"  # valid? correct syntax?
    Option "NoLogo" "True"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "IPS235 Flatron"
    # edid returns incorrect HorizSync
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"  # needed?
EndSection
```
Not sure of the "UseEDID" options syntax.  The option appears to be available:  [http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html)  Look at the **--use-edid, --no-use-edid**.  You might be better off with the **--use-edid-freqs, --no-use-edid-freqs** option, but I have less idea of what that syntax looks like.  That's why I want to know if the Nvidia control panel lets you set freq.s or turn off edid.

---

### Post by tehforum on 2012-09-25
Yep, NVIDIA accelerated graphics driver (version 173) is activated and currently in use.

Just searched for nvidia and found NVIDIA X Server settings, I guess that's it.

There's no option to edit the refresh rates, it says my refresh rate is 59.93Hz
and there's an option to acquire EDID to be saved on the hard drive.

---

### Post by Favux on 2012-09-25
It's the Nvidia configuration gui I'm talking about.  Is that what you are looking at?  Enter Nvidia in Dash I suppose.  Can't recall the name just now.

Alright, sounding like it is what you are looking at.  Never used a nvidia-xsettings before.  It looks like the command would be:
```
nvidia-xconfig --no-use-edid
```
if I'm understanding the manual correctly.  And that should add the Option with the correct syntax to xorg.conf after making a backup of the original, again if I am understanding the manual correctly.  Same thing with:
```
nvidia-xconfig --no-use-edid-freqs
```
**Not suggesting you try that yet.**  You haven't answered the questions about backing up and restoring from the command line.

---

### Post by tehforum on 2012-09-25
> **Favux said:**
> It's the Nvidia configuration gui I'm talking about.  Is that what you are looking at?  Enter Nvidia in Dash I suppose.  Can't recall the name just now.

Never used a nvidia-xsettings before.  It looks like the command would be:
```
nvidia-xconfig --no-use-edid
```
if I'm understanding the manual correctly.  And that should add the Option with the correct syntax to xorg.conf after making a backup of the original, again if I am understanding the manual correctly.  Same thing with:
```
nvidia-xconfig --no-use-edid-freqs
```
**Not suggesting you try that yet.**  You haven't answered the questions about backing up and restoring from the command line.


Backing up 


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


Restoring

cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Is that right?

I still don't know how to get into recovery mode, because of this error. Is there another way of accessing recovery mode?

---

### Post by Favux on 2012-09-25
Yes, you have backup and restore correct.

Looks like I was wrong about your access to Recovery Mode.  I'm guessing you don't dual boot.  Is that correct?  Otherwise the Grub selection menu should be the first thing to appear after the BIOS finishes.  That may be what is confusing me since I only have dual boot setups.  We need to figure out how to access the Grub selection menu for you.  The monitor error should be irrelevant to accessing it.

Edit:  So you were correct you use a key, except it is the Left shift key not the Esc key:  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)  So just hold down the Left shift key while it is booting so you don't miss the window.

---

### Post by tehforum on 2012-09-25
Yeah, I don't dual-boot.

I'll restart the computer now and give it a go.

edit: Left shift key didn't work. I tried restarting again and letting it load normally, and yeah, the problem is still there (as expected).

I compared the two start ups though.

When I held the left shift key, the error message just stayed on the screen, and even when I let go, the screen did not refresh and load the login screen.

Whereas, when I left it to its own devices, the error message appeared as normal, but then the screen refreshes and the login screen loaded.

So I imagine something is happening...but I can't see it so I can't do anything about it.

---

### Post by Favux on 2012-09-25
I don't understand that.  The Grub menu option should appear long before anything to do with the monitor has been loaded.  Maybe it is keeping the settings from the previous boot?

Try:
1)  Turning the computer (and monitor) off before rebooting and holding the shift key.
2)  Running the following command in a terminal:
```
sudo update-grub
```
and then rebooting and holding the shift key.
3)  Continuously tap the shift key:  [http://ubuntuforums.org/showthread.php?p=11073718](http://ubuntuforums.org/showthread.php?p=11073718)
4)  Use the installation CD, and at the very first screen, at the "boot:" prompt type "rescue" and next follow the instructions that are given.

---

### Post by tehforum on 2012-09-25
The first 3 didn't work.

Do I really need to use that rescue command first?

Or should I wait until Wim looks over the xorg.conf files and xrandr settings?

---

### Post by Favux on 2012-09-25
I think there is an option that shows up on the screen that'll do the same thing.  Whatever.

The point is you need to be able to access a root command line in order to restore your xorg.conf from backup or to edit it with the nano editor (nano /etc/X11/xorg.conf).  Otherwise you can't experiment with modifying the xorg.conf because if you break X you are stuck again.

And yes wait for Wim's thoughts.  So while waiting for that figure out how to get to the command line.

---

### Post by tehforum on 2012-09-26
Bump

---

### Post by Wim Sturkenboom on 2012-09-27
There seem to be two problems; first one is that grub does not show a menu or a garbled screen; the second one is that you don't have the correct resolution in the graphical environment. Which resolution / refresh rate do you get by default?

Can you post the contents of /var/log/Xorg.0.log (either using code tags or by attaching the file)? That will tell us which driver is actually used.

Have you tried the 'nomodeset' option in grub's kernel line as I described earlier? That might solve the issue regarding the second point; maybe in combination with a proper xorg.conf.

If 'nomodeset' does not give the required result, please provide Xorg.0.log for that situation as well.

If there is an xorg.conf generated by nVidia, please post / attach as well.

I don't have much time till the weekend, so any possible help will probably have to wait till then and it's a 'spouse permitting' situation ;)

---

### Post by Wim Sturkenboom on 2012-09-27
Edit /etc/default/grub (you need root permissions so use sudo or gksudo)

There is a line like the red italic the line below. It has a number at the end (10 if I recall correctly); remove it so the line looks like the shown one.
```

GRUB_DEFAULT=0
*[COLOR="Red"]GRUB_HIDDEN_TIMEOUT=[/COLOR]*
GRUB_HIDDEN_TIMEOUT_QUIET=true

```
The result of this change will be that you don't have to keep <shift> pressed while booting to get to the menu.

The next change is to stop grub from using fancy stuff. Find the below line in red italic.
```

# Uncomment to disable graphical terminal (grub-pc only)
*[COLOR="Red"]#GRUB_TERMINAL=console[/COLOR]*

```
And remove the '#' in the beginning.
```

# Uncomment to disable graphical terminal (grub-pc only)
*[COLOR="Red"]GRUB_TERMINAL=console[/COLOR]*

```

Save the file and run _sudo update-grub_

```

wim@i3-2120:~$ **sudo update-grub**
[sudo] password for wim: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
wim@i3-2120:~$ 

```

Next reboot your system and see if you get the grub menu. There should not be a reason to press any key for a normal boot.

---

