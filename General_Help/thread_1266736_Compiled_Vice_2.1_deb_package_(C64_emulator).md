---
title: "Compiled Vice 2.1 deb package (C64 emulator)"
date: 2009-09-15
forum: General Help
---

### Post by petermg on 2009-09-15
COMMODORE 64 EMULATOR VICE 2.1 !!!

I had trouble getting this to work, but finally I got it!!  Here is the deb I created if anyone is interested:

 [http://www.filefactory.com/file/ah9e290/n/vice_2_1-1_i386_deb](http://www.filefactory.com/file/ah9e290/n/vice_2_1-1_i386_deb) 

You can download games for free/legally at [www.c64.com](www.c64.com)

The audio on it doesn't work, at least it doesn't on my system.  Not sure if it's how I compiled it or just my own settings.  But I really liked using Vice on Windows XP, so I figured I'd share the love with anyone else who wants it :D

Also if there is a better place for me to post deb packages of apps I've compiled please let me know.  I looked but didn't really see an obvious place.

Hope someone appreciates this.  I searched and searched and the only version in the repos I found was like 1.4 or something like that.  This is version 2.1, the latest! :D
:guitar:

---

### Post by petermg on 2009-09-15
apparently if you launch it like this

aoss x64

or

aoss x64dtv


aoss it an OSS sound wrapper for alsa and it enables the sound, but seems to make other sounds on my system pause and skip sometimes while the application is running... :\

---

### Post by Rytron on 2009-09-24
> **petermg said:**
> apparently if you launch it like this

aoss x64

or

aoss x64dtv


aoss it an OSS sound wrapper for alsa and it enables the sound, but seems to make other sounds on my system pause and skip sometimes while the application is running... :\

Hello. Are there any more launch command such as ```
aoss x64
``` or ```
aoss x64dtv
```

---

### Post by cronos on 2009-12-22
Just to let you all know that Vice v2.2 was released a few days ago.

Get it here: [http://vice-emu.sourceforge.net/#download](http://vice-emu.sourceforge.net/#download)

---

### Post by Rytron on 2009-12-23
> **cronos said:**
> Just to let you all know that Vice v2.1 was released a few days ago.

Get it here: [http://vice-emu.sourceforge.net/#download](http://vice-emu.sourceforge.net/#download)

Thank you cronos. :popcorn:

---

### Post by nathanpc on 2010-06-21
Please reupload the RapidShare link, because it was deleted. :-k

---

### Post by mrwaistcoat on 2011-06-02
Bump!

Thankyou so much to whoever made the deb package.  Prior to finding this thread I'd wasted two hours trying to sort it out and follow other instructions, this is great

All I need now is a Joystick!
Wonderful stuff

---

### Post by petermg on 2011-06-03
> **mrwaistcoat said:**
> Bump!

Thankyou so much to whoever made the deb package.  Prior to finding this thread I'd wasted two hours trying to sort it out and follow other instructions, this is great

All I need now is a Joystick!
Wonderful stuff

You're welcome.  I was having an awful time finding a working binary (the version installed by the synaptic package manager would not work at all for me) so I decided to try to simply compile one on my own so when I finally was able to compile the deb, I thought I'd share it with everyone as I was unable to find one anywhere on the internet!  
I love the C64!!! :D and I love this emulator :)

---

### Post by mrwaistcoat on 2011-06-07
mmmm strange

All was working great, now it has just stopped, nothing happening at all

I've uninstalled it via the package manager, and reinstalled from your link

Still nothing

Any ideas?  Not sure if this helps but I did mess with the settings on the GUI the last time it worked...

Thanks in advance if you can suggest anything

Btw don't suppose you are also a spectrum fan ?  Fuse seems to have gone from the repros and I cant find a deb package anywhere.

---

### Post by Rytron on 2011-06-07
> **mrwaistcoat said:**
> mmmm strange

All was working great, now it has just stopped, nothing happening at all

I've uninstalled it via the package manager, and reinstalled from your link

Still nothing

Any ideas?  Not sure if this helps but I did mess with the settings on the GUI the last time it worked...

Thanks in advance if you can suggest anything

Btw don't suppose you are also a spectrum fan ?  Fuse seems to have gone from the repros and I cant find a deb package anywhere.

I had to lock the deb package from being upgraded to the Synaptic version
```
echo vice hold | dpkg --set-selections
```

Try deleting ~/.vice and completely removing Vice from synaptic and then reinstalling deb vice.

You can get Fuse here: [http://people.igalia.com/berto/](http://people.igalia.com/berto/)

---

### Post by mrwaistcoat on 2011-06-07
I've again uninstalled Vice from synaptic, but again the reinstall doesn't work. You say remove it from synaptic altogether - how do I do that?

I also get the following error
rick@desktopPC:~$ echo vice hold | dpkg --set-selections
dpkg: operation requires read/write access to dpkg status area

---

### Post by Rytron on 2011-06-15
> **mrwaistcoat said:**
> I've again uninstalled Vice from synaptic, but again the reinstall doesn't work. You say remove it from synaptic altogether - how do I do that?

I also get the following error
rick@desktopPC:~$ echo vice hold | dpkg --set-selections
dpkg: operation requires read/write access to dpkg status area

Remove ~/.vice directory
Uninstall vice from Synaptic (Right click in Synaptic and select **complete removal**)
Install Vice deb package

Lock it.

Re error. Goto Synaptic and goto Status and see is there any broken packages.

---

### Post by Ralph Hinkley on 2011-06-25
I've been using 2.1 which I got right here:

[http://ubuntuforums.org/showthread.php?t=1371606](http://ubuntuforums.org/showthread.php?t=1371606)

The sound works on mine. It's awesome, but it does crash every now and then.

---

### Post by Rytron on 2011-06-26
> **Ralph Hinkley said:**
> I've been using 2.1 which I got right here:

[http://ubuntuforums.org/showthread.php?t=1371606](http://ubuntuforums.org/showthread.php?t=1371606)

The sound works on mine. It's awesome, but it does crash every now and then.

Cheers Ralph. ;)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-12
I've just installed VICE 2.3.dfsg-2 from Synaptic. But when I click on it from Dash, nothing happens. Is there anyone who has this working on Precise?

---

