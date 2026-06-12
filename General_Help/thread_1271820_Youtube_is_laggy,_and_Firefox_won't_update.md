---
title: "Youtube is laggy, and Firefox won't update"
date: 2009-09-21
forum: General Help
---

### Post by Auslegung on 2009-09-21
I'm running 9.04 eeebuntu on an Asus 1000HA, standard with the obligatory 2gb RAM added.  I've spent over an hour searching the web with no luck.  Youtube has been getting more and more laggy over the last couple of months, and I've just dealt with it, but now I'm tired of it.  I had adobe-flashplugin installed so I tried to update it, but it was the newest version.  Then I removed all my flashplugins and installed just flashplugin-nonfree.  Still no luck.

Then I ran across something about updating Firefox.  I checked and sure enough my Firefox is 3.0.14.  After 15 minutes of trying to update it, I've decided I'm retarded and/or Firefox is.  I've tried downloading from the website, I've tried using synaptic, I've tried using terminal, and after I download 3.5 it doesn't update.  I restart Firefox and it's still the same old version.  Any ideas?

---

### Post by highfructose327 on 2009-09-21
9.04 is not using Firefox 3.5 if you want to use 3.5 you check out this link[http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/]("http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/") on how to install firefox 3.5. good luck

---

### Post by Auslegung on 2009-09-21
I got 3.5 but youtube is still laggy.

---

### Post by badook on 2009-09-21
Try this:

```

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

```

It basically forces flash to use gpu accelleration

---

### Post by Auslegung on 2009-09-21
> **badook said:**
> Try this:

```

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

```

It basically forces flash to use gpu accelleration

Tried it and it changed nothing.  Thanks for the suggestions so far, please keep them coming.  The most recent video to resist all my efforts of watching it smoothly is this one: <[http://www.youtube.com/watch?v=VGDeA4papLg]("http://www.youtube.com/watch?v=VGDeA4papLg")>.  I figured I'd mention that in case it is important.

---

### Post by Nostalos on 2009-09-21
Not trying to rain on your parade as I would love for this to work far better than it does.    Unfortunatly think your problem "might" be two fold.   I don't own that specific netbook so I can't say for sure, but.

1.  Adobe Flash under Mac/Linux are real under performers.   Adobe has not put the time in on those as it has on windows and continuously under performs the windows version.

2.  Don't know if this is the case with you or not, but in 9.04 Intel cards had a regression problem between Kernel and Xorg.   Can give the following link a read to see if this might be affecting you as well.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)


And just FYI, I can't play that video smoothly on any of my boxes with Intel Vid adapters on 8.10 or 9.04.   I don't have access to my nvidia/ati machines to test it from those.

---

### Post by Auslegung on 2009-09-21
> **Nostalos said:**
> Not trying to rain on your parade as I would love for this to work far better than it does.    Unfortunatly think your problem "might" be two fold.   I don't own that specific netbook so I can't say for sure, but.

1.  Adobe Flash under Mac/Linux are real under performers.   Adobe has not put the time in on those as it has on windows and continuously under performs the windows version.

2.  Don't know if this is the case with you or not, but in 9.04 Intel cards had a regression problem between Kernel and Xorg.   Can give the following link a read to see if this might be affecting you as well.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)


And just FYI, I can't play that video smoothly on any of my boxes with Intel Vid adapters on 8.10 or 9.04.   I don't have access to my nvidia/ati machines to test it from those.

Thanks, following that seems to have solved the video problem quite nicely (except it devours resources), but now my mousepad is a little laggy.  Oh well, hopefully there's a fix for that, but thanks for the link.

---

### Post by Nostalos on 2009-09-21
Awesome.  I know some folks have had luck with it.  Myself, I've not been so lucky.  Glad it helped.

---

### Post by H_out on 2009-10-30
I was having trouble with laggy Flash videos (especially full-screened) and found a quick fix.

Right click the Flash video, click settings, and UNCHECK the "Enable hardware acceleration" box.

Definitely counter-intuitive, but solved my problem.

---

