---
title: "Gparted, resizing Ubuntu Drive"
date: 2010-09-30
forum: General Help
---

### Post by Peter7K on 2010-09-30
Hi all.. I'd like to install Windoze *after* this current Ubuntu install.  How can I resize my ubuntu drive to allow Window$ around 10gigs of space?  It seems I can't resize it while it's mounted... is it impossible?

---

### Post by kDDs on 2010-09-30
*Windows**

You could boot into the ubuntu live CD and do it from there. Gparted is installed on the live CD. It will not be possible to do it while the partition is mounted, so if windows is on the same physical drive as ubuntu, you'll have to do it while neither system is booted.

---

### Post by oldos2er on 2010-09-30
May I suggest you install Windows first? People seem to have fewer problems that way.

Boot the LiveCD and run gparted from there.

---

### Post by drs305 on 2010-09-30
Here's a post I made about resizing /.  It assumes you already have a Windows partition and takes space from it, but the tips about half way down the first post still apply. Even if you want to shrink rather than expand...

The short answer: Boot the LiveCD and use gparted. Backup any important files first.

[_http://ubuntuforums.org/showthread.php?t=1219270_]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by Peter7K on 2010-10-01
This has been something that's been bothering me for a while... on my ubuntu cd I don't get the option to boot to the CD.  I'm using the normal 32bit architecture .iso... anyone know of any reason it wouldn't let me do that?

---

### Post by drs305 on 2010-10-01
> **Peter7K said:**
> This has been something that's been bothering me for a while... on my ubuntu cd I don't get the option to boot to the CD.  I'm using the normal 32bit architecture .iso... anyone know of any reason it wouldn't let me do that?

Just to make sure, the normal options are to install Ubuntu or to try Ubuntu. The 'try ubuntu without installing' is the 'boot to the Desktop' option we often refer to.

---

### Post by Peter7K on 2010-10-01
> **drs305 said:**
> Just to make sure, the normal options are to install Ubuntu or to try Ubuntu. The 'try ubuntu without installing' is the 'boot to the Desktop' option we often refer to.

Correct.  I sadly do not have the "try ubuntu without installing" option.  I haven't had it since 9.04 Karmic.  9.10 on cds I've made haven't had that option.

---

### Post by oldos2er on 2010-10-01
> **Peter7K said:**
> Correct.  I sadly do not have the "try ubuntu without installing" option.  I haven't had it since 9.04 Karmic.  9.10 on cds I've made haven't had that option.

Something's very wrong then. You should always check md5sum on either the ISO file or the CD. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by drs305 on 2010-10-01
Is it possible you have a copy of the Alternate CD? It's been a long time since I've used that method to install Ubuntu but I don't think the "Live Desktop" option was available with the alternate ISO.

---

### Post by psusi on 2010-10-01
In the last few releases when you boot the livecd you just get an icon showing a man and a keyboard.  You have to touch a key to have the menu come up.

---

### Post by Peter7K on 2010-10-02
Might I ask where this icon is?

These are the options I see:

> Install Ubuntu
check disc for defects
Test memory
Boot from first hard disk
Rescue a broken system

---

### Post by Manifest on 2010-10-02
When your cd loads up Do **not** press any buttons and wait then after a minute you'll see the option:)

---

### Post by psusi on 2010-10-02
> **Peter7K said:**
> Might I ask where this icon is?

These are the options I see:

Umm... it's at the bottom of the screen, before you see the menu you posted, which has the test memory option on it that everyone has been telling you to choose.

---

### Post by Peter7K on 2010-10-02
> **psusi said:**
> Umm... it's at the bottom of the screen, before you see the menu you posted, which has the test memory option on it that everyone has been telling you to choose.

Well I "waited for it to load" for about 30 minutes.  Still no icon.  I guess only the cool kids get the livecd boot option?

Seriously why is this so difficult?

---

### Post by drs305 on 2010-10-02
The 'cool' kids actually see the "Try" and "Install" options. The 'almost cool' only see the two icons...  ;-)

Have you tried pressing F6 as the CD starts to load to display the menu choices?

---

### Post by Peter7K on 2010-10-02
> **drs305 said:**
> The 'cool' kids actually see the "Try" and "Install" options. The 'almost cool' only see the two icons...  ;-)

Have you tried pressing F6 as the CD starts to load to display the menu choices?

Tried that joint already.

Okay I have attached screenshots.  This is exactly what I see when I boot up the computer (I merely booted up to a virtualbox to show you guys what it looked like booting from my "Live" cd)

---

### Post by drs305 on 2010-10-02
Just curious. If you press ESC at the language prompt, and then F1, does it state:
> "This is a live system for Ubuntu XX.XX"
which I assume means it has the LiveCD option.

---

### Post by psusi on 2010-10-02
Why are you so confused?  You got the menu, now pick the memory test option.

---

### Post by Peter7K on 2010-10-02
> **psusi said:**
> Why are you so confused?  You got the menu, now pick the memory test option.

wtf memory test doesn't do anythang, I tried it.. :O

it just tests the memory.. i want to boot to live cd

---

### Post by Quackers on 2010-10-02
Once the Ubuntu screen loads up and after you have chosen the language what happens if you press F6 on the next screen? What other options are shown, if any? What happens if you hover the pointer over the icons at the bottom right of the screen?
I ask because these items don't appear on my live cd.

---

### Post by Peter7K on 2010-10-02
> **Quackers said:**
> Once the Ubuntu screen loads up and after you have chosen the language what happens if you press F6 on the next screen? What other options are shown, if any? What happens if you hover the pointer over the icons at the bottom right of the screen?
I ask because these items don't appear on my live cd.

My third screenshot on my previous post shows the F6 options:

[http://ubuntuforums.org/attachment.php?attachmentid=171100&d=1286045561](http://ubuntuforums.org/attachment.php?attachmentid=171100&d=1286045561)

Am I creating a cd in the wrong way?  All I do is download the .iso for ubuntu 32bit, drag it to the cd in nautilus, do burn iso contents option (instead of as files or whatever).  Is there some other way I should be doing it?

I'm using a DVDR.

---

### Post by Quackers on 2010-10-02
I haven't used that method. I usually burn an .iso image with Brasero in Ubuntu or ImgBurn if I'm in Windows (free program) but in those circumstances it is necessary to choose "Burn Image".
Have you downloaded the .iso for the alternate cd by any chance?

---

### Post by Peter7K on 2010-10-02
> **Quackers said:**
> I haven't used that method. I usually burn an .iso image with Brasero in Ubuntu or ImgBurn if I'm in Windows (free program) but in those circumstances it is necessary to choose "Burn Image".
Have you downloaded the .iso for the alternate cd by any chance?

Ah.. that might be the case.  I usually just go here [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/) and torrent it, I probably clicked alternative by mistake?

Time to find another cd..

---

### Post by Quackers on 2010-10-02
Possibly. Check the MD5 of the file you downloaded against the Ubuntu site.

---

### Post by Peter7K on 2010-10-02
The help menu states:
This is an installation system for Ubuntu 10.10. It was built on 20100831.2.

So it's not a live cd?

WACKKK ATTACK

---

### Post by drs305 on 2010-10-02
> **Peter7K said:**
> The help menu states:
This is an installation system for Ubuntu 10.10. It was built on 20100831.2.

So it's not a live cd?

WACKKK ATTACK

Nope. It's an Alternate Install CD.  ](*,)

But now you know and can download the Desktop version.

[_http://www.ubuntu.com/desktop/get-ubuntu/download_]("http://www.ubuntu.com/desktop/get-ubuntu/download")

---

### Post by Quackers on 2010-10-03
Deja vu, drs305?

---

