---
title: "Blinking cursor for about 12 seconds before login screen appears."
date: 2010-10-20
forum: General Help
---

### Post by Lnxphrk on 2010-10-20
Hello fellow geeks, just joined and am looking forward to getting to know everyone.:)

On to my question: I installed Ubuntu 10.10 alongside my Windows 7 os in a dual boot config. I used an installation disk and allowed the ubuntu installer to do all the resizing of partitions, installing of grub, etc. The install is working great and I haven't needed to boot my windows os since which is great. The only complaint I have is that it takes it takes a bit longer to boot than windows did for some reason. The culprit is a blinking cursor that comes up and remains for about 12-15 seconds before the grub menu appears. I already altered the boot option for the grub menu so that ubuntu is default and the option to select another os only appears for 3 seconds but I don't think this is related since the delay occurs before those options appear. I'm not really sure what is causing the delay. Is it looking for the loader? If so, is there a way to edit the configuration so doesn't have to search? As I mentioned, the install is running great otherwise. Thanks in advance - Lnxphrk

---

### Post by ThePhysician on 2010-10-20
Mine does the same thing, and all I am running is Linux on it.

---

### Post by drs305 on 2010-10-20
Lnxphrk,

Welcome to the Ubuntu forums.

One thing that comes to mind, since you stated it is already on the first drive searched by BIOS, is whether you have made any changes to the default resolution or are trying to use a background image. That might delay things while Grub tried to find and display the menu.

You might also check the UUIDs in grub.cfg to make sure they exist on your system. You can make a quick check with these two commands. I don't know if it's something that would slow down the display but they are checked beforehand:
```
sudo blkid && grep UUID /boot/grub/grub.cfg
```

---

### Post by Lnxphrk on 2010-10-20
Thanks for the response drs305. I see the UUID listed. Im not sure what you mean by a background image...do you mean on my desktop or elsewhere? I do have a wallpaper if thats what you mean, but no other splash screens or login mods like the ones found on gnomelook.org.

 Here are the results:

```
nemesis@NemesisSystem:~$ sudo blkid && grep UUID /boot/grub/grub.cfg
[sudo] password for nemesis: 
/dev/sda1: LABEL="PQSERVICE" UUID="DAA41C49A41C2B11" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="2C28035128031A0A" TYPE="ntfs" 
/dev/sda3: LABEL="Gateway" UUID="E2F00A3FF00A1A85" TYPE="ntfs" 
/dev/sda5: UUID="469f24bb-c002-4a26-9d5c-129f3c7204ac" TYPE="ext4" 
/dev/sda6: UUID="0937f778-d264-462b-b75e-c0f408807bce" TYPE="swap" 
linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=469f24bb-c002-4a26-9d5c-129f3c7204ac ro   quiet splash
linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=469f24bb-c002-4a26-9d5c-129f3c7204ac ro single
```Most importantly, I just realized I made a mistake when I posted my question. The blinking cursor appears AFTER the default os is selected in grub, not before. Im guessing this changes everything. My apologies.

---

### Post by drs305 on 2010-10-20
> **Lnxphrk said:**
>  I just realized I made a mistake when I posted my question. The blinking cursor appears AFTER the default os is selected in grub, not before. Im guessing this changes everything. My apologies.

Yes it does, but no problem.

First, have you tried a different kernel, if one is available from the menu.

If only one is available or that doesn't work, you could try highlighting the main Ubuntu menu entry, press "e" to enter the "edit" mode. Go to the end of the "linux" line. Remove the "quiet splash" if they are there, and add "nomodeset"  (no quotation marks). Once you have typed it (do not ENTER), press CTRL-x to resume booting.

If that boots to the desktop you probably need to update and/or install your video drivers.

---

### Post by Lnxphrk on 2010-10-20
> **drs305 said:**
> First, have you tried a different kernel, if one is available from the menu. The only options are the default, recovery mode, memtest and the windows 7 loader.

> **drs305 said:**
> 
If only one is available or that doesn't work, you could try highlighting the main Ubuntu menu entry, press "e" to enter the "edit" mode. Go to the end of the "linux" line. Remove the "quiet splash" if they are there, and add "nomodeset"  (no quotation marks). Once you have typed it (do not ENTER), press CTRL-x to resume booting.

If that boots to the desktop you probably need to update and/or install your video drivers.

Tried those options, it resumed booting when I pressed ctrl-x, once it got the the cursor it did the same thing which was blink for 10-12 seconds before going to the login screen.

Any other ideas? (Thanks for the help so far)

Lnxphrk

---

### Post by drs305 on 2010-10-20
Sorry, but I don't have any other ideas. 

As a moderator though, I can change the title if you like to reflect that it is hanging before the login screen and not before the grub menu. That's the best I can do. Let me know if you want me to do that.

---

### Post by Jebtrix on 2010-10-20
There is one thing you can try to see if its the login autostarting apps slow it up. This strips everything launched at login except for the login app itself. Doubt it but worth a shot :)

```
sudo mkdir /usr/share/gdm/nostart
sudo mv /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/at-spi-registryd-wrapper.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/metacity.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/onboard.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/gnome-power-manager.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/gnome-mag.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop /usr/share/gdm/nostart/
sudo mv /usr/share/gdm/autostart/LoginWindow/orca-screen-reader.desktop /usr/share/gdm/nostart
```

Reboot and check. 

To restore
```
sudo mv /usr/share/gdm/nostart/gnome-settings-daemon.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/at-spi-registryd-wrapper.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/metacity.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/onboard.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/gnome-power-manager.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/gnome-mag.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/libcanberra-ready-sound.desktop /usr/share/gdm/autostart/LoginWindow/
sudo mv /usr/share/gdm/nostart/orca-screen-reader.desktop /usr/share/gdm/autostart/LoginWindow/
```

---

### Post by Lnxphrk on 2010-10-20
> **drs305 said:**
> As a moderator though, I can change the title if you like to reflect that it is hanging before the login screen and not before the grub menu. That's the best I can do. Let me know if you want me to do that.
That would be great, thanks.

> **Jebtrix said:**
> There is one thing you can try to see if its the login autostarting apps slow it up. This strips everything launched at login except for the login app itself. Doubt it but worth a shot :)

Ill try that and report back. Question though, if it were auto starting apps...wouldn't the delay occur after the login? The load time between inputting my password and a usable desktop is only 2-3 seconds if that.

---

### Post by drs305 on 2010-10-20
> **Lnxphrk said:**
> Question though, if it were auto starting apps...wouldn't the delay occur after the login? The load time between inputting my password and a usable desktop is only 2-3 seconds if that.

Yes, assuming you are both talking about the apps started by Startup Applications. Those apps wouldn't cause the pre-login delay.

Thread title changed per OP request. I hope it's more accurate. If your next post doesn't include a quote the new title will stick to the posts as well as the thread title.

---

### Post by Lnxphrk on 2010-10-22
Downloaded a startup manager from the Ubuntu software manager and disabled all the auto-starting program and services. The wait between the grub menu and login remains the same. We already knew that wasn't the issue but I had to try lol. I counted the times the cursor blinks before the login appears and its about 40-45 times. Just doesn't seem right. Searches of the forum have turned up similar cases caused by varying issues. Most of the threads are older, some even by a few years and I'm not sure if its safe to try them with the current version of Ubuntu. Is there an option for making a system restore disk, something that would allow me to recover my install from an external image for example? Id like to have a back up so I can start trying some of these solutions. Thanks.

---

### Post by trikster_x on 2010-10-22
I know for myself and many others, boot and shutdown times have increased considerably in the 10.10 release.  My boot time has added at least three secs, and shutdown is now at a healthy 10-12 secs total.  In 10.04 it was about 6-8 secs to load and perhaps 4 secs to shutdown.  And the problem with a blinking cursor taking the place of usplash also cropped up upon upgrading my system.  It's not something that can be addressed easily, since the main problem most likely lies with the way the kernel has been built.  Just shows how much of a step back an upgrade can be sometimes.

---

### Post by drs305 on 2010-10-22
It's funny because I jumped into this thread when it initially sounded like a grub problem. But now a day later I realize that this happens on my computer as well. 10-12 seconds.

You can take a look at System, Administration, Log File Viewer - dmesg
For the record, on my system the delay is between:
> 
[    2.687603] ata8: port disabled. ignoring.
[   14.386284] udev[428]: starting version 163


I used Partimage to make backups for many years, but stopped when it wasn't capable of managing ext4. I don't know if it can now or not. Now I use fsarchiver run from a systemrescue cd. I think many are avid fans of rsync.

---

### Post by oregonbob on 2010-10-22
My desktop does it about the same, maybe a few seconds less, but when that is done it pops up to a login very quickly. It might be 20 seconds total. My system is Windows 7 dual boot and Linux always boots faster than Windows 7. I figure the pause is that it takes time to check out all the devices I have.

---

### Post by trikster_x on 2010-10-22
I've been using Ubuntu since 8.04, with the exception of 8.10(I was still getting used to linux at the time of it's release and thought it better to wait until I had a better foundation to upgrade).  I have to say I have noticed a steady deterioration in the OS's ability to display Usplash correctly.  From 9.04 on, it seems like I have always gotten a few lines of verbose mode output before usplash comes up and just before the login screen, with the amount of lines steadily increasing in subsequent releases.  Not that I care that much, I prefer to know what my computer is doing anyway, just seems like boot screens have been problematic for a while now.  I was particularly happy with Lucid's boot time and shutdown time, and with some of the other glitches in Maverick I am severely regretting upgrading.

---

### Post by ndefontenay on 2010-12-07
I have the same problem ever since Karmic Koala.

I know this is an old thread but I was hoping I could fix this issue.

My guess is: I'll have to live with it then.

The sad part is: If the blinking didn't occur, the boot time would be a nice sub 10 seconds boot.

---

### Post by Lnxphrk on 2010-12-09
> **ndefontenay said:**
> I have the same problem ever since Karmic Koala.
 
I know this is an old thread but I was hoping I could fix this issue.
 
My guess is: I'll have to live with it then.
 
The sad part is: If the blinking didn't occur, the boot time would be a nice sub 10 seconds boot.
 
Agreed, my boot time would be about the same:)
 
Ill admit, I havent looked into it any further.

---

