---
title: "Playing DVD's in Ubuntu 9.10 64-bit"
date: 2010-01-12
forum: General Help
---

### Post by lukster91 on 2010-01-12
Hey all,

I'm running Ubuntu 9.10 64bit version. I'm trying to get a DVD to play. Yet no media players that I have on here will work. 

I've tried all the codes in the terminal that I have found online to get this working... Here are the codes I have put in and their respective responses: 

**sudo apt-get install debhelper build-essential fakeroot**
 - Installed

**sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine mencoder**
 - luke@Luke-Ubuntu:~$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine mencoder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

**sudo apt-get install libdvdread3**
 - luke@Luke-Ubuntu:~$ sudo apt-get install libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdread3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread3 has no installation candidate

**sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine mencoder**
 - luke@Luke-Ubuntu:~$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine mencoder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

**sudo /usr/share/doc/libdvdread3/install-css.sh**
 - luke@Luke-Ubuntu:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found


Any idea how I can sort this and get my DVD playing?

Thanks.

---

### Post by Puck7 on 2010-01-12
Have you tried VLC?

```
sudo apt-get install vlc
```

---

### Post by Woody1987 on 2010-01-12
You need to add the medibuntu repository [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

run this in a terminal:
> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Then install the packages you want.

---

### Post by lukster91 on 2010-01-12
> **Woody1987 said:**
> You need to add the medibuntu repository [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

run this in a terminal:


Then install the packages you want.

Thanks. I've installed them, I was able to install the libdvdcss2. But I still can't install the others. I'm getting these messages:

luke@Luke-Ubuntu:~$ sudo apt-get install libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdread3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread3 has no installation candidate
luke@Luke-Ubuntu:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found

---

### Post by Woody1987 on 2010-01-12
I have libdvdread4 installed, libdvdread3 is not available to me on karmic. Try that instead.

---

### Post by howefield on 2010-01-12
libdvdread3 isn't available in Karmic, try libdvdread4

[http://packages.ubuntu.com/karmic/libdvdread4](http://packages.ubuntu.com/karmic/libdvdread4)

---

### Post by lukster91 on 2010-01-12
Very odd, just tried to install it. It's already there. 

When I try and play the DVD, the program closes (whether it's VLC or media player), and right now I can't eject the DVD from the tray.

Still won't play though.

---

### Post by Woody1987 on 2010-01-12
try installing ubuntu-restricted-extras if you havent already, it installs codecs and some other stuff.

---

### Post by lukster91 on 2010-01-12
It's already installed...

---

### Post by Woody1987 on 2010-01-12
When in doubt, reboot, cross fingers and try playing the dvd again.

---

### Post by lukster91 on 2010-01-12
Thanks, will try. Loaded into my Windows Partition now as I'm sick of waiting to watch this movie! If I find the solution, I will post it on here.

---

### Post by howefield on 2010-01-12
Just a thought, how are you trying to play the dvd ?

eg, if it is vlc you are using, select Media > Open Disc.

---

### Post by efflandt on 2010-01-12
It seems like you are going about it the hard way.

I usually install ubuntu-restricted-extras, and what the Synaptic description for that (link) says is needed for DVD's.  I completely uninstall flashplugin-installer (which is actually 32-bit flash with a wrapper) and install real 64-bit flash.  And for DVD playing, I install vlc.

For some reason I have never been able to get totem (Movie Player) to work properly for DVD's (32 or 64-bit systems).  Either DVD menus work, but I get no sound, or sound works and DVD menus do not (so I get no farther than opening splash screen).  Sound works fine for everything else.

But vlc works better for DVD anyways, since it is proper aspect ratio on various screens (totem was not proper aspect ratio on my 1280x800 laptop no matter what I tried).

---

### Post by techstop on 2010-01-12
> **efflandt said:**
> It seems like you are going about it the hard way.

Damn straight!

The simple thing to do would be to go to the Multimedia and Video section of the forum and read the "Comprehensive Howto" sticky.

In summary, after enabling medibuntu and doing an apt-get update and apt-get upgrade, run this in a terminal (this is for 64-bit ubuntu);

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar

```

Then run this in a terminal for DVD support;

```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlc
```

There's a troubleshooting section at the end of the sticky if you're still having troubles;

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by lukster91 on 2010-01-12
> **techstop said:**
> Damn straight!

The simple thing to do would be to go to the Multimedia and Video section of the forum and read the "Comprehensive Howto" sticky.

In summary, after enabling medibuntu and doing an apt-get update and apt-get upgrade, run this in a terminal (this is for 64-bit ubuntu);

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar

```

Then run this in a terminal for DVD support;

```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlc
```

There's a troubleshooting section at the end of the sticky if you're still having troubles;

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Fantastic. This works brilliantly. Menu, sound, everything.

Thanks.

---

### Post by techstop on 2010-01-12
> **lukster91 said:**
> Fantastic. This works brilliantly. Menu, sound, everything.

Thanks.

No worries at all! :biggrin:

---

### Post by lukster91 on 2010-01-12
Still can't eject the disk drive though. Any thoughts on that?

---

### Post by hawthornso23 on 2010-01-12
> **lukster91 said:**
> Still can't eject the disk drive though. Any thoughts on that?

Are you talking about failure to respond when you click eject in the media player, or are you  unable to eject the disk at all (not even when you hit the eject button on the case). This sounds like a more hardware specific issue to me, so you probably need to tell us what you are using.

---

### Post by lukster91 on 2010-01-12
> **hawthornso23 said:**
> Are you talking about failure to respond when you click eject in the media player, or are you  unable to eject the disk at all (not even when you hit the eject button on the case). This sounds like a more hardware specific issue to me, so you probably need to tell us what you are using.

Sorry, I was a bit inspecific.

I am able to eject the disk fine with: 

> eject -T /dev/cdrom

Issue is, I can't eject it using the button on the disk tray, or in the player. I think the computer is under the assumption the disk is in use when it isn't. So it's a software issue...

---

### Post by HeadHunter00 on 2010-01-12
Don't worry about ejecting it "safely." If you mean that you can't get the DVD out, then I guess you're outta luck. BTW, what's your computer model, "luckster"?

---

### Post by lukster91 on 2010-01-12
Well, other than my fancy bit of code there, I assume there is a work around.

---

### Post by hawthornso23 on 2010-01-12
Wotcher got in /etc/fstab . Lets see how the thing is being mounted.

---

### Post by hawthornso23 on 2010-01-12
I've just checked and mine doesn't respond to the button on the case either. I eject by right clicking the disk icon on the desktop and selecting `eject'. Does this work for you?

---

### Post by lukster91 on 2010-01-12
> **hawthornso23 said:**
> Wotcher got in /etc/fstab . Lets see how the thing is being mounted.

DVD isn't in there at the moment. That make a difference?

---

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=eb522d1c-7688-45ee-ad9a-ad573b4c722e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=18aa1956-3d34-43f0-ba87-39375a1c4ad5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by lukster91 on 2010-01-12
> **hawthornso23 said:**
> I've just checked and mine doesn't respond to the button on the case either. I eject by right clicking the disk icon on the desktop and selecting `eject'. Does this work for you?

Don't have eject. I have "Unmount" though, then ejecting it works fine.

---

### Post by hawthornso23 on 2010-01-12
Here is yours

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Here is mine

/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec,utf8 0       0

Notice the difference? It is subtle. 

Mine says `users' while yours says 'user'.  I remember now making this change a while back. 

With `user' only the person who mounts the file system can umount it. So if your wife leaves a DVD in the player and logs out, you won't be able to eject it at all without a huge hassle. 

With 'users' anyone can mount or umount. 

Not sure if this is related to your problem, but it is a change I'd recommend you make.

---

### Post by lukster91 on 2010-01-12
> **hawthornso23 said:**
> Here is yours

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Here is mine

/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec,utf8 0       0

Notice the difference? It is subtle. 

Mine says `users' while yours says 'user'.  I remember now making this change a while back. 

With `user' only the person who mounts the file system can umount it. So if your wife leaves a DVD in the player and logs out, you won't be able to eject it at all without a huge hassle. 

With 'users' anyone can mount or umount. 

Not sure if this is related to your problem, but it is a change I'd recommend you make.

Not quite related, but thanks. I will make the change!

---

### Post by Tourdog on 2010-01-13
Techstop,
Nice work there because it worked for me too!

I have dvds crystal clear plus outstanding audio from Totem and VLC.

Thanks again! :D

---

### Post by Tourdog on 2010-01-13
I want to amplify the previous post:

Here are the steps that finally worked for me:

1.
> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
2.
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar

3.
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlc


I did not run the 3rd sudo because those files were already showing installed using Synaptic. ( VLC media player had been installed basically to check against Totem.)

Both Totem and VLC would scramble, then lose (crash) within a minute upon playing a paid-for DVD.   I went ahead and ran the 3 rd sudo and "voila"!  (Ran, meaning right over the top of the same files)

Both Totem and VLC now play beautifully any DVD that we have.  Video and sound have no shortcomings.   Perfect!

So far I only see a long wait for BBC and downloads therein but YouTube is very fast considering our 2.4 gighertz wireless connect to a rural tower some 2 1/2 miles away plus my in house wifi (g) for broadband.  This ISP can bog down to 1 mbit/s thru-put but normally is from 3 to 5 mbits/s with 30 m/s latency.

The first 2 sudos are available on the  "MultiMedia & Video".................. (sticky) of this forum plus many postings (this thread).

Now for some reason I cannot find the "button" on either Totem or VLC to "eject" the DVD?!   (Greyed out)

Thanks to all who have helped out  :D

---

