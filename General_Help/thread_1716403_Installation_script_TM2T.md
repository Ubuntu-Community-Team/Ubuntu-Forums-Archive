---
title: "Installation script TM2T"
date: 2011-03-28
forum: General Help
---

### Post by tembares on 2011-03-28
Hello all,

As an owner of the HP Touchsmart TM2T 2100 CTO I had to search on the internet to fine tune Ubuntu Netbook Remix, like auto-rotate.

I am a Linux noob.
Is there an expert who can develop an installation script to get the fine-tuning done by executing that script?

I am thinking about installing auto-rotate, maybe fixing the ATI-card, multitouch, ...

I know multitouch works out of the box, but I red some drivers can be updated to get the latest gestures and so on.

As Linux user who is not familiar knowing what he really is doing, such a script can be handy. It also helps new TM2T owners to work fast with the best OS there is: Ubuntu!

Thank you in advance.

---

### Post by chadmerkert on 2011-04-04
I have a TM2T 2100 CTO, and I have gotten Ubuntu 11.04 Beta working pretty well. I have an installation script that gets the hybrid graphics cards working almost perfectly. The only problem I am experiencing now is, if I suspend with the ATI card active, it resumes to a black screen. Attached is the installation script. Just chmod +x and then run install_Hybrid_Graphics.sh from the terminal using sudo, then enter your username. It turns off the unused graphic card, on login, and fixes suspend issues, and hanging on shutdown.

I also will attach a script for auto rotating the screen. The original script rotates it automatically to portrait. I made a customized version which adds a message box that asks if you want portrait or landscape, and remembers it until you logout(or kill the process). You can also comment out a line (specified in file) that will make it ask every time you close the screen what way to rotate it.

Let me know how these things work! I'd be happy to try to help anyone get their TM2T working!

ToDo:

I haven't gotten the finger print scanner working yet, but I will keep trying. HDMI out works when on the ATI graphic card, but sound through HDMI doesn't work yet. Also, the rotate button on the site of the screen doesn't work.

---

### Post by tembares on 2011-04-20
Chad, thank you very much! Sorry for my late responds, but got my TM2T just back from repair and (sorry) was not subscribed to this thread :-(

I tested your script. Wonderful!
Some comments:
- rotate.sh:
It rotates, but I have to test if it also starts automatically. I mention this because I found some auto-rotate scripts on the internet, installed them and added them to 'start-up apps', but it does not rotate automatically. 'ps -aux' shows me 'auto-rotate' was running and 'cat /sys/something_i_cannot_remember' showed me a 0 on open screen and 1 on tablet mode. Maybe it has to do something with rights, but 'ls -laF' shows me root:root. I will test yours later after start up. -> Tested: I am using Cellwriter now to enter this line, because I am using it in tablet mode. So it works.
What I like is the message. I had Cellwriter installed earlier and is a perfect app for us, TM2T users. It only starts when I come back from tablet mode to laptop mode. So, it comes too late :-)

EDIT: Todat I mentoined that when I rotated once it does not rotate twice. When excuting 'ps aux' rotate is still running.

- switch_between_cards.sh
I also had this installed.
I have the ATI prop driver activated and/or FGLRX installed. These are, if I am well informed, the open source ATI drivers that must be used. If not, please let me know :-)
If I start 'sudo bash switch_between_cards' I get the following error: cat: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
Before I saw your post I was busy getting everything done. Please read the following post and see my problem with vga-switcheroo: [Schitchable VGA/video card -> TM2T]("http://ubuntuforums.org/showthread.php?t=1734454")
If I do not activate/install ATI prop driver/FGLRX then after a switch I come in text mode and have to restart.

Thank you very much for your time for making the script. I hope this can make it a lot easier for Ubuntu-users with our laptops.

---

### Post by chadmerkert on 2011-04-21
Tembares,

Do you mean even with the driver in Additional drivers disabled, you can't switch to the ATI Card?

Installing the driver in Additional Drivers is installing the Proprietary driver(one made by ATI), not the Open Source Driver. I have not been able to get the proprietary driver to work on my TM2T yet either. I can however use HDMI out with the open-source driver. Simply remove the driver in Additional Drivers(or don't install it in the first place) and then use the switch_between_cards.sh. This is how it works for my computer

If even without the Proprietary driver installed you are unable to switch to the ATI card using the script, please post the contents of your: ```
/etc/modprobe.d/blacklist.conf
``` file as well as the output of: ```
lsmod
``` I would like to see which driver(s) are loaded. Thanks, and hopefully we can get your ATI card working!

---

### Post by tembares on 2011-04-21
> **chadmerkert said:**
> Do you mean even with the driver in Additional drivers disabled, you can't switch to the ATI Card?
I have disabled the ATI Additional driver and have installed the open source driver.

> **chadmerkert said:**
> Installing the driver in Additional Drivers is installing the Proprietary driver(one made by ATI), not the Open Source Driver. I have not been able to get the proprietary driver to work on my TM2T yet either. I can however use HDMI out with the open-source driver. Simply remove the driver in Additional Drivers(or don't install it in the first place) and then use the switch_between_cards.sh. This is how it works for my computer
So, the drivers are the same on our laptops.
When I use 'sudo switch_between_cards' I see the following in dmesg:
[I][ .. ] vga_switcheroo: client 1 refused switch
[ .. ] vga_switcheroo: setting delayed switch to client 1[/I]
It refuses to switch :-s

Permissions 'switch' as instructed [here]("https://help.ubuntu.com/community/HybridGraphics").
```
bla:~$ sudo ls -laF /sys/kernel/debug/vgaswitcheroo/switch
-rw-r--r-- 1 root plugdev 0 2011-04-22 00:16 /sys/kernel/debug/vgaswitcheroo/switch
```

EDIT+SOLVED permissions: I did the following when the permission issue solved:
```
bla:~$ sudo chown root:*username* /usr/local/bin/*
```
FYI: the dmesg lines from above still exist and switching does not work.

> **chadmerkert said:**
> If even without the Proprietary driver installed you are unable to switch to the ATI card using the script, please post the contents of your: ```
/etc/modprobe.d/blacklist.conf
```
To be sure, here is the output:
```
bla:~$ cat /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist i915
```

> **chadmerkert said:**
>  file as well as the output of: ```
lsmod
``` I would like to see which driver(s) are loaded. Thanks, and hopefully we can get your ATI card working!
```
bla:~$ lsmod
Module                  Size  Used by
michael_mic            12540  8 
arc4                   12473  4 
i915                  450979  7 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
rfcomm                 38125  11 
sco                    17779  2 
snd_hda_codec_idt      60537  1 
bnep                   17785  2 
l2cap                  48656  18 rfcomm,bnep
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
wacom                  41292  0 
uvcvideo               66851  0 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  18160  4 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
videodev               75143  1 uvcvideo
snd_seq_midi           13132  0 
radeon                925124  1 
snd_rawmidi            25269  1 snd_seq_midi
hp_wmi                 13418  0 
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13666  1 hp_wmi
lib80211_crypt_tkip    17203  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2642531  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59039  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  2 i915,radeon
intel_ips              17769  0 
serio_raw              12990  0 
drm                   184133  6 i915,radeon,ttm,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13184  2 i915,radeon
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
r8169                  46630  0 
libahci                25548  1 ahci
```

Thanks!

---

### Post by chadmerkert on 2011-04-22
Tembares,

It looks like the proper graphic drivers are loaded.

What version of Ubuntu are you using? Kubuntu? 64-bit or 32-bit? 11.04 beta? Unity, KDE, Gnome?

Also, go to a terminal and post the output from these commands: ```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

---

### Post by tembares on 2011-04-22
> **chadmerkert said:**
> Tembares,

It looks like the proper graphic drivers are loaded.

What version of Ubuntu are you using? Kubuntu? 64-bit or 32-bit? 11.04 beta? Unity, KDE, Gnome?

Also, go to a terminal and post the output from these commands: ```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

I am using Ubuntu Natty beta 2 with Unity 32-bit.

```
bla:~$ cat /sys/kernel/debug/vgaswitcheroo/switch
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

```
bla:~$ echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
bla:~$ 
```

Some extras to see that switch works:
```
bla:~$ echo ON > /sys/kernel/debug/vgaswitcheroo/switch
bla:~$ cat /sys/kernel/debug/vgaswitcheroo/switch
0:DIS: :Pwr:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

But real switching does not work:
```
bla:~$ echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
bla:~$ cat /sys/kernel/debug/vgaswitcheroo/switch
0:DIS: :Pwr:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

I tried to find what the messages in dmesg mean, but could not find a good explanation.

Thank you for your time!

---

### Post by chadmerkert on 2011-04-22
Have you tried switching the cards manually?
To switch to the ATI card:
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
```
```
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```
Then log out, and log back in. Once logged back in, type:
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```

It should now show up as:
```
0:DIS:+:Pwr:0000:01:00.0
1:IGD: :Off:0000:00:02.0
```
Instead of:
```
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

This means you are now using the ATI card. Does this work? Or do you get thrown into text session?

---

### Post by tembares on 2011-04-22
When I turn ON and DDIS and log out an on, then this is the output of 'switch':
```
Commands: [low, high, off]

Status:
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

It seems (D)DIS doesn't work.

---

### Post by chadmerkert on 2011-04-22
Hmm... That should have worked. You have permission to edit the switch file. The two commands to switch the graphics cards are
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
```Which should switch to the Intel card, and:```
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
``` Which should switch to the ATI card. A logout and log back in is required for the change to take effect. This is the site that I found the script on, and learned how to switch the cards. You may want to take a look there: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

My last thought would be to open up Synaptic Package Manager, and search for Radeon. Then install or reinstall: xserver-xorg-video-radeon, radeontool, xserver-xorg-video-ati, and remove fglrx if it is installed. reboot, and try switching the cards again. 

If that doesn't work, my last suggestion would be a clean install.Just use the install_Hybrid_Graphics.sh script. I am wondering if installing the ATI proprietary driver, it messed something up.

Hope this helps.

---

### Post by tembares on 2011-04-22
You say log out and on.
I restarted. To be sure, you are talking about logging on again without restart/reboot?
Going to do a nap now. Will test it later today :-)

---

### Post by chadmerkert on 2011-04-22
Yes, only log out, and then back in again. If you reboot, the Intel card will automatically be used again. If you switch the cards, and just log out of your account, and back in again, does the switch file say you are on the DIS card?

---

### Post by tembares on 2011-04-22
F*cking hell!
YES!!! It works and have even the extended mode.

Only touch does a little bit strange now. The aspect of touch (width of both screens (laptop + HDMI)) is different than the the screen width of the laptop. Do you have the same issue with that?

---

### Post by chadmerkert on 2011-04-22
hahaha, Good to hear! Do you know what it was that fixed it?

I have the tablet being uncalibrated when using HDMI out problem as well. It can be fixed with the Wacom Tablet Area property. I have been able to manually edit this to get it to work right, but it is a bit of a pain. For example, if you are using HDMI out, and extending your desktop onto another screen at 1280x800, you can type:
```
xinput --set-prop 10 "Wacom Tablet Area" 0, 0, 5222, 1632
xinput --set-prop 11 "Wacom Tablet Area" 0, 0, 52224, 16320
xinput --set-prop 12 "Wacom Tablet Area" 0, 0, 52224, 16320
```

I will look around and see if someone has made a script that changes the Wacom Calibration when using extended desktop. If not, I will give it a shot! Can't be too hard. Just figure out the Virtual Desktop Size, and then do some math, to figure out what to put as the tablet area coordinates.

You can play around with the Wacom Tablet Area command yourself.
to see the ID's for the different tablet devices:
```
xinput --list
```
To see what the current tablet area is replace 10 with the device ID of the tablet device you want to see:
```
xinput --list-props 10 | grep "Wacom Tablet Area"
```
to set new coordinates replace 10 with the device ID you want to set:
```
xinput --set-prop 10 "Wacom Tablet Area" 0, 0, 5222, 1632
```

I'll post back here if I find or make a script to do it automatically! :)

---

### Post by tembares on 2011-04-22
My fault was that I rebooted/restarted every time and not logged off and on.
I moved your script files to /usr/local/bin. I had to set the chown to root:*username* to let it work without 'sudo'.
I also set the permissions of /sys/kernel/debug/vgaswitcheroo/switch to root:plugdev. I do not know if this is needed.

I suggest to add an option at 'switch_between_cards', namely to 'switch and log off' or to 'switch only'.
Somewhere in my search for the solution to get ATI work I red that there is also a possibility to restart gdm. Maybe this can be used instead of logging off and on. Let me try later to find this solution.

Your 'rotate'-script works for me one time after start-up: I rotate, select my choice, do my thing, rotate back and the screen rotates back again. If I do this for a second time, the screen does not rotate, there are also no notifications about rotating.
If I run 'ps aux' 'rotate' is active and running.
If I start 'rotate' in a terminal I can rotate as much as I can.

Something else:
In a thread I asked how I can find out who made the HP webcam driver. I would like to know if there is an option to 'rotate/vertical flip' the webcam.  When the screen has been rotated, then I want to flip the webcam also. That makes Skype easy and fun in Tablet mode :-)

Let's keep in contact. I appreciate that you are spending so much time! THANK YOU!

---

### Post by chadmerkert on 2011-04-22
I found out how to fix the calibration problem when using extended desktop. I am uploading a script that you can execute after extending the desktop to get your tablet calibrated properly. I am trying to make a script that is always running in the background and automatically fix when extended, but it causes the mouse to freeze quickly every few seconds... really annoying! So here is a script to fix it, but it has to be run every time you change the extended desktops size or location.

As for the switch cards script, are you using unity? if so, then open the script with a text editor, and replace every instance of gnome-classic with gnome. I had it set this way, because I use the classic gnome desktop.

Also, which rotate script are you using? the one I made is rotate.sh, which should ask you how you want to rotate when converting to tablet mode. I like this way better, because I can choose which way to rotate the screen. If you always use it one way, you can open the file and comment out the line ```
	ROTATE_PREFERENCE="" #Comment out this line to remember your rotate preference for the session.
``` by placing a # at the beginning of the line. This way, it will ask you which way to rotate the screen, and then rotate it that way for the rest of your session or until you kill the process and start it again.

As for rotating the video, I will look into that. I'm pretty sure there is a way. Perhaps I can add that to my rotate script! :D

Hope this all helps!

---

### Post by tembares on 2011-04-22
> **chadmerkert said:**
> I found out how to fix the calibration problem when using extended desktop. I am uploading a script that you can execute after extending the desktop to get your tablet calibrated properly. I am trying to make a script that is always running in the background and automatically fix when extended, but it causes the mouse to freeze quickly every few seconds... really annoying! So here is a script to fix it, but it has to be run every time you change the extended desktops size or location.
The script messed it up. When I switched to the ATI card and used your script my laptop screen comes as 'a layer' over the extended screen on my HDMI, my TV. And I do not know how to get it back, because when I run it for the second time, it still exists.

> **chadmerkert said:**
> As for the switch cards script, are you using unity? if so, then open the script with a text editor, and replace every instance of gnome-classic with gnome. I had it set this way, because I use the classic gnome desktop.
So I was not the only one with the idea to log off automatically. By chancing gnome-classic into gnome it really works!
Why are you not using Unity. It works so well in tablet mode!

> **chadmerkert said:**
> Also, which rotate script are you using? the one I made is rotate.sh, which should ask you how you want to rotate when converting to tablet mode. I like this way better, because I can choose which way to rotate the screen. If you always use it one way, you can open the file and comment out the line ```
	ROTATE_PREFERENCE="" #Comment out this line to remember your rotate preference for the session.
``` by placing a # at the beginning of the line. This way, it will ask you which way to rotate the screen, and then rotate it that way for the rest of your session or until you kill the process and start it again.
Ofcourse I am using your rotating script. I renamed it to rotate, so without '.sh' and moved it to /usr/local/bin. I commented the ROTATE_REFERENCE-line and indeed, it only asks one time how to rotate.
I can only rotate once back and forth. A second time rotating does not work. Maybe because of a variable setting that loops the code. I will have a look also myself.

> **chadmerkert said:**
> As for rotating the video, I will look into that. I'm pretty sure there is a way. Perhaps I can add that to my rotate script! :D
I know there are programs who can do it. So if they can do it, then 'we' have to be able, too :D  And I am not a fan of using to much extended programs to fix things. I hope by using a modprobe-command with a 'vflip' or something like that, that is better.

Again, thanks!

---

### Post by chadmerkert on 2011-04-22
I don't use Unity, because I like my Gnome! I will probably end up switching to Gnome3 once it's ready and stable for Ubuntu! But Unity didn't seem customizable enough for my tastes.

As for the display rotate problem, I discovered what you were talking about. When you try to rotate the laptop screen, but not the HDMI screen, it gets all glitchy! I fixed the rotate script, which should make it work properly now.

Let me know if it works! :)

---

### Post by tembares on 2011-04-22
Let me be short:
it works now.

Do you have an idea about HDMI extended_desktop_calibrate issue?

Where did you find info about LVDS? I cannot find an explanation, only in code.

---

### Post by chadmerkert on 2011-04-22
Is the tablet calibrated properly when connected to an HDMI display? I added the code to calibrate it when you rotate the screen. If you change the size of the external display resolution, then the calibration will be off again. rotating the screen should run the calibration code again, but if you don't want to you should be able to run the extended_desktop_calibrate.sh

As for the LVDS I was playing around with xrandr to get the rotation working properly, and saw it in the output of the command xrandr -q which lists information about your display setup.

LVDS is the laptop display when connected to an HDMI.
HDMI-0 is the HDMI screen.
LVDS2 is the laptop display when not connected to an HDMI screen(on intel card)

So is everything with the rotate script and calibration working properly?

---

### Post by tembares on 2011-04-22
What happend after the calibration is that the laptop screen is not calibrated anymore.
The HDMI-screen gives me 100% view, the screen on the laptop not.
The screen on the laptop finishes from left to right for about 65%, from top to bottom about 80%.

```
bla:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      50.0*+   60.0  
   1920x1080i     30.0     25.0  
VGA-0 disconnected (normal left inverted right x axis y axis
```

The resolution of the HDMI is also used for the laptop screen.
Can this be changed?

---

### Post by chadmerkert on 2011-04-23
Edit: Oh... your using Unity right? Just for the heck of it, log in to Ubuntu Classic! I just tried Unity, and it seems very glitchy with the Multi display, and rotating!
So even after using the most recent rotate script the touch screen isn't calibrated properly when you have the external display plugged in? The commands I used are:

```
xsetwacom --set 10 "MapToOutput" LVDS
xsetwacom --set 11 "MapToOutput" LVDS
xsetwacom --set 12 "MapToOutput" LVDS
```

These commands are basically setting the tablet area to area of the laptop display instead of the current desktop size. Perhaps your tablet input ID's are different. Try the command:
```
xinput --list
``` and see what the ID numbers are for your Wacom inputs. If they are different you may need to replace these number in the calibration script and the rotation script. You can also just try these command straight in the command line and see if it fixes the calibration. Let me know if you get the calibration working properly.


As for your other problem, I'm not exactly sure I understand. Here is the output of my xrandr -q:```
chad@Ubuntu-HP-TouchSmart-tm2:~$ xrandr -q
Screen 0: minimum 320 x 200, current 2720 x 900, maximum 8192 x 8192
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 connected 1440x900+1280+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0 +
   1440x900       59.9* 
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
VGA-0 disconnected (normal left inverted right x axis y axis)

```

One thing I noticed is your external display is only recognizing 2 resolutions. I am wondering if that is causing problems. have you tried adjusting the resolution in System>Preferences>Monitors? Also one thing that I found was glitchy is that in Monitor settings if I move the position of the external monitor relative to the laptop display, it gets messed up sometime. I found that moving it to the top or bottom, and then back, it works properly then. The driver seems to be a little bit messed up. I also noticed that if I have the laptop display rotated and the external display not rotated, if I rotate the Compiz cube, it makes the laptop display glitched up! I can unrotate and rotate the screen a few times to fix it though.... really weird though.

Keep me posted on your progress! Hopefully we can get it working properly!

---

### Post by tembares on 2011-04-23
I will reply on your previous post later. If have to go out, doing the family thing :-)

Yesterday I shut down my laptop in tablet mode. Today when I started Ubuntu in laptop mode my touchpad did not work. Going into tablet and back made it work again.

I will check your script later to see if I can find a solution for that, but as told you before I have to leave my laptop some time.

---

### Post by tembares on 2011-04-23
A fast reply on the code:

Can't you change
```
xsetwacom set 10 LVDS
xsetwacom set 11 LVDS
xsetwacom set 12 LVDS
```
into

```
xsetwacom set "Wacom ISDv4 E3 Finger touch" LVDS
xsetwacom set "Wacom ISDv4 E3 Pen eraser" LVDS
xsetwacom set "Wacom ISDv4 E3 Pen stylus" LVDS
```
Maybe this makes it more generally when other wants to use the script, too.

Will come back later

---

### Post by chadmerkert on 2011-04-23
Good Catch on the mouse setting! I just added a line that enables the mouse first thing when the script is loaded. That way when you log in, it will make sure the touch pad is enabled, if it was disabled last time it was shut down. I also changed the names from their ID numbers to their names for the Calibration part! I also discovered that when you log out and in again, it seems like the script stays running, so when you log back in you get 2, 3, 4... scripts running at the same time. I'm working on adding the ability to kill previous sessions of the script when it loads itself. that way it should only stay at one script running at a time. Should be able to post the appended script later today! :) Hope you are enjoying your family time!

---

### Post by chadmerkert on 2011-04-23
New Script Time! Here's the latest rotate script. It should fix the TouchPad problem. It should also make sure that only rotate script is running at one time. It also calls the Wacom components by name now instead of ID number, in hope that it will be more universal.

One interesting issue I am having is that when connected to an external monitor, if I rotate the screen, and then try to switch to a different workspace, it makes the laptop screen all glitchy. Unrotating and rotating again fixes it, but it's a bit inconvenient. I don't know if I will be able to fix this though... I think it's a problem with Compiz.

Let me know how it works, or if there is anything that could be improved!

Are you still using this script in Unity? How's it working for you? I need to do a little more testing with Unity.

---

### Post by tembares on 2011-04-23
> **chadmerkert said:**
> LVDS is the laptop display when connected to an HDMI.
HDMI-0 is the HDMI screen.
LVDS2 is the laptop display when not connected to an HDMI screen(on intel card)

The rotating and enabling of the touchpad works fine.

I was still thinking about the resolutions when an extended display is connect and when not.

By adding the following makes your script a screen_handling-script and not only a rotating-script.

My idea is:
If LVDS2 is active, then setwacom ... LVDS2
If LVDS  is active, then setwacom ... LVDS + HDMI

In my opinion this calibrates the cursor for the touchscreen, because the 'new' width is laptop-width+HDMI-width.

You have to add this to your 'rotate'-script because that is the one which runs at start-up. 'switch_between_cards' only runs on demand.

And did you remove the Cellwriter option at start-up? I miss it. I cannot get the icon in the applet-bar on top anymore. This makes using the laptop in tablet mode difficult, because if I want to enter something I have to use my keyboard.

I think that when I start up my laptop in tablet mode, the screen does to rotate. I have to rotate it to laptop and back to get it rotated in tablet mode.
Is it possible to check cat /dev/.../tablet (or something like that) and see if it is in tablet or laptop mode. If tablet, than touchpad can be disabled and the screen has to be rotated.

Let me start by saying that I do not know what the technical difference is between Ubuntu Classic and Ubuntu Unity. I think it is only a shell, nothing else.

Having that thought it should not made any difference using Classic or Unity.

The nice thing about Unity is the launcher on the left. With the settings it is possible to put it anywhere. Also auto-hide and some other options are there. Starting and switching between applications are easy to do with Unity.
I do not know if the Super-keys work the same in Classic. For instance Super-S shows me the 4 workspaces where I can drag and drop applications between workspaces.
Clicking Super only shows me a screen with short cuts to Media-, Internet-, More Apps, Find Files and some other possibilities. It is also possible to hit Super-key and type the name of the app to start one.

I hope you appreciate the feedback. Sometimes it is difficult to feel if something is said in a good way or not. Let me say that all is said in positive way!

Enjoy!

Uhhh... In what timezone do you live? I live on St Maarten, UTC -4.

---

### Post by tembares on 2011-04-23
Hey Chad,

Ready for a new challenge?
I had an idea about rotating.
When I rotate the screen you come up with a pop-up with 2 choices: invert and portrait.
The first time you have to have 2 options, if the 'line' is commented then the last option is stored.
My idea is the following:
Remember the t way of rotation and always pop-up with the other option.
So, if I choose invert the first time, the second time I rotate from laptop mode it rotates to invert with a 3 seconds pop-up with the portrait rotation.

How does that sound :-)

---

### Post by chadmerkert on 2011-04-24
I live on the Eastern Time Zone of the US, which is GMT-5. We are on Daylight Savings time now though, so I don't know if that changes things.

The script uses xsetwacom "MapToOutput" to try to calibrate it to both LVDS and LVDS2 when it is rotated, so it should calibrate whether you are on the ATI card or the Intel card.

I use Onboard, but I will add back some code to launch a keyboard(cellwritter or onboard) when rotated.

Also, when I start my laptop up in tablet mode, after I log in, and the script starts, it detects that it is in tablet mode, and asks which way I want to rotate. Does it work for you?

I do think that there are some significant differences between Unity and Gnome Classic, but it should for the most part work. I think that any differences might actually come from compiz. I really should try to start using Unity more. It is pretty nice.

Also, I like your idea for the timeout of 3 seconds before it auto-rotates to your preference. I already started adding the code for that, and should be able to upload a new script later today.

P.S. What's your name? (I want to add it in the comments of the script for who made it, along with my name.) :)

---

### Post by chadmerkert on 2011-04-25
Okay, here is the latest script. It has a 3 second change your rotate preference box, and added support for both CellWriter and OnBoard. To use either of these, uncomment the line near the top of the file for that keyboard program. There are comments in the file to tell you which line to uncomment.

Everything seems to working very well. Let me know if you find any problems, or any thing else it should do! :)

---

### Post by tembares on 2011-04-26
> **chadmerkert said:**
> Okay, here is the latest script. It has a 3 second change your rotate preference box, and added support for both CellWriter and OnBoard. To use either of these, uncomment the line near the top of the file for that keyboard program. There are comments in the file to tell you which line to uncomment.

Everything seems to working very well. Let me know if you find any problems, or any thing else it should do! :)

Hey Chad,
Thank you for the script.
So far so good, but I need to test the touch calibrating when I have HDMI connected to my laptop.

I am still thinking about that.
In every section of the rotate script you use LVSD. I think this works as long an extended screen has not been connected.

Because the desktop is extended, the width of the 'screen' is LVSD+HDMI-0. To calibrate the touch for the LVSD only, you also need to 'extend' the width for the setwacom.

Because now the 2 scripts are 'working' with each other 'rotate' does not cover the meaning of the script anymore. That is why I should call it 'screen_handler' or something like that.

I hope I could explain clear enough with what I mean. If not, no problem, let me know.

---

### Post by chadmerkert on 2011-04-26
Hey Tembares,

The command:
```
xsetwacom set "Wacom ISDv4 E3 Finger touch" "MapToOutput" LVDS
```
tells xsetwacom to use the size of LVDS to calibrate instead of LVDS and HDMI-0 together. LVDS is what the laptop screen is called when an HDMI cable is plugged in. When no HDMI cable is plugged in, it is called LVDS2.
Hope this makes sense.

Since the script is mainly a rotate script, it just has a few extra features(calibrate display, disable touchpad), I will leave the name the same. The name would make more sense to someone looking for a way to rotate their screen. It just has a few extra benefits other than just rotating the display! :)

One more thing I will test is with VGA output. I use the VGA out put more often than the HDMI, so I will test the script when using a VGA output.

I looked into the rotating of the camera, and it looks a bit harder than I anticipated. I doubt it is something that I would be able to add to the script.

Let me know if you run into any problems with the script.

We made a pretty awesome script here! Now, any other areas of the TM2T that could be improved? :D

---

### Post by tembares on 2011-04-26
Did you know that playing movies with Movie Player on the ATI card gives very strange colors? When using the intergrated Intel one, there is no problem.

I tested the extended screen again and the calibration is not okay.

1) the resolution is still not right as described earlier.
2) the calibration of the touch screen is not okay as described earlier.

A new option to be added could be to make the right click workable. I am trying to avoid right clicking, but sometimes I have to. Then I use the pen or the gesture on the screen.

To calibrate the touchscreen the screen width of the resolution of both screens has to be added. Then it will work, for sure :-) ... if the resolutions of both screens are right configured, ofcourse :-)

Why the laptop screen does not goes to its own resolution I do not understand. Well, Unity ends fine and the vertical scroll bar also.
But when I goes down with my cursor by touchpad then the cursor disappears. When I go up with the cursor it takes a while before it's visible again. Maybe it is because the resolution of the HDMI screen is higher than the laptop screen one so that the desktop is set to the highest resolution.
That makes calibration of the touchscreen not more difficult, because you have to take the witdh of LVSD or, when intergrated is selected, LVSD2.

And this is the reason why I think that the rotate script will become more than only rotating ;-)

Looking forward to your feedback on this.

---

### Post by chadmerkert on 2011-04-26
I did not know about the video on the ATI card. Is it on the laptop screen or an external display? I think I played a video on the ATI card and it looked fine on the laptop screen. I'll test it out, and see if I can get it to do that.

Also, can you post the output of ```
xrandr -q
``` for both the Intel Card, and the ATI card with an HDMI monitor plugged in? Also, with an HDMI screen connected try running the command: ```
xsetwacom --set "Wacom ISDv4 E3 Pen stylus" "MapToOutput" LVDS
``` replacing the Wacom name with all three wacom device names from xinput --list If it does not calibrate the screen, post the error message.

As for the right click, have you tried tapping with two fingers at once anywhere on the touchpad? it should right click! also if you tap at the very very bottom right, it will right click, but I just use the two finger right click. I actually miss it when I'm on windows! :D

Also, when you have an external display that is higher resolution than the laptop screen, you will have an area of dead space that the mouse can get lost in sometimes. For example if the external display has a higher vertical resolution, you will have an area either above or below the laptop screen that the mouse can get lost in. It can be a little annoying, but it isn't anything too serious, and I don't think it's something that a script could fix. It is probably something that needs to be fixed in X or Gnome.

Also, have you tried adjusting the resolution in System>Preferences>Monitors?

---

### Post by tembares on 2011-04-26
Does switch_between_cards still work for you?
This evening I updated Natty and there was a OpenGL-update.
After the update the script does not work anymore for me.

It has something to do with the permission, but still I did not find that out.
Stand bye.

Solution:
I enabled auto log on. This does not work.
You can set auto log on, but with a 2 seconds delay to have the possibility to switch to an other user.

---

### Post by chadmerkert on 2011-04-26
Wow, yes, mine still works. I checked for updates, and rebooted as well, just to make sure. Still working fine for me.

What does the script do? Does it show you which card is currently active? I'm wondering if the /etc/gdm/PostLogin/Default file got overwritten by an update and removed the changes my script made to it. Tell me what the script does, and also the output of ```
cat /etc/gdm/PostLogin/Default
```

---

### Post by tembares on 2011-04-26
Starting the script I see the pop-up, not showing which card is active and powered on.

See this post of me with this issue. I think it is a OpenGL/Natty thing :-)
[http://ubuntuforums.org/showthread.php?t=1740298]("http://ubuntuforums.org/showthread.php?t=1740298")

cat /etc/gdm/PostLogin/Default is still there as installed.

---

### Post by tembares on 2011-04-26
> **chadmerkert said:**
> I did not know about the video on the ATI card. Is it on the laptop screen or an external display? I think I played a video on the ATI card and it looked fine on the laptop screen. I'll test it out, and see if I can get it to do that.

Also, can you post the output of ```
xrandr -q
``` for both the Intel Card, and the ATI card with an HDMI monitor plugged in? Also, with an HDMI screen connected try running the command: ```
xsetwacom --set "Wacom ISDv4 E3 Pen stylus" "MapToOutput" LVDS
``` replacing the Wacom name with all three wacom device names from xinput --list If it does not calibrate the screen, post the error message.

As for the right click, have you tried tapping with two fingers at once anywhere on the touchpad? it should right click! also if you tap at the very very bottom right, it will right click, but I just use the two finger right click. I actually miss it when I'm on windows! :D

Also, when you have an external display that is higher resolution than the laptop screen, you will have an area of dead space that the mouse can get lost in sometimes. For example if the external display has a higher vertical resolution, you will have an area either above or below the laptop screen that the mouse can get lost in. It can be a little annoying, but it isn't anything too serious, and I don't think it's something that a script could fix. It is probably something that needs to be fixed in X or Gnome.

Also, have you tried adjusting the resolution in System>Preferences>Monitors?

```
bla:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 8192 x 8192
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      50.0 +   60.0* 
   1920x1080i     30.0     25.0  
VGA-0 disconnected (normal left inverted right x axis y axis)
```

Entering manually
```
$ xsetwacom --set "Wacom ISDv4 E3 Finger touch" "MapToOutput" LVDS
```
calibrates the touch screen and, using Pen ..., also the pen.

Do we have to rebuild the script or is there something weird going on. Because before entering that manually it was NOT calibrated.

And thanks for the gesture tip. Touch with two fingers works great!

---

### Post by tembares on 2011-04-26
Yep, tested it.
When starting up, touch is NOT calibrated.
After manually executing the xsetwacom line it is calibrated.

Is there a possibility that the IF-set is not correct?
EDIT: AFAIK I see in the script that
```
#Recalibrate touch screen if using extended desktop
	xsetwacom set "Wacom ISDv4 E3 Finger touch" "MapToOutput" LVDS
	xsetwacom set "Wacom ISDv4 E3 Pen eraser" "MapToOutput" LVDS
	xsetwacom set "Wacom ISDv4 E3 Pen stylus" "MapToOutput" LVDS
```
is executed when the screen has been rotated. As long the screen is not rotated calibrating has not been done.
Something like this has to be added to the script:
- Read which graphic card is used
  - if Intel, then xsetwacom with LVSD2
  - if ATI  , then xsetwacom with LVSD

By doing this the script becomes much more than only rotating. Also calibrating the screen has been implemented by then.

BTW: After rebooting I have to set the permissions again to get 'switch_between_cards' work :-(

Solution:
I enabled auto log on. This does not work.
You can set auto log on, but with a 2 seconds delay to have the possibility to switch to an other user.

---

### Post by chadmerkert on 2011-04-27
Glad to hear the two finger touch works well! I really like it, and miss it when using Windows (thankfully not too often!)

As for the script, I didn't bother putting the calibration commands in an IF statement, because if either LVDS or LVDS2 are not present, the command just exits with an error. This error will not cause any problems though, so if it is not connected, the commands basically don't do anything. I have added the calibrate lines to the beginning of the file now, to run them when the script is first executed. I have also added LVDS2 calibration lines, to make it work when connected to a VGA monitor with the Intel Card. 
Let me know if the calibration is now correct. I don't see any logical reason as to why it wouldn't! :confused:

Here is the script, and let me know how it works! :)

---

### Post by tembares on 2011-04-27
The calibration works fine now.
Maybe a '> NULL' after the commands makes it more beautiful so that the errors doesn't appear.

Now I am getting nervous because tomorrow is the day: release day of Natty.

---

### Post by tembares on 2011-04-29
Hello Chad,
Busy with Natty?
I did a clean install and ran the script.
I saw that /sys/kernel/debug/vgaswitcheroo/switch was still root:root and that both cards are powered on.

Maybe you can rewrite the install-script with the latest news.
I received a private post about the security hole. Your suggestion was a good compromise according the settings.

Onboard keyboard is better than cellwriter. Do you know what the scanning mode means? I tried to find info about it, but couldn't find anything about it.

---

### Post by tembares on 2011-04-29
Chad,

Maybe you can add the script on [this]("https://wiki.edubuntu.org/HP%20TouchSmart%20tm2") page which is under Graphics. That puts the ATI card OFF by default.

---

### Post by tembares on 2011-04-29
To make the script working by itself an addition to StartUp will make it all perfect.
You can start a program by adding a file to ~/.config/autostart/

If I come up with an other idea, I will let you know!

---

### Post by chadmerkert on 2011-04-29
Hey Tembares,

Sorry, I was away from my computer for most of the day. I just did a fresh install of 11.04. The script works after some tweaking. I have attached a new install script. I think the problem is fixed after doing it a new way. This also addresses the security hole(as far as I know). 
In the /etc/gdm/PostLogin/Default file, it should look like this:
```
#!/bin/sh
chmod -R 705 /sys/kernel/debug
chown -R USERNAME:USERNAME /sys/kernel/debug/vgaswitcheroo
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

This is the change I made in the installation script. It only gives the /sys/kernel/debug read/execute access, and doesn't chown it to your username. It should be more secure, and also works perfectly.

I hope this helps. Let me know if you run into problems with it! :)

---

### Post by tembares on 2011-04-29
Been a while away, too.

I changed the script for myself already, but for the readers and new users it would be nice to have an updated zip in the first post with your attachment. Then they do not have to read everything over and over again :-)  The new solution works fine for me.

Did you read the idea of adding the 'autostart' option? What is your idea about it?

I am using onboard now, too. I posted a question to add a minimize button on the keyboard. How do you do that now? And do you know what the scanning mode is?

---

### Post by chadmerkert on 2011-04-29
I already updated the zip in the first post! :)

Also, I'm not sure what scanning is on onboard... If you find out, I'm curious as well...

Also, I'm not sure I understand what you mean by autostart. What do you want to autostart?

And also, there is a minimize button for OnBoard. Or were you thinking of something else?

---

### Post by tembares on 2011-04-29
> **chadmerkert said:**
> I already updated the zip in the first post! :)
Great

> **chadmerkert said:**
> Also, I'm not sure what scanning is on onboard... If you find out, I'm curious as well...
I did not find a manual of onboard.

> **chadmerkert said:**
> Also, I'm not sure I understand what you mean by autostart. What do you want to autostart?
When Ubuntu starts, rotate is not started by itself, until you added rotate in System->Administration->Startup Apps.
To add a startup file in ~/.config/autostart this adding can be done by your script.

> **chadmerkert said:**
> And also, there is a minimize button for OnBoard. Or were you thinking of something else?
Do you mean the minimize button next to the 'end' and 'maximize' button? It is so hard to touch minimize in one time. If there is a minimize button on the keyboard which is big enough, minimizing the keyboard will go easier than ever :-)

---

### Post by chadmerkert on 2011-04-29
Ahh, I see what you mean. I will add that to the install script so it autostarts! Would make it easier!

Also, in Gnome Classic, I can just click on the OnBoard icon in the bottom panel to minimize it. But in Unity, I like the status icon. Under OnBoard settings, there is an option for "Show status Icon" which adds an icon to the notification area. You can then tap on this and slide down to Hide or Show Onboard. Works nicely, and less chance you accidentally close or maximize it! :D Hope this helps! 

Oh, and if you haven't already, using OnBoard for the lock screen is always a good thing to do! Lets you unlock the computer from tablet mode!

---

### Post by tembares on 2011-04-30
It seems /etc/gdm/PostLogin/Default does not run at start up, or I have done something wrong:
```
bla:/etc/gdm/PostLogin$ cat Default
#!/bin/sh
chmod -R 705 /sys/kernel/debug
chown -R bla:bla /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
Give me a hint :-)
Running this script manually then it works fine.

I know what the problem is: again, automatically log on. Strange, btw.

---

### Post by dugh on 2011-04-30
How did you get 11.04 installed and running on the tm2t?  

The installer just hangs for me.  So I installed 10.10 and upgraded to 11.04 and that worked, but I just get a blank screen on boot after grub, and none of these fixes work: [http://ubuntuforums.org/showthread.php?p=10743950](http://ubuntuforums.org/showthread.php?p=10743950)

Are you both using the 32 bit version?  I tried installing the 32 bit version but again the installer just hangs.

---

### Post by tembares on 2011-04-30
> **dugh said:**
> How did you get 11.04 installed and running on the tm2t?  

The installer just hangs for me.  So I installed 10.10 and upgraded to 11.04 and that worked, but I just get a blank screen on boot after grub, and none of these fixes work: [http://ubuntuforums.org/showthread.php?p=10743950](http://ubuntuforums.org/showthread.php?p=10743950)

Are you both using the 32 bit version?  I tried installing the 32 bit version but again the installer just hangs.

When starting from USB/CD you see a keyboard and 'circle with person inside' on the screen. Click a key, click enter to select English and press F6. Select 'nomodeset' and start setup.
After setup Ubuntu Natty works out of the box, but need this script to make it better :-)

Let me know if you have more questions.

---

### Post by chadmerkert on 2011-04-30
Tembares, I did you make sure it is set as executable? try
```
sudo chmod +x /etc/gdm/PostLogin/Default
```
And if that doesn't work... try changing the second line to
```
chown -R bla:bla /sys/kernel/debug/vgaswitcheroo
```

Dugh, Glad to see someone else in this thread! I got the 64-bit version running, but it does fight with you a little on the installation. The black screen is a problem with the back light. If you ever get a black screen, try turning the back light up. Once you get 11.04 installed with nomodeset like tembares recommended, either run the installation script for the hybrid graphics, or add 
```
blacklist i915
```
to the end of
```
/etc/modprobe.d/blacklist.conf
```
This fixes a problem with the two graphics cards conflicting.

Hope this help, and if you have any questions or problems, ask away!

---

### Post by dugh on 2011-04-30
It's still not booting, even in recovery mode, and even with various flags like nomodeset

First I found the error message:
> failed to get i915 symbols, graphics turbo disabled

and I added some things to blacklist.conf

but now I keep getting the error message:

> phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

and there is no way to fix it since I can't boot up to the os, and it's already marked as fixed in the bug report so that's it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659143)

ATI did release brand new drivers a few days ago:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
but again I can't even get through the boot sequence in order to try anything else - I'm going to try linux mint or opensuse later on, or else xubuntu/lubuntu

---

### Post by chadmerkert on 2011-04-30
dugh,

I'm sorry it's not working. Have you tried going through the installation process a second time? It took me a few tries to get it working. 

I recommend right after a fresh installation, booting with the nomodeset flag, and using my installation script to get the hybrid graphics working properly.

I tried using Opensuse 11.4, and I got it working okay, but after getting Ubuntu 11.04 working, I am glad I came back to Ubunu. I think it is definitely worth a little fighting to get it to work!

So before you try installing another distro, I would recommend giving it another go from scratch with Ubuntu. Best of luck, and we are here to help! Keep us informed as to your status.

EDIT: Also, don't install the Proprietary Graphics Driver. It doesn't work! Use the OpenSource one(installed by default.) If I can get the proprietary driver working, i'll post about it here. I tried the latest from the AMD site as well, and still no luck!

---

### Post by dugh on 2011-05-04
> **chadmerkert said:**
> dugh,
I recommend right after a fresh installation, booting with the nomodeset flag, and using my installation script to get the hybrid graphics working properly.


Really appreciate your help and scripts.
It's working now using nomodeset the first time I booted as you suggested.
And rotating works, along with xournal for note taking and gimp w/pressure sensitivity.

---

### Post by rougered on 2011-05-04
Hi!
       first of ll i wanted to say that i can use my computer with Natty thanks to your scripts...so ... thank you very much!!

however i still have a problem with the rotation of my screen...i get the error

rotate.sh: 104: [[: not found

i run the command as 
sudo sh rotate.sh
any suggestion?

thank you
Riccardo

---

### Post by chadmerkert on 2011-05-04
rougered, 
Glad things are working for you. As for the rotate script, you shouldn't need to run it as sudo. Also instead of sh rotate.sh use ```
./rotate.sh
```
Hope this helps. And if you have any more questions/problems, feel free to ask away.

dugh,
Glad everything is working well for you!

---

### Post by tembares on 2011-05-04
> **rougered said:**
> Hi!
       first of ll i wanted to say that i can use my computer with Natty thanks to your scripts...so ... thank you very much!!

however i still have a problem with the rotation of my screen...i get the error

rotate.sh: 104: [[: not found

i run the command as 
sudo sh rotate.sh
any suggestion?

What I did was copying the files to /usr/local/bin.
Then I renamed them all from blabla.sh to blabla.
Then I set the permission: sudo chmod +x blabla
If needed I changed the owner rights to: sudo chown username:username blabla, where username is your username.

Then I set a shortcut (ctrl+alt+G) to make it easy to change from cards.

---

### Post by rougered on 2011-05-05
Hi again ... 
rotation didn't work.

i mean neither
./rotate.sh
nor
sudo ./rotate.sh

the user and groups are correct... at least from what i see from "ls -l"
i prefer not to copy to /usr/local/bin ... it should not matter in any case.

i wonder...should it work with both ati and intel?

thank you
Riccardo

---

### Post by tembares on 2011-05-05
> **rougered said:**
> Hi again ... 
rotation didn't work.

i mean neither
./rotate.sh
nor
sudo ./rotate.sh

the user and groups are correct... at least from what i see from "ls -l"
i prefer not to copy to /usr/local/bin ... it should not matter in any case.

i wonder...should it work with both ati and intel?

What do you see when you execute '(sudo) rotate.sh'?
Try sudo 'bash ./rotate.sh'.

Copy/past the output of 'ls -laF'.

Execute 'dmesg'. Wait 5 seconds, rotate your screen, wait 1 second, rotate your screen back and send us the latest output of dmesg.

---

### Post by xdominex on 2011-05-06
First of all, let me tell you guys:
It is freakin refreshing to see a group of guys (though small) actively working on this! I have been laboring at it with much frustration in my efforts to make everything work. I will post (in detail) my setup, what works, what doesn't, and my thoughts regarding the "why" aspect of it all.

Auto-rotate:
```

#!/bin/bash

old="0"
while true; do
    if [ -e /sys/devices/platform/hp-wmi/tablet ]; then
        new=`cat /sys/devices/platform/hp-wmi/tablet`
        if [ "$new" != "$old" ]; then
            if [ $new == "1" ]; then
		xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate HALF
		xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate HALF
		xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate HALF
		xrandr -o inverted
		xinput set-prop 15 "Device Enabled" 0
            elif [ $new == "0" ]; then
		xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate NONE
		xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate NONE
		xsetwacom set $"Wacom ISDv4 E3 Pen stylus" Rotate NONE
		xrandr -o normal
		xinput set-prop 15 "Device Enabled" 1
            fi
        fi
            	old=$new
    fi
    	sleep 0.5s
done

exit 0

```

This script came from the following thread:
[http://ubuntuforums.org/showthread.php?t=845911&page=58](http://ubuntuforums.org/showthread.php?t=845911&page=58)
I modified it to have the correct device arguments (i.e. replacing "touch" with "Wacom ISDv4 E3 Finger touch") and removed the cellwriter-related commands from it. Works wonderfully for what I need it to do.

I slapped the script into my list of startup applications (accessed via System > preferences menu), but eventually had to also throw the script into /bin/ to make it work properly that way.

The great thing about this script is that it rotates the screen flawlessly and starts up upon login without a hitch. Only problem I've seen is that multiple instances tend to start happening sometimes (possibly from logging out and logging back in without restart). HOWEVER, it would be awesome if we got the dual-monitor issue tackled; I also have a vested interest in such a solution.


Rotate-display:
```

#!/bin/bash

if [ $# != 1 ]; then
    echo 'Usage: '
    echo $0 'none|half|left|right'
    exit
fi

xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate NONE
xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate NONE
xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate NONE
ROTATE="NONE"
DISP="normal"

if [ "$1" == "left" ]; then
	xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate CW
	xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate CW
	xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate CW
   	ROTATE="CW"
    	DISP="left"
elif [ "$1" == "right" ]; then
	xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate CCW
	xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate CCW
	xsetwacom set "Wacom ISDv4 E3 Pen touch" Rotate CCW
	DISP="right"
	ROTATE="CCW"
elif [ "$1" == "half" ]; then
    	xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate HALF
    	xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate HALF
    	xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate HALF
	DISP="inverted"
    	ROTATE="half"    	
fi
echo "Rotating to: $DISP ($ROTATE)"

xrandr -o $DISP

```
This script is simply installed in case I want to do a special rotation for some reason or need to get out of a tight spot in which screen rotation is screwing things up.


Tablet-mode:
```

#!/bin/sh 


# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    inverted) 
#    -rotate to the left
   	 xrandr -o right
   	 xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate ccw
   	 xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate ccw
   	 xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate ccw
    ;; 
    right) 
#    -rotate to half
    	xrandr -o inverted 
	xsetwacom set "Wacom ISDv4 E3 Pen eraser" Rotate half
	xsetwacom set "Wacom ISDv4 E3 Pen stylus" Rotate half
	xsetwacom set "Wacom ISDv4 E3 Finger touch" Rotate half
    ;; 
esac

exit 0

```
This one simply rotates it from landscape to portrait or vice-versa depending on the current state. This is convenient so I can easily and quickly switch between the two when in tablet mode; I created a launcher for it in my top panel for convenient access. On other forums, I have seen the "rotate ccw" referred to as the "left-handed" solution, but "rotate cw" seems foolish to me since it points the vent into my lap.


Dual-graphics (numbers simply indicate different areas of concern):
1. I have serious problems with booting up to a black screen. After upgrading to a newer kernel (2.6.39-0) and installing the latest video drivers from xorg's xcrack team, it seems EASIER to boot up successfully, but now I have a un-conquerable black screen when returning from suspend (previously there was a black screen that could be dispelled with the "increase brightness" hotkey). For whatever odd reason, everywhere I read mentions "nomodeset," but that doesn't work for me; HOWEVER, "nomodset" does lolz! When it gets REALLY hard to boot up, I do a complex routine that seems to work reliably for some odd reason.
-start computer loading bios-settings screen
-exit bios without saving changes
-use ctrl-alt-delete to reboot when grub appears
-wait for grub to come back
-add "nomodprobe=i915" to the boot options and boot up!

2. Switching to the ATI card is as simple as running (as root) ```
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```
then logging out and back in. The system automatically powers on the ATI card and powers off the Intel card, so the "echo OFF.." and "echo ON.." commands are not necessary. Unfortunately, 3D acceleration does not work on the ATI card due to weak support from open-source drivers (also, for some odd reason, though, Phoronix Test Suite thinks my intel HD card has 3D acceleration but my ATI doesn't).

3. I slapped the following two lines into /etc/rc.local to make the whole vga-switcheroo thing work fine:
```

chmod 777 /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```
Tweak 777 if worried about security. I'm not worried about it since only root can run it still.

Hope all of this helps! I will definitely keep track of this thread and contribute as I am able to do so!

Notes: 
-all files displayed here are attached for reference, use, editing, or whatever else
-all executable files have been placed in my /bin/ directory, as it seems the only location from which they can be faithfully and effectively launched

---

### Post by rougered on 2011-05-07
Hi all,
       first of all thank you for the answers... 

sudo bash ./rotate does work ... but when i rotate to portrait only the lowest two thirds of the screen are shown. It is strange because the whole launcher bar is shown correctly.

my dmesg output follows

[QUOTE][
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=dbe80680-ace6-4bf7-83cb-0d56cfd53ab6 ro quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009b63f000 (usable)
[    0.000000]  BIOS-e820: 000000009b63f000 - 000000009b6bf000 (reserved)
[    0.000000]  BIOS-e820: 000000009b6bf000 - 000000009b7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009b7bf000 - 000000009b7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009b7ff000 - 000000009b800000 (usable)
[    0.000000]  BIOS-e820: 000000009b800000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000158000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP TouchSmart tm2 Notebook PC   /1486, BIOS F.11 07/08/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x158000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 09B800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 base 158000000 mask FF8000000 uncachable
[    0.000000]   7 base 160000000 mask FE0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0x9b800 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000009b800000
[    0.000000]  0000000000 - 009b800000 page 2M
[    0.000000] kernel direct mapping tables up to 9b800000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000158000000
[    0.000000]  0100000000 - 0158000000 page 2M
[    0.000000] kernel direct mapping tables up to 158000000 @ 9b638000-9b63f000
[    0.000000] RAMDISK: 366e4000 - 3736a000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 000000009b7fe120 00094 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 000000009b7fc000 000F4 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 000000009b7e9000 0FA6D (v02 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 000000009b75f000 00040
[    0.000000] ACPI: ASF! 000000009b7fd000 000A5 (v32 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 000000009b7fb000 00038 (v01 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000009b7fa000 0008C (v02 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000009b7f9000 0003C (v01 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000009b7e8000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009b7e6000 01152 (v01 TrmRef PtidDevc 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000009b7e5000 00172 (v01  VaRef  Va_Acpi 00003000 INTL 20051117)
[    0.000000] ACPI: BOOT 000000009b7e4000 00028 (v01 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009b7e3000 00C39 (v01 INTEL   SataPri 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000009b7e2000 006C5 (v01 INTEL   SataSec 00001000 INTL 20051117)
[    0.000000] ACPI: ASPT 000000009b7e1000 00034 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009b7e0000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000009b7de000 01A8F (v01 AmdRef  AmdTabl 00001000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000158000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000158000000
[    0.000000]   NODE_DATA [0000000157ffb000 - 0000000157ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff880154000000-ffff8801577fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00158000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009b63f
[    0.000000]     0: 0x0009b7ff -> 0x0009b800
[    0.000000]     0: 0x00100000 -> 0x00158000
[    0.000000] On node 0 totalpages: 996813
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 618104 pages, LIFO batch:31
[    0.000000]   Normal zone: 4928 pages used for memmap
[    0.000000]   Normal zone: 355520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009b63f000 - 000000009b6bf000
[    0.000000] PM: Registered nosave memory: 000000009b6bf000 - 000000009b7bf000
[    0.000000] PM: Registered nosave memory: 000000009b7bf000 - 000000009b7ff000
[    0.000000] PM: Registered nosave memory: 000000009b800000 - 00000000a0000000
[    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:40000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88009b400000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 977543
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=dbe80680-ace6-4bf7-83cb-0d56cfd53ab6 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3836660k/5636096k available (5940k kernel code, 1648844k absent, 150592k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 40632320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 1330.098 MHz processor.
[    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2660.19 BogoMIPS (lpj=13300980)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000051] Security Framework initialized
[    0.000071] AppArmor: AppArmor initialized
[    0.000073] Yama: becoming mindful.
[    0.000730] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002647] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.003455] Mount-cache hash table entries: 256
[    0.003644] Initializing cgroup subsys ns
[    0.003649] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.003653] Initializing cgroup subsys cpuacct
[    0.003660] Initializing cgroup subsys memory
[    0.003671] Initializing cgroup subsys devices
[    0.003674] Initializing cgroup subsys freezer
[    0.003677] Initializing cgroup subsys net_cls
[    0.003680] Initializing cgroup subsys blkio
[    0.003725] CPU: Physical Processor ID: 0
[    0.003727] CPU: Processor Core ID: 0
[    0.003736] mce: CPU supports 9 MCE banks
[    0.003750] CPU0: Thermal monitoring handled by SMI
[    0.003761] using mwait in idle threads.
[    0.007337] ACPI: Core revision 20110112
[    0.057555] ftrace: allocating 24314 entries in 96 pages
[    0.071169] Setting APIC routing to flat
[    0.071539] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.171439] CPU0: Intel(R) Core(TM) i3 CPU       U 380  @ 1.33GHz stepping 05
[    0.286950] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.286960] ... version:                3
[    0.286962] ... bit width:              48
[    0.286964] ... generic registers:      4
[    0.286967] ... value mask:             0000ffffffffffff
[    0.286969] ... max period:             000000007fffffff
[    0.286971] ... fixed-purpose events:   3
[    0.286973] ... event mask:             000000070000000f
[    0.287740] Booting Node   0, Processors  #1
[    0.446792] CPU1: Thermal monitoring handled by SMI
[    0.466973]  #2
[    0.626569] CPU2: Thermal monitoring handled by SMI
[    0.646783]  #3
[    0.806351] CPU3: Thermal monitoring handled by SMI
[    0.826480] Brought up 4 CPUs
[    0.826485] Total of 4 processors activated (10640.19 BogoMIPS).
[    0.828987] devtmpfs: initialized
[    0.830642] print_constraints: dummy: 
[    0.830675] Time: 13:17:14  Date: 05/07/11
[    0.830727] NET: Registered protocol family 16
[    0.830877] Trying to unpack rootfs image as initramfs...
[    0.830894] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.830899] ACPI: bus type pci registered
[    0.831018] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.831023] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.893981] PCI: Using configuration type 1 for base access
[    0.895263] bio: create slab <bio-0> at 0
[    0.900205] ACPI: EC: Look up EC in DSDT
[    0.904874] ACPI: Executed 1 blocks of module-level executable AML code
[    1.026287] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.033308] ACPI: SSDT 000000009b691a98 0033A (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.034467] ACPI: Dynamic OEM Table Load:
[    1.034471] ACPI: SSDT           (null) 0033A (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.034814] ACPI: SSDT 000000009b690018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.035932] ACPI: Dynamic OEM Table Load:
[    1.035936] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.166603] ACPI: SSDT 000000009b691718 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.167810] ACPI: Dynamic OEM Table Load:
[    1.167815] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.196269] ACPI: SSDT 000000009b68fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.197407] ACPI: Dynamic OEM Table Load:
[    1.197411] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.234320] Freeing initrd memory: 12824k freed
[    1.665485] ACPI: Interpreter enabled
[    1.665494] ACPI: (supports S0 S3 S4 S5)
[    1.665568] ACPI: Using IOAPIC for interrupt routing
[    1.667219] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.701802] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.705112] ACPI: Power Resource [FN00] (on)
[    1.706086] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.735802] ACPI: No dock devices found.
[    1.735805] HEST: Table not found.
[    1.735810] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.736496] \_SB_.PCI0:_OSC invalid UUID
[    1.736498] _OSC request data:1 8 1f 
[    1.736506] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.737632] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.737637] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.737640] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.737645] pci_root PNP0A08:00: host bridge window [mem 0xa0000000-0xfeafffff]
[    1.737665] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.737696] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.737725] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
[    1.737768] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.737773] pci 0000:00:01.0: PME# disabled
[    1.737793] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.737812] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    1.737823] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.737831] pci 0000:00:02.0: reg 20: [io  0x4050-0x4057]
[    1.737910] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.737943] pci 0000:00:16.0: reg 10: [mem 0xc4506100-0xc450610f 64bit]
[    1.738021] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.738027] pci 0000:00:16.0: PME# disabled
[    1.738072] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.738389] pci 0000:00:1a.0: reg 10: [mem 0xc4505c00-0xc4505fff]
[    1.740104] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.740110] pci 0000:00:1a.0: PME# disabled
[    1.740140] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.740160] pci 0000:00:1b.0: reg 10: [mem 0xc4500000-0xc4503fff 64bit]
[    1.740227] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.740233] pci 0000:00:1b.0: PME# disabled
[    1.740259] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.740329] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.740334] pci 0000:00:1c.0: PME# disabled
[    1.740360] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    1.740429] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.740434] pci 0000:00:1c.1: PME# disabled
[    1.740480] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.740779] pci 0000:00:1d.0: reg 10: [mem 0xc4505800-0xc4505bff]
[    1.742500] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.742506] pci 0000:00:1d.0: PME# disabled
[    1.742532] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.742607] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    1.742753] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    1.742783] pci 0000:00:1f.2: reg 10: [io  0x4048-0x404f]
[    1.742796] pci 0000:00:1f.2: reg 14: [io  0x405c-0x405f]
[    1.742809] pci 0000:00:1f.2: reg 18: [io  0x4040-0x4047]
[    1.742823] pci 0000:00:1f.2: reg 1c: [io  0x4058-0x405b]
[    1.742836] pci 0000:00:1f.2: reg 20: [io  0x4020-0x403f]
[    1.742848] pci 0000:00:1f.2: reg 24: [mem 0xc4505000-0xc45057ff]
[    1.742902] pci 0000:00:1f.2: PME# supported from D3hot
[    1.742907] pci 0000:00:1f.2: PME# disabled
[    1.742932] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    1.742952] pci 0000:00:1f.3: reg 10: [mem 0xc4506000-0xc45060ff 64bit]
[    1.742979] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    1.743026] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.743056] pci 0000:00:1f.6: reg 10: [mem 0xc4504000-0xc4504fff 64bit]
[    1.743191] pci 0000:01:00.0: [1002:68e0] type 0 class 0x000300
[    1.743215] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.743234] pci 0000:01:00.0: reg 18: [mem 0xc4400000-0xc441ffff 64bit]
[    1.743248] pci 0000:01:00.0: reg 20: [io  0x3000-0x30ff]
[    1.743271] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    1.743303] pci 0000:01:00.0: supports D1 D2
[    1.743336] pci 0000:01:00.1: [1002:aa68] type 0 class 0x000403
[    1.743359] pci 0000:01:00.1: reg 10: [mem 0xc4420000-0xc4423fff 64bit]
[    1.743441] pci 0000:01:00.1: supports D1 D2
[    1.743477] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.743482] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    1.743487] pci 0000:00:01.0:   bridge window [mem 0xc4400000-0xc44fffff]
[    1.743493] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.743567] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    1.743590] pci 0000:02:00.0: reg 10: [io  0x2000-0x20ff]
[    1.743625] pci 0000:02:00.0: reg 18: [mem 0xc0404000-0xc0404fff 64bit pref]
[    1.743648] pci 0000:02:00.0: reg 20: [mem 0xc0400000-0xc0403fff 64bit pref]
[    1.743709] pci 0000:02:00.0: supports D1 D2
[    1.743712] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.743719] pci 0000:02:00.0: PME# disabled
[    1.743764] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.743770] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.743776] pci 0000:00:1c.0:   bridge window [mem 0xc3400000-0xc43fffff]
[    1.743784] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.743890] pci 0000:03:00.0: [14e4:4727] type 0 class 0x000280
[    1.743922] pci 0000:03:00.0: reg 10: [mem 0xc2400000-0xc2403fff 64bit]
[    1.744036] pci 0000:03:00.0: supports D1 D2
[    1.744084] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.744089] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    1.744094] pci 0000:00:1c.1:   bridge window [mem 0xc2400000-0xc33fffff]
[    1.744102] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.744190] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    1.744196] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.744203] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.744212] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.744216] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.744219] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.744223] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.744227] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfeafffff] (subtractive decode)
[    1.744251] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.744544] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.744615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.744758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.744832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.745008] \_SB_.PCI0:_OSC invalid UUID
[    1.745010] _OSC request data:1 19 1f 
[    1.755830] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.755954] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    1.755986] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    1.756020] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    1.756050] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    1.756078] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    1.756107] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    1.756558] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.756635] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.756709] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.756781] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.756854] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.756927] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.757001] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.757074] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.757247] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.757260] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.757268] vgaarb: loaded
[    1.757526] SCSI subsystem initialized
[    1.757624] libata version 3.00 loaded.
[    1.757698] usbcore: registered new interface driver usbfs
[    1.757712] usbcore: registered new interface driver hub
[    1.757748] usbcore: registered new device driver usb
[    1.758304] wmi: Mapper loaded
[    1.758306] PCI: Using ACPI for IRQ routing
[    1.758310] PCI: pci_cache_line_size set to 64 bytes
[    1.758414] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
[    1.758417] reserve RAM buffer: 000000009b63f000 - 000000009bffffff 
[    1.758421] reserve RAM buffer: 000000009b800000 - 000000009bffffff 
[    1.758568] NetLabel: Initializing
[    1.758571] NetLabel:  domain hash size = 128
[    1.758573] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.758590] NetLabel:  unlabeled traffic allowed by default
[    1.758652] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.758661] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.760685] Switching to clocksource hpet
[    1.765177] Switched to NOHz mode on CPU #0
[    1.765266] Switched to NOHz mode on CPU #1
[    1.765294] Switched to NOHz mode on CPU #2
[    1.765343] Switched to NOHz mode on CPU #3
[    1.770245] AppArmor: AppArmor Filesystem Enabled
[    1.770289] pnp: PnP ACPI init
[    1.770315] ACPI: bus type pnp registered
[    1.770972] pnp 00:00: [bus 00-fe]
[    1.770977] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.770980] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.770983] pnp 00:00: [io  0x0d00-0xffff window]
[    1.770986] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.770989] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.770992] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.770995] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.770998] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.771001] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.771005] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.771010] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.771014] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.771017] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.771020] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.771023] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.771026] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.771029] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.771032] pnp 00:00: [mem 0xa0000000-0xfeafffff window]
[    1.771035] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.771194] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.771315] pnp 00:01: [io  0x0000-0x001f]
[    1.771318] pnp 00:01: [io  0x0081-0x0091]
[    1.771320] pnp 00:01: [io  0x0093-0x009f]
[    1.771323] pnp 00:01: [io  0x00c0-0x00df]
[    1.771327] pnp 00:01: [dma 4]
[    1.771371] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.771384] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.771428] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.771605] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.771650] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.771667] pnp 00:04: [io  0x00f0]
[    1.771682] pnp 00:04: [irq 13]
[    1.771724] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.771742] pnp 00:05: [io  0x002e-0x002f]
[    1.771745] pnp 00:05: [io  0x004e-0x004f]
[    1.771747] pnp 00:05: [io  0x0061]
[    1.771750] pnp 00:05: [io  0x0063]
[    1.771752] pnp 00:05: [io  0x0065]
[    1.771755] pnp 00:05: [io  0x0067]
[    1.771757] pnp 00:05: [io  0x0070]
[    1.771760] pnp 00:05: [io  0x0080]
[    1.771762] pnp 00:05: [io  0x0092]
[    1.771765] pnp 00:05: [io  0x00b2-0x00b3]
[    1.771767] pnp 00:05: [io  0x0680-0x069f]
[    1.771770] pnp 00:05: [io  0x0800-0x080f]
[    1.771773] pnp 00:05: [io  0x0810-0x0813]
[    1.771775] pnp 00:05: [io  0xffff]
[    1.771778] pnp 00:05: [io  0x0400-0x047f]
[    1.771780] pnp 00:05: [io  0x0500-0x0501]
[    1.771783] pnp 00:05: [io  0x0700-0x077f]
[    1.771786] pnp 00:05: [io  0x164e-0x164f]
[    1.771812] pnp 00:05: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.1 BAR 13 [io  0x1000-0x1fff]
[    1.771896] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.771900] system 00:05: [io  0x0800-0x080f] has been reserved
[    1.771903] system 00:05: [io  0x0810-0x0813] has been reserved
[    1.771907] system 00:05: [io  0xffff] has been reserved
[    1.771910] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.771914] system 00:05: [io  0x0500-0x0501] has been reserved
[    1.771918] system 00:05: [io  0x0700-0x077f] has been reserved
[    1.771923] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.771937] pnp 00:06: [io  0x0070-0x0077]
[    1.771945] pnp 00:06: [irq 8]
[    1.771987] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.772003] pnp 00:07: [io  0x0060]
[    1.772006] pnp 00:07: [io  0x0064]
[    1.772013] pnp 00:07: [irq 1]
[    1.772059] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.772077] pnp 00:08: [irq 12]
[    1.772129] pnp 00:08: Plug and Play ACPI device, IDs SYN1e2d SYN1e00 SYN0002 PNP0f13 (active)
[    1.772343] pnp 00:09: [irq 23]
[    1.772418] pnp 00:09: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.772745] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.772748] pnp 00:0a: [mem 0xfed10000-0xfed13fff]
[    1.772751] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.772754] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.772757] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.772760] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.772763] pnp 00:0a: [mem 0xfed90000-0xfed8ffff disabled]
[    1.772766] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    1.772769] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.772772] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.772775] pnp 00:0a: [mem 0xc4600000-0xc4600fff]
[    1.772886] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.772891] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.772894] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.772898] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.772902] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.772906] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.772909] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.772913] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.772918] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.772922] system 00:0a: [mem 0xc4600000-0xc4600fff] has been reserved
[    1.772926] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.773307] pnp 00:0b: [bus ff]
[    1.773396] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.773442] pnp: PnP ACPI: found 12 devices
[    1.773445] ACPI: ACPI bus type pnp unregistered
[    1.780396] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.780448] pci 0000:01:00.0: BAR 6: assigned [mem 0xc4440000-0xc445ffff pref]
[    1.780453] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.780457] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    1.780463] pci 0000:00:01.0:   bridge window [mem 0xc4400000-0xc44fffff]
[    1.780467] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.780474] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.780478] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.780485] pci 0000:00:1c.0:   bridge window [mem 0xc3400000-0xc43fffff]
[    1.780491] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.780500] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.780504] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    1.780511] pci 0000:00:1c.1:   bridge window [mem 0xc2400000-0xc33fffff]
[    1.780517] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.780526] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    1.780529] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.780535] pci 0000:00:1e.0:   bridge window [mem disabled]
[    1.780540] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.780564] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.780570] pci 0000:00:01.0: setting latency timer to 64
[    1.780584] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.780590] pci 0000:00:1c.0: setting latency timer to 64
[    1.780599] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.780604] pci 0000:00:1c.1: setting latency timer to 64
[    1.780613] pci 0000:00:1e.0: setting latency timer to 64
[    1.780620] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.780623] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.780626] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.780630] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.780633] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    1.780636] pci_bus 0000:01: resource 1 [mem 0xc4400000-0xc44fffff]
[    1.780640] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    1.780643] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.780646] pci_bus 0000:02: resource 1 [mem 0xc3400000-0xc43fffff]
[    1.780650] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.780653] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    1.780657] pci_bus 0000:03: resource 1 [mem 0xc2400000-0xc33fffff]
[    1.780660] pci_bus 0000:03: resource 2 [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.780664] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.780667] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.780670] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.780673] pci_bus 0000:04: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.780733] NET: Registered protocol family 2
[    1.780966] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.782538] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.785759] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.786166] TCP: Hash tables configured (established 524288 bind 65536)
[    1.786169] TCP reno registered
[    1.786187] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.786223] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.786395] NET: Registered protocol family 1
[    1.786423] pci 0000:00:02.0: Boot video device
[    1.820722] PCI: CLS 64 bytes, default 64
[    1.820725] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.820729] Placing 64MB software IO TLB between ffff880097400000 - ffff88009b400000
[    1.820732] software IO TLB at phys 0x97400000 - 0x9b400000
[    1.820780] Simple Boot Flag at 0x44 set to 0x1
[    1.821467] audit: initializing netlink socket (disabled)
[    1.821480] type=2000 audit(1304774234.660:1): initialized
[    1.843451] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.846223] VFS: Disk quotas dquot_6.5.2
[    1.846307] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.847272] fuse init (API version 7.16)
[    1.847403] msgmni has been set to 7518
[    1.847741] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.847775] io scheduler noop registered
[    1.847779] io scheduler deadline registered
[    1.847843] io scheduler cfq registered (default)
[    1.847991] pcieport 0000:00:01.0: setting latency timer to 64
[    1.848038] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.848229] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.848266] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.848328] intel_idle: MWAIT substates: 0x1120
[    1.848330] intel_idle: v0.4 model 0x25
[    1.848332] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.849753] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.850028] ACPI: AC Adapter [AC] (on-line)
[    1.850145] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.850187] ACPI: Lid Switch [LID0]
[    1.850251] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.000436] ACPI: Power Button [PWRB]
[    2.000530] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.000536] ACPI: Power Button [PWRF]
[    2.000625] ACPI: Fan [FAN0] (on)
[    2.000940] ACPI: acpi_idle yielding to intel_idle
[    2.009404] thermal LNXTHERM:00: registered as thermal_zone0
[    2.009408] ACPI: Thermal Zone [TZ00] (50 C)
[    2.010280] thermal LNXTHERM:01: registered as thermal_zone1
[    2.010283] ACPI: Thermal Zone [TZ01] (37 C)
[    2.011138] thermal LNXTHERM:02: registered as thermal_zone2
[    2.011142] ACPI: Thermal Zone [TZ02] (56 C)
[    2.011183] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.011300] ERST: Table is not found!
[    2.011420] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.520315] ACPI: Battery Slot [BAT0] (battery present)
[    2.532604] Linux agpgart interface v0.103
[    2.532741] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    2.532920] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.534080] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    2.534294] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    2.535937] brd: module loaded
[    2.536684] loop: module loaded
[    2.536812] i2c-core: driver [adp5520] using legacy suspend method
[    2.536815] i2c-core: driver [adp5520] using legacy resume method
[    2.537385] Fixed MDIO Bus: probed
[    2.537427] PPP generic driver version 2.4.2
[    2.537478] tun: Universal TUN/TAP device driver, 1.6
[    2.537481] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.537601] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.537630] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.537660] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.537666] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.537724] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.537816] ehci_hcd 0000:00:1a.0: debug port 2
[    2.541741] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.541768] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc4505c00
[    2.559768] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.559968] hub 1-0:1.0: USB hub found
[    2.559975] hub 1-0:1.0: 3 ports detected
[    2.560084] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.560105] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.560110] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.560163] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.560235] ehci_hcd 0000:00:1d.0: debug port 2
[    2.564163] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.564183] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc4505800
[    2.579748] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.579912] hub 2-0:1.0: USB hub found
[    2.579918] hub 2-0:1.0: 3 ports detected
[    2.580009] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.580025] uhci_hcd: USB Universal Host Controller Interface driver
[    2.580172] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.583654] i8042: Detected active multiplexing controller, rev 1.1
[    2.587203] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.587214] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.587230] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.587234] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.587244] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.587489] mousedev: PS/2 mouse device common for all mice
[    2.587698] rtc_cmos 00:06: RTC can wake from S4
[    2.587790] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.587824] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.587970] device-mapper: uevent: version 1.0.3
[    2.588083] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    2.588157] device-mapper: multipath: version 1.2.0 loaded
[    2.588163] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.588467] cpuidle: using governor ladder
[    2.588688] cpuidle: using governor menu
[    2.589048] TCP cubic registered
[    2.589235] NET: Registered protocol family 10
[    2.590259] NET: Registered protocol family 17
[    2.590299] Registering the dns_resolver key type
[    2.591351] ACPI Error: [NPSS] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    2.591370] ACPI Error: Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff88014f9ad140), AE_NOT_FOUND (20110112/psparse-536)
[    2.591391] ACPI Error: Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff88014f9ad028), AE_NOT_FOUND (20110112/psparse-536)
[    2.592016] ACPI Error: [NPSS] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    2.592032] ACPI Error: Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff88014f9ad140), AE_NOT_FOUND (20110112/psparse-536)
[    2.592051] ACPI Error: Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff88014f9ad028), AE_NOT_FOUND (20110112/psparse-536)
[    2.592070] ACPI Error: Method parse/execution failed [\_PR_.CPU1._PPC] (Node ffff88014f9ad118), AE_NOT_FOUND (20110112/psparse-536)
[    2.592605] ACPI Error: [NPSS] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    2.592621] ACPI Error: Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff88014f9ad140), AE_NOT_FOUND (20110112/psparse-536)
[    2.592640] ACPI Error: Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff88014f9ad028), AE_NOT_FOUND (20110112/psparse-536)
[    2.592658] ACPI Error: Method parse/execution failed [\_PR_.CPU2._PPC] (Node ffff88014f9ad370), AE_NOT_FOUND (20110112/psparse-536)
[    2.592913] ACPI Error: [NPSS] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    2.592921] ACPI Error: Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff88014f9ad140), AE_NOT_FOUND (20110112/psparse-536)
[    2.592931] ACPI Error: Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff88014f9ad028), AE_NOT_FOUND (20110112/psparse-536)
[    2.592940] ACPI Error: Method parse/execution failed [\_PR_.CPU3._PPC] (Node ffff88014f9ad2d0), AE_NOT_FOUND (20110112/psparse-536)
[    2.593164] PM: Hibernation image not present or could not be loaded.
[    2.593181] registered taskstats version 1
[    2.593590]   Magic number: 11:615:280
[    2.593631] tty tty17: hash matches
[    2.593803] rtc_cmos 00:06: setting system clock to 2011-05-07 13:17:16 UTC (1304774236)
[    2.593807] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.593809] EDD information not available.
[    2.597191] Freeing unused kernel memory: 956k freed
[    2.597425] Write protecting the kernel read-only data: 10240k
[    2.599024] Freeing unused kernel memory: 184k freed
[    2.608217] Freeing unused kernel memory: 1444k freed
[    2.626138] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.640002] <30>udev[71]: starting version 167
[    2.745827] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.745869] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.745935] r8169 0000:02:00.0: setting latency timer to 64
[    2.746019] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    2.749293] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc900110c4000, 1c:c1:de:a0:13:de, XID 083000c0 IRQ 41
[    2.754939] ahci 0000:00:1f.2: version 3.0
[    2.754971] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.755039] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.755105] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    2.755110] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    2.755117] ahci 0000:00:1f.2: setting latency timer to 64
[    2.755781] scsi0 : ahci
[    2.756194] scsi1 : ahci
[    2.756321] scsi2 : ahci
[    2.756449] scsi3 : ahci
[    2.756654] ata1: SATA max UDMA/133 abar m2048@0xc4505000 port 0xc4505100 irq 42
[    2.756657] ata2: DUMMY
[    2.756659] ata3: DUMMY
[    2.756661] ata4: DUMMY
[    2.819534] Refined TSC clocksource calibration: 1329.999 MHz.
[    2.819542] Switching to clocksource tsc
[    2.889444] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.040102] hub 1-1:1.0: USB hub found
[    3.040301] hub 1-1:1.0: 6 ports detected
[    3.099197] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.100897] ata1.00: ATA-8: WDC WD3200BEKT-60KA9T0, 01.01A01, max UDMA/133
[    3.100903] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.102750] ata1.00: configured for UDMA/133
[    3.102942] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 01.0 PQ: 0 ANSI: 5
[    3.103238] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.103312] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.103466] sd 0:0:0:0: [sda] Write Protect is off
[    3.103472] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.103519] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.159153] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.175837]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    3.176550] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.310017] hub 2-1:1.0: USB hub found
[    3.310209] hub 2-1:1.0: 8 ports detected
[    3.389083] usb 1-1.4: new full speed USB device using ehci_hcd and address 3
[    3.588608] usb 2-1.5: new full speed USB device using ehci_hcd and address 3
[    3.732194] usbcore: registered new interface driver usbhid
[    3.732200] usbhid: USB HID core driver
[    3.778448] usb 2-1.6: new high speed USB device using ehci_hcd and address 4
[    3.890022] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.931475] Adding 3904508k swap on /dev/sda7.  Priority:-1 extents:1 across:3904508k 
[   10.946361] <30>udev[312]: starting version 167
[   10.972677] lp: driver loaded but no devices found
[   11.046460] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   11.134002] hp_accel: laptop model unknown, using default axes configuration
[   11.134873] lis3lv02d: 8 bits sensor found
[   11.180508] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input4
[   11.180833] Registered led device: hp::hddprotect
[   11.180913] hp_accel: driver loaded
[   11.228919] lib80211: common routines for IEEE802.11 drivers
[   11.228926] lib80211_crypt: registered algorithm 'NULL'
[   11.247429] [drm] Initialized drm 1.1.0 20060810
[   11.250034] type=1400 audit(1304767045.159:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=546 comm="apparmor_parser"
[   11.251477] type=1400 audit(1304767045.159:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=546 comm="apparmor_parser"
[   11.252304] type=1400 audit(1304767045.159:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=546 comm="apparmor_parser"
[   11.252645] type=1400 audit(1304767045.159:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=555 comm="apparmor_parser"
[   11.254119] type=1400 audit(1304767045.159:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=555 comm="apparmor_parser"
[   11.255735] type=1400 audit(1304767045.159:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=555 comm="apparmor_parser"
[   11.261032] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.261040] Disabling lock debugging due to kernel taint
[   11.272967] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 11, expected 14)
[   11.273008] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.273313] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   11.307958] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   11.342008] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.342021] wl 0000:03:00.0: setting latency timer to 64
[   11.395688] lib80211_crypt: registered algorithm 'TKIP'
[   11.447443] type=1400 audit(1304767045.349:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=673 comm="apparmor_parser"
[   11.453076] type=1400 audit(1304767045.359:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=681 comm="apparmor_parser"
[   11.455330] type=1400 audit(1304767045.359:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=675 comm="apparmor_parser"
[   11.459283] type=1400 audit(1304767045.369:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=681 comm="apparmor_parser"
[   11.500346] input: Wacom ISDv4 E3 Finger as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5
[   11.532649] input: Wacom ISDv4 E3 Pen as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input6
[   11.537092] usbcore: registered new interface driver wacom
[   11.537098] wacom: v1.52:USB Wacom tablet driver
[   11.570441] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   11.585444] Linux video capture interface: v2.00
[   11.609491] uvcvideo: Found UVC 1.00 device HP Webcam (174f:1118)
[   11.624049] input: HP Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
[   11.624208] usbcore: registered new interface driver uvcvideo
[   11.624213] USB Video Class driver (v1.0.0)
[   11.742572] [drm] radeon defaulting to kernel modesetting.
[   11.742578] [drm] radeon kernel modesetting enabled.
[   11.742616] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   11.742705] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   11.742721] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.742731] radeon 0000:01:00.0: setting latency timer to 64
[   11.745253] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68E0).
[   11.745378] [drm] register mmio base: 0xC4400000
[   11.745382] [drm] register mmio size: 131072
[   11.746868] r8169 0000:02:00.0: eth0: link down
[   11.748060] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.780305] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.780397] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   11.780439] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.928845] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.929045] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.138711] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0x5a0400
[   12.175784] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   13.106446] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   17.532952] input: HP WMI hotkeys as /devices/virtual/input/input11
[   19.289914] ATOM BIOS: HP
[   19.290006] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   19.290011] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   19.290022] mtrr: no more MTRRs available
[   19.290024] [drm] Detected VRAM RAM=512M, BAR=256M
[   19.290027] [drm] RAM width 64bits DDR
[   19.290213] [TTM] Zone  kernel: Available graphics memory: 1926034 kiB.
[   19.290217] [TTM] Initializing pool allocator.
[   19.290249] [drm] radeon: 512M of VRAM memory ready
[   19.290252] [drm] radeon: 512M of GTT memory ready.
[   19.290279] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   19.290282] [drm] Driver supports precise vblank timestamp query.
[   19.290338] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   19.290346] radeon 0000:01:00.0: radeon: using MSI.
[   19.290393] [drm] radeon: irq initialized.
[   19.290397] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   19.291198] [drm] Loading CEDAR Microcode
[   19.312051] radeon 0000:01:00.0: WB enabled
[   19.328927] [drm] ring test succeeded in 1 usecs
[   19.329107] [drm] radeon: ib pool ready.
[   19.329327] [drm] ib test succeeded in 0 usecs
[   19.331409] [drm] Radeon Display Connectors
[   19.331414] [drm] Connector 0:
[   19.331417] [drm]   LVDS
[   19.331422] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[   19.331426] [drm]   Encoders:
[   19.331430] [drm]     LCD1: INTERNAL_UNIPHY
[   19.331433] [drm] Connector 1:
[   19.331436] [drm]   HDMI-A
[   19.331439] [drm]   HPD1
[   19.331444] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   19.331448] [drm]   Encoders:
[   19.331451] [drm]     DFP1: INTERNAL_UNIPHY1
[   19.331454] [drm] Connector 2:
[   19.331457] [drm]   VGA
[   19.331462] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   19.331466] [drm]   Encoders:
[   19.331469] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   19.337499] [drm] Internal thermal controller with fan control
[   19.337569] [drm] radeon: power management initialized
[   19.352621] [drm] fb mappable at 0xA0141000
[   19.352624] [drm] vram apper at 0xA0000000
[   19.352627] [drm] size 4096000
[   19.352629] [drm] fb depth is 24
[   19.352630] [drm]    pitch is 5120
[   19.352997] Console: switching to colour frame buffer device 160x50
[   19.353055] fb0: radeondrmfb frame buffer device
[   19.353058] drm: registered panic notifier
[   19.353071] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[   19.353192] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.353279] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   19.353318] HDA Intel 0000:01:00.1: setting latency timer to 64
[   19.534076] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.534084] i915 0000:00:02.0: setting latency timer to 64
[   19.592135] ppdev: user-space parallel port driver
[   19.610754] audit_printk_skb: 18 callbacks suppressed
[   19.610759] type=1400 audit(1304767053.529:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1174 comm="apparmor_parser"
[   19.612051] type=1400 audit(1304767053.529:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1174 comm="apparmor_parser"
[   19.624349] mtrr: no more MTRRs available
[   19.624355] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   19.624998] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   19.625005] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   19.625008] [drm] Driver supports precise vblank timestamp query.
[   19.724830] vga_switcheroo: enabled
[   19.724892] radeon atpx: version is 1
[   19.783970] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   19.783979] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.875014] fb1: inteldrmfb frame buffer device
[   19.875936] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.876644] acpi device:02: registered as cooling_device5
[   19.877026] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input12
[   19.877118] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.877163] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   19.879821] acpi device:0b: registered as cooling_device6
[   19.880295] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
[   19.880403] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   19.880989] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[   21.325826] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   21.508062] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   21.814173] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   21.966446] eth1: no IPv6 routers present
[   27.467224] radeon: switched off
[   29.467383] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467392] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467395] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467397] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467400] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467403] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467405] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467408] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467411] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467413] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467416] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467419] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467421] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467424] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467427] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467430] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467432] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467435] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467438] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467440] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467443] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467446] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467449] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467451] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467454] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467457] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467460] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467462] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467465] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467468] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467470] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467473] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467476] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467478] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467481] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467484] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467486] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467489] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467492] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467495] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467497] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467500] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467503] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467505] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467508] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467511] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467513] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467516] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467519] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467521] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467524] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467527] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467529] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467532] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467535] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467538] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467540] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467543] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467546] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467548] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467551] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467554] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467556] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467559] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467562] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467564] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467567] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467570] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467572] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467575] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467578] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467581] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467583] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467586] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467589] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467591] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467594] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467597] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467599] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467602] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467605] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467608] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467611] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467613] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467616] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467619] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467622] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467624] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467627] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467630] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467632] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467635] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467638] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467640] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467643] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467646] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467649] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467651] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467654] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467657] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467659] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467662] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467665] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467667] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467670] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467673] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467675] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467678] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467681] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467683] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467686] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467689] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467691] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467694] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467697] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467700] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467702] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467705] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467708] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467710] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467713] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467716] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467718] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467721] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467724] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467726] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467729] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467732] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467734] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467737] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467740] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467743] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467745] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467748] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467751] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467753] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467756] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467759] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467762] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467764] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467767] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467770] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467772] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467775] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467778] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467781] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467783] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467786] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467789] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467791] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467794] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467797] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467799] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467802] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467805] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467807] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467810] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467813] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467815] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467818] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467821] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467824] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467826] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467829] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467832] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467834] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467837] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467840] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467842] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467845] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467848] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467850] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467853] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467856] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467859] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467861] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467864] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467867] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467869] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467872] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467875] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467877] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467880] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467883] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467885] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467888] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467891] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467894] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467896] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467899] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467902] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467905] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467907] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467910] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467913] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467915] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467918] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467921] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467923] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467926] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   29.467929] hda-intel: spurious response 0x0:0x0, last cmd=0x2f2d00
[   31.484944] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x002f2d00
[   32.493730] hda-intel: No response from codec, disabling MSI: last cmd=0x002f2d00
[   33.502515] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x002f2d00
[   67.601501] atkbd serio0: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[   67.601507] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[   67.613517] atkbd serio0: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[   67.613523] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[   83.537233] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   83.537239] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[   83.549233] atkbd serio0: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[   83.549238] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[   98.669196] atkbd serio0: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[   98.669202] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[   98.681228] atkbd serio0: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[   98.681233] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[  136.288989] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  136.289000] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[  136.302687] atkbd serio0: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[  136.302697] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
/QUOTE]

aside of this i am having big troubles with the pad keys not working... i mean...i can not rightclick!!!

thank you for any hint
ciao
Riccardo

---

### Post by xdominex on 2011-05-07
Riccardo,

Does a two-finger tap work for right click? Unfortunately, normal "right-clicks" in the right-click box on the touchpad do not work. It makes me frustrated and sad because two-finger tap often moves the cursor off of whatever I want to right-click.

Also, do you need to use rotate with dual monitors? If not, you should be able to slap my rotate-display script (attached in my previous post) into your /bin/ folder, change it to be executable, and run "rotate-display (none,half,left,right)" according to how you want your screen oriented. If you want me to modify it to disable the touchpad in specific orientations, I can do that for you. The following commands can also disable or enable the touchpad:
To enable:```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
```
To disable:```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0
```

I hope this can get you going for now until we get a complete fix figured out.

(BTW, my resume-from-suspend is working fine now)

---

### Post by dugh on 2011-05-11
My laptop was still hanging everytime I went to shutdown.

I'm not sure if this is the fix (haven't tried shutting down yet :), but there is a little typo in chadmerkert's script in the part that fixes the shutdown hang.

[UPDATE: yeah this fixes it]

Change:

```

#Fix hang on shutdown
echo #!/bin/sh > /etc/init.d/hybrid-graphics
```

to this: (add quotes after echo command)
```

#Fix hang on shutdown
echo "#!/bin/sh" > /etc/init.d/hybrid-graphics
```

or manually add this line to the top of the /etc/init.d/hybrid-graphics file like I did:

```
#!/bin/sh
```

---

### Post by android272 on 2011-05-12
so I tryed your scrips and Im not sure if they worked. I ran them though the terminal as the thing prompted me when I clicked on the files. 

I dont know what some of your scrips do. they are self-explanatory but I don't know how to tell weather they worked. 

I know from reading this forum that some of they scrips do multiple things.

would it be possible for some one to write a read me to include with the files. just to explain what they do, how use them, what you need to add to the start-up programs, how to make it work in 10.10/11.04.

I use 10.10 because I was not sure that 11.04 would work with this computer yet. 

here are some things that I am having trouble with and am wondering whether anyone ells is having the same. I can not seem to get the wifi, here is a [post]("http://ubuntuforums.org/showthread.php?t=1755168&highlight=HP+TouchSmart+tm2") that I have already made about that. I can't connect to my bluetooth mouse ether. I have a mac mighty mouse, I have gotten this to work on other computer running ubuntu but not my tablet.

I am also happy to find that people are still working on this computer. my friend told me that if the problems where not fixed soon after its release that the community would just drop it.

---

### Post by michael.p.mckenzie on 2011-05-13
I would like to thank you for the installation scripts. For the first time, I have been able to use my tablet computer. Ubuntu is so much better than windows for this interface, even though windows has by far the better handwriting recognition and onenote style application.

Using your scripts I have been able to get suspend resume working, and I am now running windows 7 under a robust operating environment.

I can recommend anyone trying to commission their HP TM2 farmiliarise themselves with the script in this thread.

I use KDE and have put the startup scripts into /etc/kde4/Xstartup where they set up the switcheroo directories properly.

The remaining problems  have are:

1. Lack of right click on the touchpad. Double fingered clicks work but they are cludgy. It also seems to lead to the mouse events being lost, or the driver is losing mouse events. The keyboard works, the touchpad and touch screen works to move the mouse but left clicks don't work.

2. Getting my Bluetooth working. It apparently shares its antenna with the wifi device and I have only been able to get this to work once by setting it up in Windows.

I am also going to try and get the wacom events sent through to windows 7 in virtual box. If anyone has any hints or clues in this area I would be very grateful for feedback.

Well done on the work so far. These are good devices and a great entry point into the cool world of touchy feely.

---

### Post by rougered on 2011-05-15
> **xdominex said:**
> Riccardo,

Does a two-finger tap work for right click? Unfortunately, normal "right-clicks" in the right-click box on the touchpad do not work. It makes me frustrated and sad because two-finger tap often moves the cursor off of whatever I want to right-click.

Also, do you need to use rotate with dual monitors? If not, you should be able to slap my rotate-display script (attached in my previous post) into your /bin/ folder, change it to be executable, and run "rotate-display (none,half,left,right)" according to how you want your screen oriented. If you want me to modify it to disable the touchpad in specific orientations, I can do that for you. The following commands can also disable or enable the touchpad:
To enable:```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
```To disable:```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0
```I hope this can get you going for now until we get a complete fix figured out.

(BTW, my resume-from-suspend is working fine now)

Hi,
        sorry for the delay, i did not see your post.

i tried the xinput set-prop stuff and indeed it activates the right click...only problem is that now both buttons do right click. Also the trackpad (without any rotation behaves strangely when i have a finger on the button and another on the trackpad.

should i deactivate multitouch? 

thx
Riccardo

---

### Post by android272 on 2011-05-16
is it possible to turn off the touch so that I can only use my stylus.  in windows there is a way to do this but there is tomany windows to go thought to turn it on and off. so I just leave it off of the most part. 

I like to have the touch turned off for when I draw or write but on when im doing everything elss. I would like a button that just switches it on and off.

what I think would be cool is to have a icon that brings up a menu that would give you different tablet options. Rotate, on/off Touch, Keyboard, and some other stuff.  Ideally I would like this menu to pop up when you would hit the rotate button but since that does not work yet a icon on my task bar will just have to do.

Tell me what you guys think about this idea. Here is a concept I made of what this would look like. 

http://s42.photobucket.com/albums/e347/Android27/?action=view&amp;current=Untitledpicture.jpg" target="_blank"><img src="http://i42.photobucket.com/albums/e347/Android27/Untitledpicture.jpg" border="0" alt="Photobucket

---

### Post by Favux on 2011-05-16
Hi android272,

Magick Rotation already does most of what you are asking for I think:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

We are about to release v. 1.4 which is the update for Natty.

---

### Post by chadmerkert on 2011-09-20
Has anyone played with the Beta of 11.10 on their TM2T yet? So many things are different, I think we will have to figure out all of the problems again from scratch! I couldn't figure out how to get vgaswitcheroo work, as it didn't show up at all. And the scripts that were part of the GDM postlogin are now unable to work because they switched the Login screen to LightDM. I will download the next beta, and play around with it more, and try to get everything working again! Any input will be helpful! :)

---

### Post by M42 on 2011-09-27
Chad,

I have been playing around with the beta2 version, the beta1 had way too many issues.  I could not get your scripts to work either.  I went back to loading the lenovo module that just turns off the ATI graphics completely.  However, suspend doesn't work when using that module. I'm going to give the FGLRX driver another try.  It would not work a few days ago but a lot of updates have come along since then

Good luck.

---

### Post by chadmerkert on 2011-09-27
I have played around with the beta, and I have given up trying to get LightDM to work with my script. I found that by installing gdm, and then using my script, everything works the way it currently does. I might add it to the script, so it automatically installs GDM. But for now, just run ```
sudo apt-get install gdm
``` and then run the installation script again. Everything should work fine then. Let me know if you have any problems.

---

### Post by fashion_m on 2011-09-28
Hello, I consider buying HP Touchsmart TM2-2190ea. Does it have any problems with Ubuntu (or any other problems)?
Specs are:
[B]Intel Pentium U5400 processor 
 3GB memory 
 320 GB Hard Drive 
 ATI Mobility Radeon 5450 graphics, with 512MB dedicated memory[/B]

---

### Post by chadmerkert on 2011-09-29
I do not know, because I don't have that model, but if it has Hybrid graphics(both Intel and ATI) then you may have problems. Mine has hybrid graphics, but there are ways of getting it to work well. So basically, it probably will work, but you may need to mess around to get it to work. If you need help, just come back to this thread, or ask around on UbuntuFourms, and I'm sure someone will be able to help! Oh and if it has the same finger print scanner as my TM2T-2100, then that's not going to work, at least not yet.

---

### Post by dugh on 2011-12-08
Thanks for the gdm tip

My main issue in 11.10 is that after it boots I have to close and reopen the lid twice for anything to show up on the monitor.  But I guess I can live with that.

And when I'm typing sometimes the curse jumps around I guess when my hand accidentally brushes the clickpad or something.

This PPA may help with clickpad issues:
[https://launchpad.net/~sergio91pt/+archive/synaptics+clickpads](https://launchpad.net/~sergio91pt/+archive/synaptics+clickpads)

In the terminal:
```
sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by chadmerkert on 2011-12-08
Thanks for the Tip on the PPA, I will have to check it out, and see if it helps. I do have some issues of clicking accidentally when typing, so it would be a welcomed fix!

As for the problem of the black screen at the login screen, I have found a fix for it! Just run the attached script with sudo, or simply add the following to the end of /etc/gdm/Init/Default but before the exit line:
```
xrandr -o left
xrandr -o normal
```

Basically it is just rotating the display to the left and then back to normal when GDM loads, which for some reason triggers the backlight to come back on. Not the greatest fix, but it works great for me, and haven't had any problems. This fix will only work for GDM though, not LightDM.

---

