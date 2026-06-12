---
title: "screen goes completly black for a few sec when browsing"
date: 2012-04-02
forum: General Help
---

### Post by petru.marginean on 2012-04-02
Hi,

My computer's screen flashes black when accessing a page that has flash videos (e.g. ads). It turns completely black for 1-2 sec, and then comes back.

It happens when using Firefox, Chrome or Opera.

I was able to reproduce it like following:
- browse to a page that displays some animation using flash
- the screen turns black

Then it turns black again every time I press the "Refresh" button in the browser.

I have Ubuntu 11.10, Firefox 11.0...
Any idea how I can fix this?

Regards,
Petru

$> uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

$> firefox -v
Mozilla Firefox 11.0

$> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

---

### Post by raja.genupula on 2012-04-02
from when you're facing this ?  have you gone through any recent updates ?

---

### Post by petru.marginean on 2012-04-02
It started a few weeks ago, unfortunately I cannot say exactly when I first noticed it.
Also I keep the machine up to date, and I don't pay much attention what package gets updated...

Regards,
PM

---

### Post by raja.genupula on 2012-04-03
as  my roam in forums , i have came through many threads as having issue as you facing with flash . 

under my knowledge i can suggest you as 
* re installation of flash.
* re installation of your graphics drivers .

So try them and report back if any one of them work for you .

---

### Post by petru.marginean on 2012-04-05
The graphic drivers look fine: only flash looks affected.

I've removed adobe flash like suggested, and the issue went away.
As soon as I reinstalled it the issue came back!

I also noticed the colors in flash videos are affected: the faces of people are blue-ish.
W/o flash I can see some videos on youtube in html5 format.
No black screen flashes, nice colors but... no sound (even my computer has sound)

This is so frustrating... 
:-(

PM

---

### Post by petru.marginean on 2012-04-06
Figured it out.
I've deleted the directory :
```
$> rm -fr ~/.adobe/Flash_Player/
```and now evrtyhing works fine.

PM

---

### Post by petru.marginean on 2012-04-06
The issue is still there: once I restarted the browser the black flash appeared again.

Regards,
PM

---

### Post by petru.marginean on 2012-04-09
I've installed the 12.04, but still no luck.

Regards,
Petru

---

### Post by winh8r on 2012-04-09
Click on the link in my sig below entitled "Help with Flash".

There is currently an issue with flash player, due to Adobe ending their support for Flash Player on Linux. As a result, the latest Flash Player has been causing a lot of problems , similar to those you describe.

The page linked to below gives step by step instructions on how resolve the issue using a workaround.

Please read the full post by **[COLOR="Red"]lovinglinux[/COLOR]** for further details.

Hope this helps.

---

### Post by petru.marginean on 2012-04-13
Many thanks [winh8r]("http://ubuntuforums.org/member.php?u=388218"), it did help!

The first suggestion fixed it, disabling the hardware acceleration: right-click on a flash video + Settings... + first tab and unchecked "Enable hardware acceleration"


Best,
PM

---

### Post by torentas on 2013-05-05
> **petru.marginean said:**
> Many thanks [winh8r]("http://ubuntuforums.org/member.php?u=388218"), it did help!  The first suggestion fixed it, disabling the hardware acceleration: right-click on a flash video + Settings... + first tab and unchecked "Enable hardware acceleration"   Best, PM  The same here. TRying to solve this issue for weeks and then a simple unchecking "Enable hardware acceleration" FIXED it in a second.   Thanks!!!

---

### Post by oldos2er on 2013-05-05
Old thread closed.

---

