---
title: "Can you watch this vid? (i can't)"
date: 2010-07-28
forum: General Help
---

### Post by justinsn95 on 2010-07-28
<object width="480" height="385"><param name="movie" value="http://www.youtube.com/v/zzctPPkUPkk&amp;hl=en_US&amp;fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/zzctPPkUPkk&amp;hl=en_US&amp;fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="480" height="385"></embed></object>

This is an embeded youtube vid, as I'm sure you have all seen before. I can see it, but when I click play, or try to change the volume, or more the slider, nothing happens. This was happening to me yesterday, when I was actually at youtube. But now, it seems that I can control the vids as long as I am on the youtube website. But when I want to watch one that someone has posted, I can not. Anyone know the reason? I am running Ubuntu 10.04

Ok, well. That didn't work. How about this: Here is a link to another site where I posted the same vid:

[http://www.dfwstangs.net/forums/showthread.php?t=419343](http://www.dfwstangs.net/forums/showthread.php?t=419343)

---

### Post by hansdown on 2010-07-28
Hi justinsn95.

There was a firefox update for downloadhelper, that lets you play this.

I was able to right click the vid, then choose to watch vid on youtube.

---

### Post by no2498 on 2010-07-28
i just clicked it and it played

---

### Post by luigi_mb on 2010-07-28
> **justinsn95 said:**
> <object width="480" height="385"><param name="movie" value="http://www.youtube.com/v/zzctPPkUPkk&amp;hl=en_US&amp;fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/zzctPPkUPkk&amp;hl=en_US&amp;fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="480" height="385"></embed></object>

This is an embeded youtube vid, as I'm sure you have all seen before. I can see it, but when I click play, or try to change the volume, or more the slider, nothing happens. This was happening to me yesterday, when I was actually at youtube. But now, it seems that I can control the vids as long as I am on the youtube website. But when I want to watch one that someone has posted, I can not. Anyone know the reason? I am running Ubuntu 10.04

Ok, well. That didn't work. How about this: Here is a link to another site where I posted the same vid:

[http://www.dfwstangs.net/forums/showthread.php?t=419343](http://www.dfwstangs.net/forums/showthread.php?t=419343)

It works fine here.


/luigi

---

### Post by millybreak on 2010-07-28
Not here!

But I'm on AMD64, so no vids/Youtube for me, since the Adobe sabotage.:(

---

### Post by lisati on 2010-07-28
Plays fine here, 64 bit 10.04.

---

### Post by justinsn95 on 2010-07-28
> **lisati said:**
> Plays fine here, 64 bit 10.04.

That is what I am using. So why is the vid completely unresponsive? Is this "Downloadhelper" something I can go get from somewhere and make it play? I am in the process of working out all the kinks in Ubuntu, and this is just one on the list.

---

### Post by lovinglinux on 2010-07-29
This usually happens when you are using the 32bit plugin on a 64bit system. If this is the case, then you need to edit the npviewer file. 

Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by justinsn95 on 2010-07-30
> **lovinglinux said:**
> This usually happens when you are using the 32bit plugin on a 64bit system. If this is the case, then you need to edit the npviewer file. 

Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

You're the *man*. But of course now I have to ask.. How did you know this? I bet you don't ever have to use windows for anything do you? Are you any good at WINE?

---

### Post by lovinglinux on 2010-07-30
> **justinsn95 said:**
> You're the *man*. But of course now I have to ask.. How did you know this? I bet you don't ever have to use windows for anything do you? Are you any good at WINE?

To be honest, I saw this fix on another post somewhere in the forums or on launchpad. I don't remember where tho. I used to ignore it, since most 64bit users were fine with the 64bit version of flash, but since Adobe stopped supporting it and left us with a critical vulnerability, I have been recommending this fix.

I also [develop a couple of Firefox extensions]("https://addons.mozilla.org/en-US/firefox/user/4352153") to make flash experience better and other extensions for Ubuntu users. You might like FLASH-AID and FlashVideoReplacer.

I have a grudge with Flash :)

> **justinsn95 said:**
> I bet you don't ever have to use windows for anything do you?

Unfortunately I need to use Windows in order to test my extensions, if I want to provide compatibility for Windows users. But I don't need it for anything else and I hate to use it. I feel completely lost when I start Windows, which is odd, considering I used it for more than 15 years and I'm using Linux for just 2 years.

> **justinsn95 said:**
> Are you any good at WINE?

Nope. Fortunately, there is only one simple program I need that requires wine and it works flawlessly.

---

### Post by justinsn95 on 2010-07-31
Well I am going to try to run all kinds of stuff with wine. Mainly games though. 

But I heard that there is something called WineDoors that makes configuring wine even easier. Ever heard of it? I looked for it in the Ubuntu Software Center and its not there. Is it only for linux Mint?

---

