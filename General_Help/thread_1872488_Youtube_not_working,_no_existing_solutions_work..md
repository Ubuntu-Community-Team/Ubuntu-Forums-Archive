---
title: "Youtube not working, no existing solutions work."
date: 2011-10-30
forum: General Help
---

### Post by Ladders on 2011-10-30
I have been running Xubuntu 11.10 for a while now with no problems. Recently (seemingly out of nowhere) Youtube videos stopped working, just giving a black screen with "An error occurred. Please try again later.".

I have the latest version of Adobe Flash installed, I do not have gnash or swfdec installed, the Flash-Aid and Flashblocker extensions for Firefox were no help at all. Clearing cookies and blocking cookies from Youtube has no effect.

I have tried both Flash 10 and the Flash plugin for Mozilla that are available in the software centre. Nothing works. Now the message I get on every Youtube page is "You need to upgrade your Adobe Flash Player to watch this video. Download it from Adobe." which links me to download the version of Flash I already have installed.

I've also made sure that the ubuntu and xubuntu restricted extras packages are installed.

Am I missing something? I did not install anything new or removing anything, this has come completely out of the blue.

EDIT: This seems to affect other things requiring Flash. I can't watch anything on BBC iPlayer either.

---

### Post by Gremlinzzz on 2011-10-30
Go to view hidden folders and delete the Mozilla folder and Marcomedia folder. don't worry soon as you use Firefox they will be back.it will clean up firefox.

---

### Post by Ladders on 2011-10-30
Thanks, that partially worked. The videos play but there is no sound.

Also, is there a more permanent solution? I'd rather not have to re-import my bookmarks, re-install my add-ons and re-customise the layout every time it decides to go haywire.

---

### Post by Gremlinzzz on 2011-10-30
Then in your new Mozilla folder create a folder and name it plugins.
download the flash player with tar.gz , extract here / take the libflashplayer.so file and copy into the plugins folder you created.
done you should have flash:popcorn:

---

### Post by Ladders on 2011-10-30
I can't find it is a tar.gz, the only thing I can find tries to install through the software centre.

---

### Post by Gremlinzzz on 2011-10-30
> **Ladders said:**
> I can't find it is a tar.gz, the only thing I can find tries to install through the software centre.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Gremlinzzz on 2011-10-30
> **Ladders said:**
> Thanks, that partially worked. The videos play but there is no sound.

Also, is there a more permanent solution? I'd rather not have to re-import my bookmarks, re-install my add-ons and re-customise the layout every time it decides to go haywire.

That was just to clean it up cause i didn't know what you installed that cause it to go haywire:popcorn:

you could also install bleachbit its a system cleaner install from software center

---

### Post by mike555 on 2011-10-30
if you can't get it to work there is an add-on for firefox called FlashVideoReplacer , I haven t tried it though.

---

### Post by Gremlinzzz on 2011-10-30
> **mike555 said:**
> if you can't get it to work there is an add-on for firefox called FlashVideoReplacer , I haven t tried it though.

me either but its worth a shot. first make sure sounds not muted:popcorn:

---

### Post by Ladders on 2011-10-31
The link you gave me will only allow download and installation through the software centre.

I've installed flashvideoreplacer, and whenever I try to play something I get a message saying "FVR was unable to play the video, due to lack of compatible plugin for autodetect.".

EDIT: I was being an idiot, I found how to download the tar.gz. I put the .so file in the folder you said and uninstalled FVR, but there's still no sound.

---

### Post by beew on 2011-10-31
> **Ladders said:**
> 

I've installed flashvideoreplacer, and whenever I try to play something I get a message saying "FVR was unable to play the video, due to lack of compatible plugin for autodetect.".

To use the flashvideoreplacer you need to install the gecko-mediaplayer from the repository.

It is an excellent addon. Flash works on my systems but I still use the FVR for the supported sites because it is much better than flash in terms of cpu usage.

---

### Post by Ladders on 2011-10-31
I've installed gecko-mediaplayer and FVR still doesn't work.

---

### Post by beew on 2011-10-31
Hmm... maybe you should ask the developer. He is a member of this forum and is very helpful.

[http://ubuntuforums.org/showthread.php?t=1487327](http://ubuntuforums.org/showthread.php?t=1487327)

Another alternative to play youtube would be minitube. Install it from the webupd8 ppa ([https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)) instead of the Ubuntu repository, the version in the repo is usually outdated or broken or both.

---

### Post by Ladders on 2011-10-31
Ah, no need. I reinstalled it all and rebooted, works perfectly now.

Thank you all for your help, and for putting up with such a noob.

---

