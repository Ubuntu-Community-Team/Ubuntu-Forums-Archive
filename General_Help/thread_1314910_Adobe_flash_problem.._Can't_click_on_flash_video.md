---
title: "Adobe flash problem.. Can't click on flash video"
date: 2009-11-04
forum: General Help
---

### Post by Syirrus on 2009-11-04
Having problems clicking on flash videos to play, skip or pause them?  This is a documented bug and it seems to effect those who are running flash with compiz enabled.

_A quick and dirty work around_
This sounds lame but it worked for me. If I right-click and hold the right mouse button while clicking on the flash video; play, skip and pause suddenly work. As soon as I let off of the right mouse button it doesn't work.  I tested it in Chromium and Firefox.

This is not a solution but I hope it helps.

Syirrus

Running: Ubuntu 9.10 AMD64 with adobe flash player 10

---

### Post by 3rdalbum on 2009-11-04
Thanks, I'll try that next time.

---

### Post by Syirrus on 2009-11-05
> **3rdalbum said:**
> Thanks, I'll try that next time.

Is this working for anyone?  It still seems to be working for me.

---

### Post by Dangger on 2009-11-06
It actually works for me too! I wonder if these bugs get fixed before the next release.

---

### Post by P4man on 2009-11-06
MXT posted this in a wrong thread, I think he wanted to post it here. Looks interesting:

[http://ubuntuforums.org/showpost.php?p=8259505&postcount=21](http://ubuntuforums.org/showpost.php?p=8259505&postcount=21)

---

### Post by 043087m135 on 2009-11-09
This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

---

### Post by KnutHB on 2009-11-10
> **Syirrus said:**
> Is this working for anyone?  It still seems to be working for me.

Confirmation of bug and the workaround works for me.

---

### Post by ricojonah on 2009-11-11
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

Thanks for the quick info. I was having the same issue with Flash. These steps resolved it for me (Ubuntu 9.10, 64-bit).

---

### Post by Digikid on 2009-11-11
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Follow that.

---

### Post by Zoot7 on 2009-11-11
What is also worth trying is grabbing the .deb off adobe's website. It seems to play nicer for me in Karmic. 
I remember reading that the package in the repositories is broken apparently.

---

### Post by pinguy on 2009-11-13
Thanks for the tip, doing the whole holding the left mouse click works for me also.

---

### Post by rifak on 2009-11-13
the workaround posted in other forums is only for 64bit. i say this because on 32bit machines, you don't even have an 'npviewer' file to change...so im not sure what to do. the whole right click thing works fine, but it's kind of embarrassing when someone is using your computer and you have to tell them this to just get a video to play. another thing is that it only messes up when using chrome/chromium, flash interaction works fine for me in firefox. anyone else having this issue of not having 'npviewer'?

---

### Post by phoozle on 2009-11-14
I experience the same issue in Karmic.

Flash works flawlessly in Firefox but in Chrome some flash buttons screw up.

Right click, click FTW! Cheers.

I hope they fix this soon.

---

### Post by tyler2time on 2009-11-14
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah
  Thank you so much.  I just spent like 2 hours downloading, installing, reinstalling deleting, editing, uninstalling, moving, extracting, reconfiguring and rebooting.  And all I had to do was add one line of text.  Thanks again you are awesome.  Just wish I would of saw this 2 hours ago

---

### Post by shobhitg on 2009-11-15
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

This workaround did not work for me.

I am using (wubi) ubuntu 64 bit. I recently upgraded to 9.10 a week ago.

-Shobhit

---

### Post by ADK01 on 2009-11-17
> **ego-sum-deus said:**
> the workaround posted in other forums is only for 64bit. i say this because on 32bit machines, you don't even have an 'npviewer' file to change...so im not sure what to do. the whole right click thing works fine, but it's kind of embarrassing when someone is using your computer and you have to tell them this to just get a video to play. another thing is that it only messes up when using chrome/chromium, flash interaction works fine for me in firefox. anyone else having this issue of not having 'npviewer'?

It seems to work for me so far on a 32bit machine. I just make sure that the variable (GDK_NATIVE_WINDOWS) is set to 1 when I launch my browser (in my case firefox)
For example, I set the variable in a startup script that I use for firefox

---

### Post by tylluan on 2009-11-17
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

This looks lit it fixed it for me.  Thanks!

---

### Post by Marlow925 on 2009-11-29
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

Hi, I had the exact same problem, this fixed it for me. Ubuntu Karmic (9.10), 64-bit. Thanks.

/M

---

### Post by v1nsai on 2009-12-21
For the people still having troubles, try the fix listed [here]("http://astoryworthtelling.wordpress.com/2009/11/09/cant-click-in-flash-using-ubuntu-9-10-karmic-try-this/")

Hope it helps

---

### Post by nicknefarious on 2009-12-21
Just to confirm this fixed worked for me. Previous to this fix I couldn't click on most links that appeared in Flash in Firefox. After I followed the instructions...

> IE,

* Hit ALT+F2 and enter
* gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
* add the following line BEFORE the last line of text
* export GDK_NATIVE_WINDOWS=1
* Save.
* Restart any applications using flash

Everything that wasn't working before is now working. 64 bit Karmic with latest Firefox and Flash Player installed.

Thanks for the fix.

Nick

---

### Post by Humr22 on 2010-01-06
Thanks for the work around, I thought I would go crazy when my clicking only works less than half the time.

---

### Post by OobNosferatu on 2010-01-13
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah


This was working for me until I upgraded some stuff on karmic. :( Anyone else having similar problems???

---

### Post by Syirrus on 2010-01-13
> **OobNosferatu said:**
> This was working for me until I upgraded some stuff on karmic. :( Anyone else having similar problems???

The solution below still seems to be working for me.  What did you upgrade in Karmic?

[http://helpforlinux.blogspot.com/200...in-ubuntu.html](http://helpforlinux.blogspot.com/200...in-ubuntu.html)

IE,

* Hit ALT+F2 and enter
* gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
* add the following line BEFORE the last line of text
* export GDK_NATIVE_WINDOWS=1
* Save.
* Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

---

### Post by v1nsai on 2010-01-14
Nosferatu, check /usr/lib/nspluginwrapper/i386/linux/npviewer to make sure the gdk_native_windows entry is still there and that the file didn't get overwritten during the upgrade

---

### Post by 00ber n00b on 2010-01-16
This npviewer workaround worked for me.  Karmic 64

---

### Post by hamid.nyc on 2010-01-30
Thanks 043087m135 (Micah, Page 1), that extra line in npviewer worked like a charm, at least in Firefox so far...

---

### Post by panicosm on 2010-01-31
Solution with npviewer works 9.10 64

Thanks

---

### Post by mjcritchie on 2010-02-05
The npviewer also works for me. Much appreciated!

---

### Post by Sam Fallow on 2010-02-23
Thanks for this. Fix worked for me running 64-bit.

I had been using the tab key to navigate around buttons.

---

### Post by binho on 2010-03-15
tks!

> * Hit ALT+F2 and enter
* gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
* add the following line BEFORE the last line of text
* export GDK_NATIVE_WINDOWS=1
* Save.
* Restart any applications using flas

worked for me in ubuntu 9.10 64 bits!

---

### Post by Emperor Jake on 2010-03-29
Thanks for this! I had this exact problem, in the exact same version, and used the exact same solution!:D

Thanks,
 - Jake

---

### Post by Grenage on 2010-03-29
What will also fix it, is removing the flash plugins via synaptic, and manually installing the current release from the adobe site.

I have it on my home machine after every install.

---

### Post by JaspSoft on 2010-04-23
thanks.

worked on my ubuntu 10.04 beta 64 bittys

---

### Post by Grams79 on 2010-05-11
[size=5]FIXED![/size]

> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah

This workaround solved the issue while using Ubuntu 10.04 x64 with Adobe Flash plugin from the software center.
Finally back to my Flash projects that I couldn't test in Firefox, not to mention I can finally close the damn Youtube ads again.
Thanks!

---

### Post by Lylex11 on 2010-06-01
This worked for me. Thanks.

---

### Post by WolfRage on 2010-06-11
@**Micah **- Thanks this has been a problem for me since Ubuntu 9.04 now Flash works again what a relief.

---

### Post by teddyinajapan on 2010-07-02
> **043087m135 said:**
> This seems to have fixed it for me:

[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

IE,

    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

I've only tested Pandora with this change but its working flawlessly for the last few minutes. Give it a whirl.

~Micah


WOW cool thanks man !!! Worked for me !!! 
BTW how the hell did you figure out how to do that ...????
WOW !!!

---

