---
title: "itunes, virtualbox and rhythmbox problem"
date: 2010-10-15
forum: General Help
---

### Post by ives31 on 2010-10-15
Ok, I've been trying for several days to find an alternative to booting into windows to for the sole purpose of using itunes.

First thing was I tried using rhythmbox to sync my iphone. Apart from not being able to install apps and the problem of subscribing to some podcasts. I found that adding and removing music was very hit and miss. Sometimes it would work, othertimes it wouldn't for no apparent reason. Same thing with syncing the iphone. Sometimes worked, sometimes wouldnt.
In the end I got sick of spending hours trying to move music from the phone to the hdd and back.

Ok, next I tried virtualbox cos I read you can install windows and run itunes. Great I thought. Installed W7 in Virtualbox and installed itunes. Fine. However, I found that my phone wouldn't show up in itunes. Then I found that USB is not supported in virtualbox unless you get the paid for version, which I can't find. WTF!. How are you supposed to use the iphone with virtualbox without a usb connection?

Is there an easy way to sync your iphone without having to dual boot into windows?

thanks,
ives

using ubuntu 10.10

---

### Post by JHurrell on 2010-10-20
Bump...

I've been researching this as well and so far haven't found a good solution. I'm using 10.10 and have an iPhone 3G with OS4.1 on it. I blew away my Windows 7 partition recently so I could commit fully to Ubuntu assuming that what I'd read about Banshee support my desire to continue using my iPhone.

No love so far. From Banshee, I can drag some Podcasts and Audiobooks to the iPhone, but they show up as music. Not really what I'd wanted.

Despite how horrible iTunes is, it does let me get content to my iPhone in a manner that makes sense.

I'm considering keeping my second machine around and using only for iTunes and other lame Windows apps.

- John

---

### Post by ives31 on 2010-10-20
I found a soloution that works ok.
I installed win XP (instead of Win 7 ) on virtual box and an older version of itunes: 8.2

Win xp is a lot faster and more responsive than 7 and itunes works pretty well.
So far, no problems at all.

---

### Post by DiNozzo92 on 2010-10-27
Are you still using the free virtual box or did you buy it?

---

### Post by ives31 on 2010-10-27
I was wrong about Virtual box needing to be paid for.
It&#347; true the OSE (open source edition) that ships with Ubuntu has no USB support, but you can download the full version from VB website. It&#347; free for personal use:
[http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523~Ubuntu~maverick_i386.deb](http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523~Ubuntu~maverick_i386.deb)

This gives you USB support that you need to use your iphone with windows in VB.

 Id use Win XP and not Vista or Win 7, since they run very slow in VB. Also, use itunes 8.2 or earlier if you can. Less bloated that the newer versions.

---

### Post by DiNozzo92 on 2010-10-27
Did you have to do any special do get USB enabled?
I got XP installed , and I got an external USB drive, but when I right click the USB Devices in the bottom bar of the VM , the "LaCie Disk" is there , but it's disabled..
Do I have to activate USB anywhere else?

---

### Post by annoyingrob on 2010-10-27
Yes, you need to go into the  virtual machine settings when the machine is powered down, and enable USB support.

Works fine for me, but it's quite slow to sync.

---

### Post by ives31 on 2010-10-28
when windows in fired up, plug on your USB device and then go to 'Devices'  (top left) and put a tick next to the Apple device. Then the phone will show up in Windows.

---

