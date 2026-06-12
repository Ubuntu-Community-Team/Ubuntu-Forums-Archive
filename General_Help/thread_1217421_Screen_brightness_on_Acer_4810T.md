---
title: "Screen brightness on Acer 4810T"
date: 2009-07-19
forum: General Help
---

### Post by joelka on 2009-07-19
Hi.

I've just installed Ubuntu 9.04 on my Acer Aspire 4810Timeline. Everything seems to be working ok, except for the screen brightness. The [Fn]+[Up]/[Down] combination displays the popup and the bar is moving correctly, but the brightness remains the same. I've checked the contents of /proc/acpi/video/OVGA/DD02/brightness which changes accordingly. Anyone who's had the same problem, and knows how to solve it?

---

### Post by OrnithO on 2009-07-24
Just run this in a terminal, it worked for me on my Acer Timeline 4810TZ-4011 on Linux Mint (which is based on Ubuntu 9.04)
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```I found it [here]("http://ubuntuforums.org/showthread.php?t=1165087&highlight=4810t&page=10"), the advice was given by alvinator@

Hope it'll work for you ;)

---

### Post by Incompetnce on 2009-08-17
This fix works. thanks. But it resets when I restart my laptop. Can I make this change permanent?

---

### Post by OrnithO on 2009-08-27
Sorry, I forgot that...:oops:
You have to go to System > Preferences > Startup Application Preferences.
Then Click on add. For the name, call it Screen Brightness (or anything you want) and put the code under command. The restart and check if it worked.
Hope you will find your way through. My Ubuntu is in French and I don't know the correct name in English...

---

### Post by edd07 on 2009-08-27
Hi.

I have a similar problem with (kind of) the same computer. The exact model is 4810TZ-4013

Running the command does nothing, I'm still unable to change the brighntess

Any ideas? This thing is starting to hurt my eyes :P

Thanks in advance

---

### Post by Arlanthir on 2009-09-24
I updated the BIOS to 2.28, logged into Ubuntu, changed the screen brightness... and it worked!

Well, the bad news is every time I do that, the system locks up =X

EDIT: bricked it trying to downgrade the BIOS, got it back, still no backlight control too, but this time I won't update the BIOS :P

---

### Post by coolvibe on 2009-09-30
> **OrnithO said:**
> Just run this in a terminal, it worked for me on my Acer Timeline 4810TZ-4011 on Linux Mint (which is based on Ubuntu 9.04)
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```I found it [here]("http://ubuntuforums.org/showthread.php?t=1165087&highlight=4810t&page=10"), the advice was given by alvinator@

Hope it'll work for you ;)

Found a workaround for the 5810T on karmic that will persist across reboots:

Add the following to the GRUB_CMD_LINUX_DEFAULT entry in /etc/default/grub: acpi_backlight=vendor

Don't forget to run update-grub.

---

### Post by edd07 on 2009-10-04
> **coolvibe said:**
> Found a workaround for the 5810T on karmic that will persist across reboots:

Add the following to the GRUB_CMD_LINUX_DEFAULT entry in /etc/default/grub: acpi_backlight=vendor

Don't forget to run update-grub.
Uh-oh, I've just installed Karmic, but I don't have a /etc/default/grub file.

Any ideas?

---

### Post by coolvibe on 2009-10-05
> **edd07 said:**
> Uh-oh, I've just installed Karmic, but I don't have a /etc/default/grub file.

Any ideas?

If you upgraded, you are still using the old GRUB. Just add them to your kopts in the menu.lst in /boot/grub, (don't forget to run update-grub afterwards) or just upgrade to GRUB 2 :)

EDIT: Oh, and KMS might be in the way as well, as it will map your screen to LVDS1 instead of LVDS, so desable that too. You can disable KMS by setting "nomodeset" as a kernel parameter.

---

### Post by edd07 on 2009-10-05
> **coolvibe said:**
> If you upgraded, you are still using the old GRUB. Just add them to your kopts in the menu.lst in /boot/grub, (don't forget to run update-grub afterwards) or just upgrade to GRUB 2 :)

EDIT: Oh, and KMS might be in the way as well, as it will map your screen to LVDS1 instead of LVDS, so desable that too. You can disable KMS by setting "nomodeset" as a kernel parameter.
Ok, I tried to upgrade GRUB and it didn't work (it booted me into a grey screen with a black rectangle on the center of the screen), so I added the option to old-school grub's menu.lst.

So, you're saying KMS will break this solution? Or will I have to do something else when it's enabled?

EDIT: Nevermind, it doesn't work. Seems like my laptop is trying really hard to blind me :-(

---

### Post by Arlanthir on 2009-10-06
> **edd07 said:**
> Ok, I tried to upgrade GRUB and it didn't work (it booted me into a grey screen with a black rectangle on the center of the screen), so I added the option to old-school grub's menu.lst.

So, you're saying KMS will break this solution? Or will I have to do something else when it's enabled?

EDIT: Nevermind, it doesn't work. Seems like my laptop is trying really hard to blind me :-(

I had the same problem and fixed it easily by adding "nomodeset acpi_backlight=vendor" as sugested to the kernel line of GRUB2 ;) 
To try it once, press 'e' on the boot screen to edit your grub boot command and add those after "quiet splash". Keep in mind it's not the last line, but probably the one above it.

---

### Post by edd07 on 2009-10-06
Hmmm. I managed to get GRUB2 working, but I still have no control over my screens brightness :-(

---

### Post by Arlanthir on 2009-10-06
> **edd07 said:**
> Hmmm. I managed to get GRUB2 working, but I still have no control over my screens brightness :-(

Did you edit the boot line as I said?

---

### Post by edd07 on 2009-10-06
I did. It fixed the grey screen I used to get with GRUB 2, but no changes brightness-wise

---

### Post by Arlanthir on 2009-10-06
> **edd07 said:**
> I did. It fixed the grey screen I used to get with GRUB 2, but no changes brightness-wise

I suppose you're not on Karmic or you wouldn't have to actually install GRUB2, so I'd wager you better wait for it and it will be fixed (at least manageable like mine) ;)

---

### Post by edd07 on 2009-10-06
I *am* on karmic, but I didn't do a fresh install, and upgrades leave your bootloader alone to be safe. I'll wait until the final release and see if I can find a solution then. 

Thanks a lot for your help and time.

---

### Post by Sashin on 2009-10-07
I am on karmic, I DID do a fresh install (alpha 6) and I'm up to date but its not working. Neither is the touchpad on off button which is supposed to work.

---

### Post by Sashin on 2009-10-07
with "nomodeset" it works but makes the desktop slow to a crawl.

---

### Post by defazn on 2009-10-07
tried the suggest commands didnt work for me. i have the aspire 4810t (from office depot) 

this dimness is really annoying making me wanna dual boot back into win7.

someone help thanks

---

### Post by tijmz on 2009-10-08
> **OrnithO said:**
> Just run this in a terminal, it worked for me on my Acer Timeline 4810TZ-4011 on Linux Mint (which is based on Ubuntu 9.04)
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

I tried this on Karmic (on a 4810T) and got this:

```
tijmz@Eurydice:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26
```

Does anyone have any suggestions? I'd like to be able to change brightness settings :)

---

### Post by Arlanthir on 2009-10-08
> **tijmz said:**
> I tried this on Karmic (on a 4810T) and got this:

```
tijmz@Eurydice:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26
```

Does anyone have any suggestions? I'd like to be able to change brightness settings :)

Read the last page or so of comments, you have to add "nomodeset acpi_backlight=vendor" to the kernel line of GRUB2.

---

### Post by Vertumnus on 2009-11-23
Hi,

When I try to edit the /etc/default/grub file and run "update-grub", I get this:

```
/etc/default/grub: 9: nomodeset acpi_backlight=vendor: not found
```

I can't find anyone else who had this problem. Any ideas?

---

### Post by Arlanthir on 2009-11-24
> **Vertumnus said:**
> Hi,

When I try to edit the /etc/default/grub file and run "update-grub", I get this:

```
/etc/default/grub: 9: nomodeset acpi_backlight=vendor: not found
```

I can't find anyone else who had this problem. Any ideas?

It's probably a typo, let me give you an example of how it should look:

```
(...)
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
(...)

```

Compare it with yours and post the results :)

---

### Post by Vertumnus on 2009-11-24
YESSSS!!!  It works!  Although for some reason, the Ubuntu "loading" icon that appears when I first turn my computer on is now stretched. I think I can put up with that though.  Thanks!

---

### Post by Arlanthir on 2009-11-24
> **Vertumnus said:**
> YESSSS!!!  It works!  Although for some reason, the Ubuntu "loading" icon that appears when I first turn my computer on is now stretched. I think I can put up with that though.  Thanks!

Good to know :)
That's probably a side effect from the 'nomodeset' part. It turns off KMS so the boot get's uglier.

---

### Post by jim.hitch on 2009-12-08
> **Arlanthir said:**
> It's probably a typo, let me give you an example of how it should look:

```
(...)
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
(...)

```

Compare it with yours and post the results :)

Hi

Just tried all this with Kubuntu 9.10 4.3.4, but no joy. any ideas?

---

### Post by Arlanthir on 2009-12-08
> **jim.hitch said:**
> Hi

Just tried all this with Kubuntu 9.10 4.3.4, but no joy. any ideas?

Yes, it doesn't work for me as well on KDE, only on gnome.
On KDE I have to use the script from [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes) ;)

The worst part is it needs root access, otherwise mapping it to the keys would be perfect...

---

### Post by jim.hitch on 2009-12-09
Shame.

I think I tried the script before, but failed to get it to work. When I have time, I'll give it another go. Not very good with scripts, me, The only scripts I've done are simple bash scripts so far, and this looks more complex than that.

I'll work it out.

Jim

---

### Post by Arlanthir on 2009-12-09
> **jim.hitch said:**
> Shame.

I think I tried the script before, but failed to get it to work. When I have time, I'll give it another go. Not very good with scripts, me, The only scripts I've done are simple bash scripts so far, and this looks more complex than that.

I'll work it out.

Jim

You don't have to 'do' anything, just copy the contents to a .sh file, backlight.sh for instance.
Then write on a terminal:

chmod +x backlight.sh

and then you just have to run it like so:

backlight.sh down
backlight.sh up

:)

---

### Post by bluesky2210 on 2009-12-10
It's my grub:
> 
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

I can't change blacklight brightness
Help me :(
I use Ubuntu 9.10 ,my laptop: ASPRIRE 4736Z

---

### Post by aioan on 2009-12-28
> **Sashin said:**
> with "nomodeset" it works but makes the desktop slow to a crawl.

On my laptop worked great while in BIOS v1.10

After upgrading to v1.31 using the brightness control brings the system to a "low power" mode making it unusable... Any application using 3d is REALLY slow and crashes when trying to run glxgears or Google Earth.

Any ideas?

Regards,

---

### Post by executorvs on 2010-03-11
I'm trying to draw more attention to this bug on launchpad as it also affects other timeline models and I suspect a few of the other Aspire series as well.

there is a bug report at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717)

I have marked as duplicates all of the bugs related to the changes in how the brightness keys have failed over time.

if anyone with either a 3810(TZ/TG) or 4810(TZ/TG) or 5810TG could post exact details of how this bug affects there computer under lucid it would be appreciated.

---

### Post by jsampaio57 on 2010-03-13
you need to
sudo update-grub 

cheers...

---

### Post by jsampaio57 on 2010-03-13
> **bluesky2210 said:**
> It's my grub:

I can't change blacklight brightness
Help me :(
I use Ubuntu 9.10 ,my laptop: ASPRIRE 4736Z



you need to:
sudo update-grub

cheers...

---

### Post by executorvs on 2010-03-13
there seem to be two problems, one is with a lot of acers and the other is with intel powered graphics cards. 
The acer problem is on launchpad [https://bugs.launchpad.net/bugs/397617](https://bugs.launchpad.net/bugs/397617) and you may find a work around in one of the listed duplicates.

The bug affecting the intel graphics cards is related to KMS and is on launchpad at [https://bugs.launchpad.net/bugs/397617](https://bugs.launchpad.net/bugs/397617) again there are workarounds listed. 

the larger annoyance in all of this is that in many cases the fixes that work for some hardware don't work for others it can be a firmware difference which makes or breaks the effectiveness of any of the workarounds listed.. I just want brightness buttons that work :-(

---

### Post by hesapotman on 2010-11-12
I am using ...

Laptop: Acer Aspire 4736z
Graphics: Intel GMA 4500M
OS: Ubuntu Maverick Meerkat (10.10)
Kernel: 2.6.35-23-generic

And I managed to solve this problem for myself using some modified scripts/advice from other forum posts.

First, create a folder on your desktop called "brightness", go into the directory, create two files: brup and brdn, and set their permissions to execute.

```
mkdir /home/<YOUR_USERNAME>/Desktop/brightness

cd /home/<YOUR_USERNAME>/Desktop/brightness

touch brup brdn

chmod 0755 br*
```

Next, we'll edit "brup"

```
gedit brup
```

Adding the following text to "brup"

```
#!/bin/bash

# these are the possible values:
# 00  19 32 4b 64 7d 96 af c8 e1 ff
# 100 90 80 70 60 50 40 30 20 10 00

Current=`sudo setpci -s 00:02.0 F4.B`
case $Current in
  e1)
    sudo setpci -s 00:02.0 F4.B=c8
  ;;
  c8)
    sudo setpci -s 00:02.0 F4.B=af
  ;;
  af)
    sudo setpci -s 00:02.0 F4.B=96
  ;;
  96)
    sudo setpci -s 00:02.0 F4.B=7d
  ;;
  7d)
    sudo setpci -s 00:02.0 F4.B=64
  ;;
  64)
    sudo setpci -s 00:02.0 F4.B=4b
  ;;
  4b)
    sudo setpci -s 00:02.0 F4.B=32
  ;;
  32)
    sudo setpci -s 00:02.0 F4.B=19
  ;;
  19)
    sudo setpci -s 00:02.0 F4.B=00
  ;;
  *)
    sudo setpci -s 00:02.0 F4.B=00
  ;;
esac
```

Now we "Save" the file and "Close" gedit.

Next, we'll edit "brdn"

```
gedit brdn
```

Adding the following text to "brdn"

```
#!/bin/bash

# these are the possible values:
# 00  19 32 4b 64 7d 96 af c8 e1 ff
# 100 90 80 70 60 50 40 30 20 10 00

Current=`sudo setpci -s 00:02.0 F4.B`
case $Current in
  00)
    sudo setpci -s 00:02.0 F4.B=19
  ;;
  19)
    sudo setpci -s 00:02.0 F4.B=32
  ;;
  32)
    sudo setpci -s 00:02.0 F4.B=4b
  ;;
  4b)
    sudo setpci -s 00:02.0 F4.B=64
  ;;
  64)
    sudo setpci -s 00:02.0 F4.B=7d
  ;;
  7d)
    sudo setpci -s 00:02.0 F4.B=96
  ;;
  96)
    sudo setpci -s 00:02.0 F4.B=af
  ;;
  af)
    sudo setpci -s 00:02.0 F4.B=c8
  ;;
  c8)
    sudo setpci -s 00:02.0 F4.B=e1
  ;;
  *)
    sudo setpci -s 00:02.0 F4.B=e1
  ;;
esac
```

Now we "Save" the file and "Close" gedit.

Next, we would like to put those files somewhere in the System. I chose to create a directory called "brightness" in the "/usr/bin" path. After that, we copy the scripts we just wrote (brup & brdn) to that path.

```
sudo mkdir /usr/bin/brightness

sudo cp * /usr/bin/brightness
```

Now we want to change the "sudoers" file so that we can execute these scripts without having to enter a password each time.

```
sudo gedit /etc/sudoers
```

After the line "#Cmnd alias specification", we want to add a line aliasing our brightness commands.

```
# Cmnd alias specification
Cmnd_Alias BRIGHT_CMDS = /usr/bin/brightness/brup, /usr/bin/brightness/brdn
```

And at the very bottom of the file (AFTER the line "%admin ALL=(ALL) ALL"), we want to add a line permitting all users to execute those scripts without having to enter a password.

```
ALL ALL=(ALL) NOPASSWD: BRIGHT_CMDS
```

Now we "Save" the file and "Close" gedit.

Painful terminal crap is over ... So close it! :)

Now we go to the menu-bar selecting from the cascading options: System -> Preferences -> Keyboard Shortcuts

In the box that opens, click the "Add" button and enter the following:

```
Name: Brightness Up
Command: gksudo /usr/bin/brightness/brup
```

And click "Apply".

Next we click the "Add" button again and enter the following:

```
Name: Brightness Down
Command: gksudo /usr/bin/brightness/brdn
```

And click "Apply".

Now, if you look at the bottom of the list of Keyboard Shortcuts, you should see two "Custom Shortcuts" (the ones you just entered).

If you click on the right side of the listings (in the "Shortcut" column), you will be able to enter a keystroke (or combination) that will activate your "Brightness Up" and "Brightness Down" actions.

For me, I chose CTRL+WIN+RIGHT_ARROW for "Brightness Up" and CTRL+WIN+LEFT_ARROW for "Brightness Down. But you can use any keystrokes you like as long as they don't conflict with other existing shortcuts.

Now click "Close" in the "Keyboard Shortcuts" box.

THAT'S IT! You should be good to go now. Give it a try with your selected keystrokes and see if it works for you. I sure hope this helps someone.

---

### Post by hesapotman on 2010-11-12
> **executorvs said:**
> there seem to be two problems, one is with a lot of acers and the other is with intel powered graphics cards. 
The acer problem is on launchpad [https://bugs.launchpad.net/bugs/397617](https://bugs.launchpad.net/bugs/397617) and you may find a work around in one of the listed duplicates.

The bug affecting the intel graphics cards is related to KMS and is on launchpad at [https://bugs.launchpad.net/bugs/397617](https://bugs.launchpad.net/bugs/397617) again there are workarounds listed. 

the larger annoyance in all of this is that in many cases the fixes that work for some hardware don't work for others it can be a firmware difference which makes or breaks the effectiveness of any of the workarounds listed.. I just want brightness buttons that work :-(

Yes indeed, different hardware reacts differently. For example, the "workaround" scripts I found specified brightness values in hex where "FF" was supposed to be 100% brightness and 19 was supposed to be 10% brightness. Well it only took me a moment to figure out that those numbers were exactly ***-backwards (for MY hardware). So I modified the scripts such that "E1" was 10% and "00" was 100%.

So for goodness sake, if anyone attempts to use the fix I listed above, PLEASE be sure to note my hardware/software specs. If you're not using the same hardware/software, I have no idea what might happen when you go messing around.

---

### Post by Noob-untu on 2010-11-14
Hi everyone,
hesapotman,

I just wanted to say that I tried your thingy and it worked for me. Wow, I didn't really have much hope, after all the solutions I have tried.

Downside: Power manager remains unable to change brightness, but hey, at least, until a comprehensive solution is found, my eyes won't drop dead now.

Downside: Sometimes, it gets a little stuck for a few seconds, and a window with the title "Starting Administrative Application" can be seen in the task bar, and the cursor gets into "loading" mode. CPU gets 'intense' while trying to sort that out.

Downside: Also, I get the impression that the max brightness I can set is dimmer than it used to be. Is it possible to change the range of brightness set in the brup and brdn files? (I'm more interested in learning this out of curiosity than of practical reasons, so you don't really have to bother explaining).

But all in all, thanks a lot, I appreciate that you bothered to write a fool-proof guide!

Acer Extensa 5235
Ubuntu 10.04
GMA 4500M

---

### Post by hesapotman on 2010-11-17
> **Noob-untu said:**
> Hi everyone,
hesapotman,

I just wanted to say that I tried your thingy and it worked for me. Wow, I didn't really have much hope, after all the solutions I have tried.

Downside: Power manager remains unable to change brightness, but hey, at least, until a comprehensive solution is found, my eyes won't drop dead now.

Downside: Sometimes, it gets a little stuck for a few seconds, and a window with the title "Starting Administrative Application" can be seen in the task bar, and the cursor gets into "loading" mode. CPU gets 'intense' while trying to sort that out.

Downside: Also, I get the impression that the max brightness I can set is dimmer than it used to be. Is it possible to change the range of brightness set in the brup and brdn files? (I'm more interested in learning this out of curiosity than of practical reasons, so you don't really have to bother explaining).

But all in all, thanks a lot, I appreciate that you bothered to write a fool-proof guide!

Acer Extensa 5235
Ubuntu 10.04
GMA 4500M

Hey, I'm really glad that worked for you! I know some of the gurus get their panties all bunched up at having such a detailed guide (they consider it condescending). But it's important to remember that not every Ubuntu user is a computer wizard, and sometimes people need a step-by-step guide telling them every little detail.

Yes, having the "Starting Administrative Application" thing show up in the taskbar - even for a moment - is a pain. But it's much better than having to enter the password for each 10% brightness step. However, I've never had any issues with the scripts eating CPU or causing slow-down. I guess it would be best not to change brightness during some mission-critical real-time apps then.

I have found the built-in Power Manager to be pretty much worthless at controlling the monitor (it won't even put my monitor to sleep correctly). It's just one more of the "default apps" that Canonical has failed to repair for a long time now. Anyway, if you're having that problem also, I used a fix where I replaced gnome-screensaver with xscreensaver. Topic is here: [http://ubuntuforums.org/showthread.php?t=1358946]("http://ubuntuforums.org/showthread.php?t=1358946")

As far as I am aware, display brightness is set as a 1-byte hexadecimal value. The range is from 00 to FF (in normal decimal, that's 0 to 255). The maximum brightness setting (00) is as low as the value can go, so it's probably the brightest your monitor can get. It's possible that the backlights in your monitor are aging and aren't as bright as they used to be. Or it's possible that you're remembering your monitor's brightness being brighter than it really was.

Cheers!

---

### Post by tuxonapogostick on 2010-11-17
Xmodmap might solve your problem.
I suggest that you do:
1. get the keysym name of the key via **xev** that you would like to use for screen brightness adjustment
2. find the keysym name for the screen brightness 
3. do : ```
xmodmap -e " keysym function4 = Brightness" 
```for example. This is just an example actual keysym names will probably different than "function4" or "Brightness".

---

### Post by hesapotman on 2010-11-23
> **tuxonapogostick said:**
> Xmodmap might solve your problem.
I suggest that you do:
1. get the keysym name of the key via **xev** that you would like to use for screen brightness adjustment
2. find the keysym name for the screen brightness 
3. do : ```
xmodmap -e " keysym function4 = Brightness" 
```for example. This is just an example actual keysym names will probably different than "function4" or "Brightness".

I did tinker around a bit with remapping keys instead of creating brightness keyboard shortcuts. But there seems to be something at a lower-level that prevents me from using the standard "XF86MonBrightnessUp" and "XF86MonBrightnessDown" keys as shortcuts. Sure, I can request they be used as shortcuts, but it just doesn't work.

Could you provide some more detail about how your solution can help with this problem? Thanks for the input!

---

### Post by m0jo1337 on 2010-11-25
I have successfully set XF86MonBrightnessUp & XF86MonBrightnessDown in the Shortcuts menu to execute the script. By simply try pressing those keys as a shortcut.

-> I pressed Fn+LeftArrow and shortcut menu instantly replacced it with XF86MonBrightnessUp and it works like a charm

---

### Post by garfieldenforce on 2010-12-04
Thanks so much Hesapotman! Your solution works nicely on my laptop, and I have no trouble using Fn+left and Fn+right.
fyi my laptop is an Acer 4810T and I'm running Maverick.

---

### Post by marquinos on 2010-12-30
This works perfect for my laptop ACER TM 5735 Graphic card T4500M, with Ubuntu 10.10 64 bits:
[http://ubuntuforums.org/showpost.php?p=10112062&postcount=6](http://ubuntuforums.org/showpost.php?p=10112062&postcount=6)
Best regards.

---

### Post by rs87424 on 2011-01-14
I have an Acer Aspire 4810TZ and I tried the brup brdn brightness fix and I found that the path usr/bin already has a file called brightness with some random media inside it.

I am running Maverick 10.10 as of now. I was just trying to figure out the specifics of the fix. Would there be any other path that I could put the file instead of usr/bin?

---

### Post by dummiebeginner on 2011-03-20
> **hesapotman said:**
> I am using ...

Laptop: Acer Aspire 4736z
Graphics: Intel GMA 4500M
OS: Ubuntu Maverick Meerkat (10.10)
Kernel: 2.6.35-23-generic

And I managed to solve this problem for myself using some modified scripts/advice from other forum posts.

First, create a folder on your desktop called "brightness", go into the directory, create two files: brup and brdn, and set their permissions to execute.

```
mkdir /home/<YOUR_USERNAME>/Desktop/brightness

cd /home/<YOUR_USERNAME>/Desktop/brightness

touch brup brdn

chmod 0755 br*
```

Next, we'll edit "brup"

```
gedit brup
```

Adding the following text to "brup"

```
#!/bin/bash

# these are the possible values:
# 00  19 32 4b 64 7d 96 af c8 e1 ff
# 100 90 80 70 60 50 40 30 20 10 00

Current=`sudo setpci -s 00:02.0 F4.B`
case $Current in
  e1)
    sudo setpci -s 00:02.0 F4.B=c8
  ;;
  c8)
    sudo setpci -s 00:02.0 F4.B=af
  ;;
  af)
    sudo setpci -s 00:02.0 F4.B=96
  ;;
  96)
    sudo setpci -s 00:02.0 F4.B=7d
  ;;
  7d)
    sudo setpci -s 00:02.0 F4.B=64
  ;;
  64)
    sudo setpci -s 00:02.0 F4.B=4b
  ;;
  4b)
    sudo setpci -s 00:02.0 F4.B=32
  ;;
  32)
    sudo setpci -s 00:02.0 F4.B=19
  ;;
  19)
    sudo setpci -s 00:02.0 F4.B=00
  ;;
  *)
    sudo setpci -s 00:02.0 F4.B=00
  ;;
esac
```

Now we "Save" the file and "Close" gedit.

Next, we'll edit "brdn"

```
gedit brdn
```

Adding the following text to "brdn"

```
#!/bin/bash

# these are the possible values:
# 00  19 32 4b 64 7d 96 af c8 e1 ff
# 100 90 80 70 60 50 40 30 20 10 00

Current=`sudo setpci -s 00:02.0 F4.B`
case $Current in
  00)
    sudo setpci -s 00:02.0 F4.B=19
  ;;
  19)
    sudo setpci -s 00:02.0 F4.B=32
  ;;
  32)
    sudo setpci -s 00:02.0 F4.B=4b
  ;;
  4b)
    sudo setpci -s 00:02.0 F4.B=64
  ;;
  64)
    sudo setpci -s 00:02.0 F4.B=7d
  ;;
  7d)
    sudo setpci -s 00:02.0 F4.B=96
  ;;
  96)
    sudo setpci -s 00:02.0 F4.B=af
  ;;
  af)
    sudo setpci -s 00:02.0 F4.B=c8
  ;;
  c8)
    sudo setpci -s 00:02.0 F4.B=e1
  ;;
  *)
    sudo setpci -s 00:02.0 F4.B=e1
  ;;
esac
```

Now we "Save" the file and "Close" gedit.

Next, we would like to put those files somewhere in the System. I chose to create a directory called "brightness" in the "/usr/bin" path. After that, we copy the scripts we just wrote (brup & brdn) to that path.

```
sudo mkdir /usr/bin/brightness

sudo cp * /usr/bin/brightness
```

Now we want to change the "sudoers" file so that we can execute these scripts without having to enter a password each time.

```
sudo gedit /etc/sudoers
```

After the line "#Cmnd alias specification", we want to add a line aliasing our brightness commands.

```
# Cmnd alias specification
Cmnd_Alias BRIGHT_CMDS = /usr/bin/brightness/brup, /usr/bin/brightness/brdn
```

And at the very bottom of the file (AFTER the line "%admin ALL=(ALL) ALL"), we want to add a line permitting all users to execute those scripts without having to enter a password.

```
ALL ALL=(ALL) NOPASSWD: BRIGHT_CMDS
```

Now we "Save" the file and "Close" gedit.

Painful terminal crap is over ... So close it! :)

Now we go to the menu-bar selecting from the cascading options: System -> Preferences -> Keyboard Shortcuts

In the box that opens, click the "Add" button and enter the following:

```
Name: Brightness Up
Command: gksudo /usr/bin/brightness/brup
```

And click "Apply".

Next we click the "Add" button again and enter the following:

```
Name: Brightness Down
Command: gksudo /usr/bin/brightness/brdn
```

And click "Apply".

Now, if you look at the bottom of the list of Keyboard Shortcuts, you should see two "Custom Shortcuts" (the ones you just entered).

If you click on the right side of the listings (in the "Shortcut" column), you will be able to enter a keystroke (or combination) that will activate your "Brightness Up" and "Brightness Down" actions.

For me, I chose CTRL+WIN+RIGHT_ARROW for "Brightness Up" and CTRL+WIN+LEFT_ARROW for "Brightness Down. But you can use any keystrokes you like as long as they don't conflict with other existing shortcuts.

Now click "Close" in the "Keyboard Shortcuts" box.

THAT'S IT! You should be good to go now. Give it a try with your selected keystrokes and see if it works for you. I sure hope this helps someone.

So I did all of that and it worked, but when I rebooted later, it was gone and doesn't work anymore.

Anyone?

---

### Post by hesapotman on 2011-08-09
> **rs87424 said:**
> I have an Acer Aspire 4810TZ and I tried the brup brdn brightness fix and I found that the path usr/bin already has a file called brightness with some random media inside it.

I am running Maverick 10.10 as of now. I was just trying to figure out the specifics of the fix. Would there be any other path that I could put the file instead of usr/bin?

Yes, you certainly can use any folder name you want under "/usr/bin" ... It doesn't have to be "brightness."

You can call it "/usr/bin/backlight" or even "/usr/bin/rosebud" if you like.

But if you do choose a different path name, you need to be sure that you use that different path name throughout my instructions. So, for example, your keyboard shortcut might point to "/usr/bin/rosebud/brup" instead of "/usr/bin/brightness/brup".

Good luck!

---

### Post by hesapotman on 2011-08-09
> **dummiebeginner said:**
> So I did all of that and it worked, but when I rebooted later, it was gone and doesn't work anymore.

Anyone?

You're saying all the files/folders you created along with the keyboard shortcuts were gone after rebooting?

With the problem you're describing (and the name "dummiebeginner"), my first guess that perhaps you are running Ubuntu from a Live CD?

If you are using a Live CD, you need to understand that you cannot make any changes (like creating folders/files and keyboard shortcuts) that remain after shutdown/reboot. In order to make permanent changes, you can do one of two things ... 

1) Instead of a Live CD, try to run Ubuntu from a Live USB thumbdrive WITH A PERSISTENCE FILE. This allows changes to be saved even after shutdown/reboot.

2) Go ahead and install Ubuntu on your computer which obviously allows changes to be saved after shutdown/reboot. I can almost promise you won't regret putting Ubuntu on your computer (as long as you don't use that horrific, shark-jumping, "Unity" desktop that came out with Natty).

If you were not using a Live CD when you experienced this problem, then I'm not sure what to tell you except ... Good luck!

---

