---
title: "Flash for using a live CD Ubuntu 10.10 mp3 and Youtube"
date: 2010-11-29
forum: General Help
---

### Post by CallDon on 2010-11-29
Due to a glitch in my XP boot sequence on my Thinkpad, I am using a live CD of Ubuntu 10.10.  I have to stick with XP on this computer so I am gonna get it repaired.  I need Windows and, there's not enough disk space to load 10.10 on the hard drive for a dual boot on this machine.

Love 10.10 except for no flash or mp3 support.  Every day, I boot up with the CD, have to log-in for mail, Facebook, etc.   The problem is, no mp3 playback, including my online radio station using pls files.  And no Youtube or flash.  I tried adding the plugin (as it says) but don't know how to make it work while using the live CD.

Any suggestions?

Thanks
Don

---

### Post by olof_ on 2010-11-29
go to [this]("http://get.adobe.com/flashplayer/") link, and choose *"APT for Ubuntu 9.04+"*. It will open a instance of "Ubuntu Software Center", where you will be prompted to enable repostories (or something similar). It will take some time, and then the enable repostories button will be exchanged to a install button. Press it and let the program install. When it is finished, restart Firefox. You have flash support.

---

### Post by CallDon on 2010-11-29
> **olof_ said:**
> go to [this]("http://get.adobe.com/flashplayer/") link, and choose *"APT for Ubuntu 9.04+"*. It will open a instance of "Ubuntu Software Center", where you will be prompted to enable repostories (or something similar). It will take some time, and then the enable repostories button will be exchanged to a install button. Press it and let the program install. When it is finished, restart Firefox. You have flash support.

Finally figured it out and got it to work for the youtube.   Now I have to figure out how to do MP3 and pls files.   

EDIT UPDATE:

Again, I discovered I can go to Applications > Software Center and search for VLC Media Player which will play the stream!!!  Works great so far.   

Thanks for the help!!!  Just knowing about and getting used to the "Software center" to find programs helps alot.

D*

---

### Post by olof_ on 2010-11-29
maybe [this]("http://psychocats.net/ubuntu/mp3") helps fixing mp3 playback?

about the .pls playback, it seems to be a [known]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/62430") limitation, you have to drag and drop the file to rhythmbox. (Application->music and video ->rhythmbox)

right click on the link you supplied ->save as, and then open it by drag and drop might be a good start AFAIK.

edit:
maybe try to install some other music playing programs and test with them...

---

### Post by CallDon on 2010-11-29
> **olof_ said:**
> maybe [this]("http://psychocats.net/ubuntu/mp3") helps fixing mp3 playback?

about the .pls playback, it seems to be a [known]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/62430") limitation, you have to drag and drop the file to rhythmbox. (Application->music and video ->rhythmbox)

right click on the link you supplied ->save as, and then open it by drag and drop might be a good start AFAIK.

edit:
maybe try to install some other music playing programs and test with them...

Thanks.  I am making a list and sending myself an e-mail with these suggestions and with what I have done so far.  The problem is, all of this is being done with a live CD, not with Ubuntu installed.  So when I reboot, I will have to do this all over again.  But at least I know more about how to do it now.  

Thanks again,
D*

---

