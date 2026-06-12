---
title: "DKMS part of installation failed.  ati driver issue after update."
date: 2010-09-29
forum: General Help
---

### Post by noveevon on 2010-09-29
here is the message i get when i try to install any proprietary ati driver:

> DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details

it all started after i had a major update today a few hours ago.. ever since then ive been trying to install every possible driver ive found, but i always get that error..

the last good driver that ive been using is the 10.6 and that worked great...

the reason i am using propitiatory and not the open source is because i rely on the  > aticonfig --pplib-cmd "set fanspeed 0 25"
 command to make my ati 4850HD more silent as without the command i can simply not use my card due to its extreme noise..

any help would be great...and yes ive been looking for other thread about this problem but i cant find any that works for me..

---

### Post by IvoP123 on 2010-09-29
> **noveevon said:**
> here is the message i get when i try to install any proprietary ati driver:



it all started after i had a major update today a few hours ago.. ever since then ive been trying to install every possible driver ive found, but i always get that error..

the last good driver that ive been using is the 10.6 and that worked great...

the reason i am using propitiatory and not the open source is because i rely on the   command to make my ati 4850HD more silent as without the command i can simply not use my card due to its extreme noise..

any help would be great...and yes ive been looking for other thread about this problem but i cant find any that works for me..

i have same problem...

---

### Post by noveevon on 2010-09-29
ok, ive been thinking and i will try this:

**[How to Undo an Update in Ubuntu Lucid]("http://hartmansblog.blogspot.com/2010/06/how-to-undo-and-update-in-ubuntu-lucid.html")**



i found these as todays updates:

> Commit Log for Wed Sep 29 17:05:52 2010


Upgraded the following packages:
cheese (2.30.1-0ubuntu1) to 2.30.1-0ubuntu2
cheese-common (2.30.1-0ubuntu1) to 2.30.1-0ubuntu2
gnome-terminal (2.29.6-0ubuntu5) to 2.30.2-0ubuntu1
gnome-terminal-data (2.29.6-0ubuntu5) to 2.30.2-0ubuntu1
google-chrome-stable (6.0.472.62-r59676) to 6.0.472.63-r59945
libcheese-gtk18 (2.30.1-0ubuntu1) to 2.30.1-0ubuntu2
libphonon4 (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-assistant (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-core (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-dbus (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-designer (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-gui (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-help (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-network (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-opengl (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-qt3support (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-script (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-scripttools (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-sql (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-sql-mysql (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-sql-sqlite (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-svg (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-test (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-webkit (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-xml (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqt4-xmlpatterns (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqtcore4 (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
libqtgui4 (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
linux-generic (2.6.32.24.25) to 2.6.32.25.27
linux-headers-generic (2.6.32.24.25) to 2.6.32.25.27
linux-image-generic (2.6.32.24.25) to 2.6.32.25.27
linux-libc-dev (2.6.32-24.43) to 2.6.32-25.44
phonon (4:4.6.2-0ubuntu5) to 4:4.6.2-0ubuntu5.1
python-software-properties (0.75.10) to 0.75.10.1
software-properties-gtk (0.75.10) to 0.75.10.1
software-properties-kde (0.75.10) to 0.75.10.1

Installed the following packages:
linux-headers-2.6.32-25 (2.6.32-25.44)
linux-headers-2.6.32-25-generic (2.6.32-25.44)
linux-image-2.6.32-25-generic (2.6.32-25.44)


so now i just have to find out which could be responsible..

---

### Post by IvoP123 on 2010-09-29
> **noveevon said:**
> ok, ive been thinking and i will try this:

**[How to Undo an Update in Ubuntu Lucid]("http://hartmansblog.blogspot.com/2010/06/how-to-undo-and-update-in-ubuntu-lucid.html")**



i found these as todays updates:



so now i just have to find out which could be responsible..

i believe this is caused by kernel update (at least in my case)

---

### Post by noveevon on 2010-09-29
> **IvoP123 said:**
> i believe this is caused by kernel update (at least in my case)


did you try to revert to an older ones/ roll back the update?

---

### Post by IvoP123 on 2010-09-29
> **noveevon said:**
> did you try to revert to an older ones/ roll back the update?

i tried to find out how to solve this on new kernel. didn't really try to revert to older one (which i believe is complicated, but i'm noob so...).

---

### Post by noveevon on 2010-09-29
> **IvoP123 said:**
> i tried to find out how to solve this on new kernel. didn't really try to revert to older one (which i believe is complicated, but i'm noob so...).


yeah im pretty noob myself..hoping there will be a new update by this time tomorrow which will fix it, if not i am hoping one of the veterans here will try and helps us..

seems there are allot of problems with ATI drivers and updates...

now if only i could find another way to control my GPU fan speed i would gladly just use some open source drivers instead of these problem filled ones...

---

### Post by IvoP123 on 2010-09-29
> **noveevon said:**
> yeah im pretty noob myself..hoping there will be a new update by this time tomorrow which will fix it, if not i am hoping one of the veterans here will try and helps us..

seems there are allot of problems with ATI drivers and updates...

now if only i could find another way to control my GPU fan speed i would gladly just use some open source drivers instead of these problem filled ones...

i hope so too... everything seems to run smoother with catalyst drivers. this is the reason why i use them...

---

### Post by dreiche2 on 2010-09-29
Same problem here.

I'm on 9.10.

Rebooting after some updates today threw me into "low-graphics mode". After playing around for a while I now made it back into normal mode, but when I try to install the ATI drivers, I get the same error. 

Help would be highly appreciated!

---

### Post by Botruckle on 2010-09-29
I was doing fine with the Catalyst 10.7 driver, then with tonight's update of Ubuntu, it complained about the video driver. I updated to the 10.9, but no real change. The update borked the video drivers, but not sure why. I tried reverting to 10.7, but again no joy. I'm on 64bit Ubuntu, ATI HD5850.

UPDATE: This ATI hotfix cured it for me: [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

---

### Post by dodjob on 2010-09-30
Thanks a lot Botruckle for the fix it worked also for me :-D
++

---

### Post by noveevon on 2010-09-30
> **Botruckle said:**
> I was doing fine with the Catalyst 10.7 driver, then with tonight's update of Ubuntu, it complained about the video driver. I updated to the 10.9, but no real change. The update borked the video drivers, but not sure why. I tried reverting to 10.7, but again no joy. I'm on 64bit Ubuntu, ATI HD5850.

UPDATE: This ATI hotfix cured it for me: [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)


hi,

thanx it helped me get my fan back to liveable noise levels, but now i cannot put my screen resolution higher then 1400 X 1050, plus i cannot see multiple screens.. do i need to re install the 10.9 driver? as the hot fix was just a small update right? but ofcourse i cannot install the 10.9 driver without the hot fix cause it will not install.

---

### Post by IvoP123 on 2010-09-30
> **Botruckle said:**
> I was doing fine with the Catalyst 10.7 driver, then with tonight's update of Ubuntu, it complained about the video driver. I updated to the 10.9, but no real change. The update borked the video drivers, but not sure why. I tried reverting to 10.7, but again no joy. I'm on 64bit Ubuntu, ATI HD5850.

UPDATE: This ATI hotfix cured it for me: [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

Thanks man. Will try it ;)

anyone got this error 

Error in MD5 checksums: b143f238219708d7a2f6ed02df04c3a3 is different from 91758a92b8610526ed13f4937fa9f853

when running .run file?

Solved it by unzipping file through terminal. Everything seems to be fine now. Thanks Botruckle!

---

### Post by dreiche2 on 2010-09-30
Fixed it for me as well. Thanks.

---

### Post by goodolandy on 2010-09-30
That happened to me as well but what I did was go to the package manager and reinstalled fglrx then when I went back in to hardware device I was able to activate the ATI driver no problem.

---

### Post by noveevon on 2010-09-30
think i fixed the resolution with this:

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Wrong%20resolutions,%20refresh%20rates,%20or%20monitor%20specs](https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Wrong%20resolutions,%20refresh%20rates,%20or%20monitor%20specs)


i used the xrandr commands to fix both of my two screen to the right values:) so i will now mark this thread solved..

---

### Post by cocamoxb on 2010-10-04
Thank you, Botruckle. This fix resolved my issue as well. Most appreciated.

---

### Post by darthcharly on 2010-10-05
Thanks a lot Botruckle. This fix resolved my issue too:P

---

### Post by misse- on 2010-10-10
Yeah, thanks botruckle. I found this thread and was able to get my fglrx back on.. However, ATI catalyst control center tells me that I'm still running 10.7 :(

I've installed the hotfix and rebooted.. should I try the original driver again, even though the DKMS is still failing? Any advice would be appreciated.

---

