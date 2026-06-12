---
title: "LiveCD Resolution"
date: 2005-02-04
forum: General Help
---

### Post by JohnC on 2005-02-04
Can someone please explain for a complete Noobie how to make the liveCD boot in lower resolutions?  I think the problem is that I have a PC with a video card capable of producing resolutions higher than the monitor can display (don't we all?)  So after the text portion of booting it goes to switch into another mode and I see my monitor complain that the resolution is out of range...  I even tried failsafe boot and it didn't seem to help.  Maybe the liveCD shoud ASK before it attempts to use a particular resolution.  Anyway can someone point me to a resource or explain it to me from beginning to end?

Thanks!!!  I can't wait to try it!

---

### Post by supergrapeman on 2005-02-05
The latest hoary livecd definitely asks you about the resolutions to use..

---

### Post by menu on 2005-02-06
[QUOTE=supergrapeman]The latest hoary livecd definitely asks you about the resolutions to use..[/QUOTE]

This depends, 
-On both of my imacs  (ati) it did not (it wont start x on those)
-On my G4/400 ati8500 it did not (it locks x resolution to 640x480
-on  a friends Dual g4 (nvidia) it did ask (but it did not tell you to push space to select a resolution) then ignored the selection and went 640x480 on me

So if there is simple  way to select resolution at ppc lifecd boot, please tell me!
I tried the knoppix startup tips as in [this](http://www.ubuntuforums.org/showpost.php?p=57526&postcount=3)   thread, they did not work for me

---

### Post by mikearagua on 2005-02-17
i've also had the problem that when i boot the live cd (onto my ibook g3 700mhz) it only gives me 640x480 and I couldn't see how to change this situation.  I love Ubuntu though, the screen resolution is the only annoying thing about the live cd.  My hard drive recently died and it's one of the only ways that machine is currently useable.  Maybe there is something I'm overlooking.

---

### Post by Demon on 2005-02-18
I also am having this problem and I cant change the refresh rate either.

---

### Post by loninappleton on 2005-02-18
Also having the problem.  With these demo things I'm
unsure as to know how to even get to the terminal screen.

A 640/400 rez doesn't even show the panel.


My Fedora setup does not have this problemo.

---

### Post by akeech on 2005-02-20
I downloaded warty live cd last week and had the same problem. "out of range" message from my flat panel monitor. I've since got the live CD working, tried it, loved it and installed it.

Initially I thought I was a genius and had had fixed this by playing around with the boot options but I just got home and tried the live CD again and realised that on my system warty boots into gnome even if i dont put in any boot options!

I still got the out of range error on my LCD syncmaster monitor but when gnome started everything was OK but just like woth the install CD there  was a poor selection of screen resolutions to choose from.

To fix the limited choice of screen resolutions run this command (as root i think)

# dpkg-reconfigure xserver-xfree86

I found this tip here:

[http://www.linuxquestions.org/questions/history/283737](http://www.linuxquestions.org/questions/history/283737)

---

### Post by RobF on 2005-02-20
akeech writes:

"To fix the limited choice of screen resolutions run this command (as root i think)
# dpkg-reconfigure xserver-xfree86"

This doesn't work for the Hoary v. 5.04 Live CD, booted as a live CD (I'm not talking about Ubuntu installed from it on a hard disk, as I suspect akeech does).  E.g.

root@ubuntu:/home/ubuntu # dpkg-reconfigure xserver-xfree86
Package `xserver-xfree86' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xfree86 is not installed
root@ubuntu:/home/ubuntu #

I've had the same experience as several other people in this thread: the Hoary Live CD boots into a low resolution Gnome desktop (in my case 800x600, with hsynch 32 kHz and vsynch 50 Hz, with a lot of flicker), and the only options available under Desktop > Administration > Screen Resolution are 800x600 and 640x480.  There don't appear to be any options for screen resolution that can be set at boot time (i.e. similar to the Knoppix cheatcodes).

supergrapeman wrote:
"The latest hoary livecd definitely asks you about the resolutions to use.."

Only once or twice in more than a dozen attempts to boot the live CD - with endless fiddling of parameters - did I see a screen that listed some 15 or so screen resolutions and asked something like "mark all the resolutions you don't want", with the lowest three (640x480, 800x600, 1024x768 ) already being marked.  I put the cursor on 1024x768 and hit <enter>, thinking this would unmark it (I should have used the space bar - why don't they say so?), and that's the last time I saw that options screen.

I think the Ubuntu live CD's are poorly put together (this also applies to the Warty live CD with which I had the same problems, it booted into a 640x480 screen), and I've just about given up on Ubuntu as a Linux distro worth checking out.  I never had these problems with two dozen other live CD's I've checked out.

Also see:
[http://www.ubuntuforums.org/showthread.php?t=15927](http://www.ubuntuforums.org/showthread.php?t=15927)

Robert

---

### Post by akeech on 2005-02-21
OK. Thats true. I did not try this on the live CD.

It may still provide a clue though as I had the same problems on the LIVE CD and the HD Install. I had limited resolution options available within the gnome menu

This command fixed the gnome menus to include the correct resolutions for my monitor.

---

### Post by scramblejams on 2005-04-15
[QUOTE=RobF]akeech writes:

"To fix the limited choice of screen resolutions run this command (as root i think)
# dpkg-reconfigure xserver-xfree86"

This doesn't work for the Hoary v. 5.04 Live CD, booted as a live CD (I'm not talking about Ubuntu installed from it on a hard disk, as I suspect akeech does).[/QUOTE]
It will work from the LiveCD -- the problem is that Ubuntu doesn't use XFree86, it uses Xorg. So what you want to do is:

# dpkg-reconfigure xserver-xorg

However, I'm not sure that'll help anyway. My iBook is locked at 640x480, and it didn't go to native resolution until I manually edited /etc/X11/xorg.conf's "Monitor" section to include the horizontal and vertical refresh frequencies for my chipset.

---

### Post by tiamet on 2005-09-23
I am a newbie but decided to give the "live" 5.04 disk a try.  Everything went fine until the final screen.  The resolution was so high that we could barely make out the icons or the pointer and the pointer was highly erratic (probable due to hi res) I have an NVIDIA GeForce2 MX/MX 400 card and a GATEWAY EV900 [Monitor] (17.7"vis, September 1997).
Please understand that I am not up to getting into the bios or other similar levels.
Is there a simple way to fix this?
Thanks

---

