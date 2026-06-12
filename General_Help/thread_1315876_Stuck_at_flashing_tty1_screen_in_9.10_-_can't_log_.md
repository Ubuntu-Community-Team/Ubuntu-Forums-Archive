---
title: "Stuck at flashing tty1 screen in 9.10 - can't log on"
date: 2009-11-05
forum: General Help
---

### Post by eidolon21 on 2009-11-05
I upgraded from 9.04 to 9.10 recently.  After hitting the 'suspend' button on my laptop, the system crashed.  After restart, I get the 9.10 white Ubuntu logo, but then no graphical log-on interface, just text.

The text is blinking rapidly, have has tty1 after my laptop name.

I can boot from the recovery kernel and enter my name and password (can't enter password in the tty1 screen), and tried to follow some of the advice on the other forums for how to solve this but nothing is working.

When I do startx, I get "Fatal Server Error: No screens found".  It also has no drivers detected.  I don't know what to do now. 


Any help extremely appreciated!

---

### Post by eidolon21 on 2009-11-05
Any ideas?

---

### Post by yuko41 on 2009-11-12
same for me and it is veery annoying....Non of the kernels works for me...
it is HP Pavillion with Nvidia card and working fine with 9.04..

I do not know what to do now...

---

### Post by fortune777 on 2009-11-12
Same Problem Here ..
i restarted the system and when i try to loggin after giving the password then system log me off ...

Not able to login ...



Can any one tell how to solve this problem ??

---

### Post by ublintu on 2009-11-13
Hi,
The same in here. About 2 days earlier, I did an update. It installed lots of packages and I can remember just for a kernel update. After this, I rebooted and after the white ubuntu logo I get a black screen with this:
Ubuntu 9.10 ublintu-laptop tty1
ublintu-laptop login:
After when I restart my laptop, it`s boot normally, like as usual. This happening just about every second time.

---

### Post by ublintu on 2009-11-16
It`s still a problem for me. It`s happens randomly (maybe about every 2-3 boot).
I searched a little bit, but I did not find the solution jet.
Someone wrote: "you need to type  startx" (mmm maybe after login. Next time I will try)
and one more thing:
At boot this time  "start usplash and X on tty1". But no GUI. So it`s means something wrong with them?
I will search for it...

---

### Post by ublintu on 2009-11-16
I reinstalled usplash, xserver, reconfigure it. When I reinstalled xserver, I saw, it uninstall ubuntu-desktop. So I put it back and it`s installed xorg.(??????)
After 3 restart it`s happened again. I wrote my name and my password in and then startx. GUI started, but the shut down was wrong now and its returned to the log in screen. From there I could shut down.
The next restart was normal, but who knows when will it happen again!
What is the solution?

---

### Post by Alpyre on 2009-11-17
Hope this helps:
[http://ubuntuforums.org/showpost.php?p=8333038&postcount=7](http://ubuntuforums.org/showpost.php?p=8333038&postcount=7)

---

### Post by ublintu on 2009-11-17
Thank you 4 the answer, but for me it isn't depend on the USB disks. These days I did not plug USB disks and its still happening sometimes. 
I forget to post something: Sometimes my computer boot like the other's, but I dont have flashing screen.
 
(#7 "reinstall xserver". When someone make a clean install with karmic, ubuntu-desktop and xorg installed with it automatically? Are they part of the basic ubuntu installation?)

---

### Post by nerdy_kid on 2009-11-17
try deleting xorg.conf?  i tryed upgrading my NVIDIA drivers and the third boot up i did i couldnt startx....said no screens found.  deleted xorg.conf-- i was able to log in to fix stuff better.

---

### Post by philinux on 2009-11-17
> **nerdy_kid said:**
> try deleting xorg.conf?  i tryed upgrading my NVIDIA drivers and the third boot up i did i couldnt startx....said no screens found.  deleted xorg.conf-- i was able to log in to fix stuff better.

+1 that should do the trick. There's probably some left over stuf that conflicts in karmic. At the command prompt ```
rm /etc/X11/xorg.conf
```

Then reboot.

---

### Post by ublintu on 2009-11-17
Thank you for the reply!
I followed the suggestion, to remove xorg.conf, but it isn`t there. I don`t have it:
ublintu@ublintu-laptop:~$ rm /etc/X11/xorg.conf
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory

(My card is not NVIDIA. I have ati 200m (I don`t know it`s depend on it))

X11 folder contains this files and folders: (attached)

---

### Post by ublintu on 2009-11-17
I just installed karmic in virtualbox and it`s happened in virtualbox as well, but at shut down and it`s happened just for 4 sec (like at boot time... tty1). After 4 sec, ubuntu shut down normally.
ok it`s not the same....

---

### Post by nerdy_kid on 2009-11-18
do you have the ATI drivers installed?
does X ever start with 'startx' or does it always give the error 'no screens found'?

try ```

sudo dexconf

```


id remove xorg-driver-fglx and any ati drivers you have ( i dont think there are any more unless you downloaded from ATI), then run dexconf.


By ATI 200m i assume Radeon 200m?
if so i feel very deeply for you... i have a pc with the same card -- it is a NIGHTMARE!

---

### Post by ublintu on 2009-11-18
Hi nerdy_kid,

To install ati driver, I followed this guide, until "configuring x.org" [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I get online just now, so I will try soon your suggestion: sudo dexconf

You have right, nightmare. Ati 200m wasn't a good choice. Did you install your ati driver like me, like in this guide?

Edit: why did you use this command sudo dexconf &#8211; reset xorg.conf configuration. I could not find xorg.conf!
edit2: Yes, X ever start with 'startx', no error
edit3: I used sudo dexconf and after reboot, it`s behave like usual. I didn`t get tty1 on my screen this time, but I need to try a few more time to make shure, because it`s happen randomly.
edit4: I realize just now: I don`t have sound now!!!

---

### Post by nerdy_kid on 2009-11-18
ok, that sounds good.  I use the same drivers, but they wont let me play games.

do you use KDE?  i think kdm has an issue like this
to fix my issue i did

```

sudo -i
cp /usr/bin/kdm /bin/kdm
cp /usr/bin/kdm /usr/sbin/kdm
cp /usr/bin/kdm /sbin/kdm

```
kinda tacky but it worked for me :D

---

### Post by ublintu on 2009-11-18
and after when you did sudo dexconf, did you have sound. I don`t have any now. It`s sound bad :)

---

### Post by ublintu on 2009-11-18
No, I`m not using KDE.

edit: reinstalled pulseaudio and now I have sound.

---

### Post by diablokicks on 2009-11-18
I am also having the same problem, however i am EXTREEMLY new to ubuntu, im doing a dual boot with xp as my host.   I have no idea what to do to take care of this problem.  Even when i go to the recovery section and try to do a normal boot there, the login/pass doesn't flash, but i still cannot log in?  Any suggestions?

---

### Post by ublintu on 2009-11-19
Hi diablokicks, 
welcome in the forum. At the moment it`s looks like nobody knows whats the problem, but be patient. We are not alone with this, because I fond a few other topics, which are talking about this.

---

### Post by chefster on 2009-11-19
Hey im a recently new user too and just upgrated from 9.04 - 9.10 and have the same crash and now flashing log in screen. Any help will be greatly appreciated 

Thanks!

---

### Post by blueridgedog on 2009-11-19
> **ublintu said:**
> Thank you for the reply!
I followed the suggestion, to remove xorg.conf, but it isn`t there. I don`t have it:
ublintu@ublintu-laptop:~$ rm /etc/X11/xorg.conf
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory


The command assumes you are booted on your system, not a LiveCD.  If you are booted on a LiveCD, you will need to mount your internal hard drive, then delete the file.  Did you run the command from your system or a LiveCD session?

If you need help deleting the file from a LiveCD session, post the output of 

```
mount
```

and 
```

sudo fdisk -l
```

These will show where your hard drive is mounted.

---

### Post by ublintu on 2009-11-19
No, I`m not using liveCD, I booted in the system.
ublintu@ublintu-laptop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ublintu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ublintu)
ublintu@ublintu-laptop:~$ sudo fdisk -l
[sudo] password for ublintu: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16        4480    35865112+   7  HPFS/NTFS
/dev/sda3            4481       14593    81232672+   5  Extended
/dev/sda5            4481       14176    77883088+  83  Linux
/dev/sda6           14177       14593     3349521   82  Linux swap / Solaris


I`m thinking to reinstall ubuntu...

---

### Post by sabre2th on 2009-11-19
I don't have a solution offhand, but I thought I'd share my experience.  Maybe the info will help someone else fix it...

I had this happen with a clean install of Karmic on my Mythbuntu machine.  It would flash as described and (as far as I could tell) would not accept any input from the keyboard after a few seconds.

I later backed up my old Jaunty partition and upgraded it instead.  This has worked fine so far, though I don't restart or play with it much, considering it's basically an appliance.  Why it worked with an upgrade and not a clean install, I'm not sure.  My initial thought was perhaps an X config issue, but I didn't bother playing with it.

---

### Post by poudigne on 2009-11-20
Got the same probleme after installing a mp3 player. I'm about to try an update and will post de result... i hope i won't loose anything
 
edit1: well.. i didn't found how to reinstall Ubuntu 9.10 without losing personnal files. so i'm reinstalling a clean install. hope for others that someone will find something to fix this bug

---

### Post by ublintu on 2009-11-20
I reinstalled ubuntu 9.10 today and still the same. Sometimes I still can get "tty1 screen"
Something else is the problem...?

Maybe the graphic driver.? What kin of graphic card do you have? 
I have ati 200m.
Is it possible, that something is conflict with it, something unnecessary thing is still here?

---

### Post by quantum8 on 2009-11-20
I had this computer switched off for a week and am now encountering this issue too.

I managed to get into recovery mode and ran an apt-get upgrade (which didn't fix the problem), and now I can't even get past the recovery menu to resume the normal boot :(

I hope this gets resolved soon as it's a major issue!

---

### Post by trampas on 2009-11-25
I did an upgrade from 9.04 and got the flashing tty1 screen, the keyboard seems to only accept every 1 out of 4 key types thus I can not login. Did a clean install of 9.10 to get around issue. 
Just did the update and I am back at the flashing tty1: login with no way to login. 
Basically 9.10 SUCKS so bad I am thinking of switching to Fedora...

Trampas

---

### Post by alexironaek on 2009-11-25
well , i encounter the same problem yesterday after an update but i fixed it today , what i did is that i deleted the xorg.conf file BUT to delete it i had to enter ./X11 NOT /X11 because X11 is a hidden file that's why for some people is says that there is no such file! , after that it booted normally but after i installed the drivers through "hardware drivers" the same thing happened again so i deleted the xorg.conf again and then i downloaded my card's driver from nvidia's site and installed it and everything is working perfectly again , at least that is how it worked on me i hope it will work on someone else too :)

---

### Post by mscomms on 2009-11-25
I have just removed the /etc/X11/xorg.conf and can now get into my system but doing this seems to have disbled the nvidia drivers I will tyy a reinstall and see how it goes

---

### Post by mscomms on 2009-11-25
OK what happened next
Booted OK, 
logged in OK,
Second screen scrambled 
ran Systen-Administration - NVIDIA X Server Settings
I get a messagebox "You do not appear to be using the NVIDIA X driver. Please edit your X configuration filr (just run `nvidia-xconfig' as root, and restart server"
from the console ran sudo nvidia-xconfig which gave the following output

WARNING:    Unable to locate/open X configuration file.

New X configuration file written to `/etc/X11/xorg.conf'

restarted X server with sudo /etc/init.d/gdm restart

Back the the flashing login prompt.

I will remove the xorg.conf again and try a different set of drivers

---

### Post by sdowney717 on 2009-11-25
the program nvidia-settings can be a pain.

you must run after you install nvidia driver from terminal 
nvidia-xconfig

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-03.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-03.html)

Then you can run from the menu nvidia-settings.
However, when i do this i select the preview after hitting the apply. And I select all and copy the settings. 
Then i manually open xorg.conf
gksu gedit /etc/X11/xorg.conf and paste it in. Dont use the merge option

every time I would try to save to xorg.conf, nvidia settings will die. I assume it is because i am not running it like this 'gksu nvidia-settings'

here is my xorg
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@nannyberry)  Sat Sep  5 21:13:00 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-E540"
    HorizSync       30.0 - 110.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    Option         "TVStandard" "NTSC-M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: 1600x1200 +0+0, TV: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



---

### Post by mscomms on 2009-11-25
tried installing [B][Linux Display Driver Version 96.43.14]("http://www.nvidia.co.uk/object/linux_display_ia32_96.43.14_uk.html") [IMG]http://www.nvidia.co.uk/content/DriverDownload/includes/images/us/recommended.jpg[/IMG] direct from the nvidia site and still no go, this time you get the initial ubuntu splash screen the a blank screen, removing xorg.conf doesnt fix it you have to uninstall.

sdowney717 cheers i'll try that
[/B]

---

### Post by Frogging101 on 2009-11-25
Computers can sometimes have really weird problems. Try unplugging the computer (Desktop), and plugging it back in. For laptops, take out the battery, and put it back in. This may work, and it may not. It's worth a try.

---

### Post by MehdizLinux on 2009-11-25
Same Problem. It happened after update. All of us, who faced this issue,  have lost our OS so easy? that's it?!

---

### Post by quantum8 on 2009-11-25
I ended up booting from the install dvd, deleting /etc/X11/xorg.conf and rebooting.

I then had to re-install the nvidia driver from the hardware drivers control panel. It's been working for me since then.

---

### Post by ublintu on 2009-11-25
I thought it isn`t relevant to the drivers, because everyone has different one (ati, nvidia) and installed it a different way. Maybe the xorg.conf, if someone has it...

Or maybe it`s relevant to the kernel, because I started to have this problem, just after an update.  It updated a lots of things and kernel as well.

More and more people have this problem...

---

### Post by dmoy on 2009-11-25
Same problem.  The only things I did differently last time I shut down (as in the last time before this problem started manifesting) was a set of updates from the update-manager (haven't grabbed the names yet) and shutting down via sudo shutdown instead of the GUI way.  It also might be worth mentioning that the computer locked up during this shutdown process...  Also:  [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

---

### Post by Astrogeek on 2009-11-25
I had this same issue with a GeForce 7800GS and was forced to do a couple of clean installs. Every once in a while I could get a clean login by ctr+alt+F4 which happened to give me a non-blinking login. Not that this helped any because the Nvidia drivers I had downloaded from Nvidia (185.18.14 and 190.42) would both throw errors when trying to compile for the kernel. Eventually I viewed the error log in /var and found that I had an issue with my BIOS settings. I fixed the AGP aperture (my machine is mostly hand-me-down) and the default video card (PCI to AGP) and it booted up fine with the 185 driver. Not sure if this will help anybody else but if you've got old gear like me it might be worth a shot to check your BIOS just in case.

---

### Post by dmoy on 2009-11-25
Of note for the following solution: I'm running x86_64, with an NVIDIA card

I solved the problem by doing the following:

NOTE: Can skip steps 1-2 if you already have a copy of the latest NVIDIA driver from nvidia.com (or if you're a dumbass like me, you can do 1-2 and then realize that you already had a copy)
1. start up in recov mode, go to a root shell w/ network
2. wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg2.run) (CHECK THIS URL, I might have typed it in wrong) (If you're not using x64, get a different driver, obv.)
3. telinit 3
4. log back in
5. sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run
6. Follow steps
7. Restart
8. Done.
9. Cross your fingers that it doesn't reappear (it might :\)

---

### Post by mscomms on 2009-11-26
If you have a fixed rather than DHCP ip address use the root rather than netroot and your network connection will work

---

### Post by mscomms on 2009-11-26
sdowney717 how are you getting the preview I don't get that option, what version driver are you using

---

### Post by trampas on 2009-11-26
My problem was that I could not login due to flashing screen (assume starting and failing X). Finally I gave up and installed a Windows 7 on a new hard drive, it is very refreshing to install an OS and everything works! Note I tried Fedora 12 and it has the same suspend issues (will not suspend with SD card in laptop). Also Gnome login on Fedora and Ubuntu has issues after resume (usually have to type password twice). 

So I needed to get the data off my Ubuntu install, finally I found that pressing the Alt+SysRq(prtsc)+i stopped the flashing and allowed me to login such that I could reinstall Nvidia. 

I will let time see which OS wins from here on out. I like Linux but I am getting tired of hacking it every time their is an update. 

Trampas

---

### Post by MehdizLinux on 2009-11-27
Here we see why that guy is the richest! It's two weeks I'm using Ubuntu. Almost nothing works in a normal way. And at last I lost it with the same problem.
You just need to pay $250+$50 for AV and just think twice when you plug your USB drive. Otherwise everything works great and easy. 
I'm a newbie in Linux and it look a mess to me. Correct me if I'm wrong.

---

### Post by MehdizLinux on 2009-11-28
> My problem was that I could not login due to flashing screen (assume starting and failing X).

Did you try "dmoy's" steps? It worked for me, 

Thanks for that.

---

### Post by krige on 2010-02-03
I had the same problem after a fresh install of Ubuntu 9.10, on the first boot.

I couldn't login because the flashing was interfering with the key strokes and not all of them were captured.

So I rebooted from the installation disk, opened a terminal, became root and deleted the /etc/X11/xorg.conf file.

The system booted normally on the next boot.

---

