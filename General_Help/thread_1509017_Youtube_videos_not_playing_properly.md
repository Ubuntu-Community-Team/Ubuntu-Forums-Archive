---
title: "Youtube videos not playing properly"
date: 2010-06-13
forum: General Help
---

### Post by davy jones on 2010-06-13
Something very strange is happening with youtube videos on my laptop. I just installed Lucid 64 bit and in some youtube videos I'm unable to click on any controls. I can't change the volume, can't turn off annotations and can't even pause or switch to better resolution. In some videos I'm able to pause and change volume but I still can't switch to higher resolution because when I point to the resolution button and the options of 480p and 720p pop up and I click on them the video just pauses, as if the pop-up was transparent. Youtube videos were playing perfectly in the 32 bit version of Lucid. Can someone help me out here?

---

### Post by tom.swartz07 on 2010-06-13
> **davy jones said:**
> Something very strange is happening with youtube videos on my laptop. I just installed Lucid 64 bit and in some youtube videos I'm unable to click on any controls. I can't change the volume, can't turn off annotations and can't even pause or switch to better resolution. In some videos I'm able to pause and change volume but I still can't switch to higher resolution because when I point to the resolution button and the options of 480p and 720p pop up and I click on them the video just pauses, as if the pop-up was transparent. Youtube videos were playing perfectly in the 32 bit version of Lucid. Can someone help me out here?

yep. theres a bug with the 32 bit version of flash running on the 64 version of Ubuntu.

You could upgrade to the x64 bit version, but I have to warn you; they recently 'paused' development on it, so there might be unpatched security holes. As of right now, its very stable, and I havent had any problems.

You could run my script located here: [http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer](http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer)

Run it from the terminal, and you should be all set!



Alternately, you could run the 32 bit version with a 'wrapper' to make it 64 bit. I dont know specifics for this, but im sure someone else does


Also, ive found that if you 'middle click' it works too. haha

---

### Post by Monotoko on 2010-06-13
Just follow this howto to fix the bug, worked fine for me :)
None of the uninstalling/reinstalling needed:

[http://heratech.net/blog/sham/cant-click-playpause-flash-youtube-etc-ubuntu](http://heratech.net/blog/sham/cant-click-playpause-flash-youtube-etc-ubuntu)

---

### Post by vamshikris422 on 2010-07-14
> **tom.swartz07 said:**
> yep. theres a bug with the 32 bit version of flash running on the 64 version of Ubuntu.

You could upgrade to the x64 bit version, but I have to warn you; they recently 'paused' development on it, so there might be unpatched security holes. As of right now, its very stable, and I havent had any problems.

You could run my script located here: [http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer]("http://bazaar.launchpad.net/%7Etom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer")

Run it from the terminal, and you should be all set!



Alternately, you could run the 32 bit version with a 'wrapper' to make it 64 bit. I dont know specifics for this, but im sure someone else does


Also, ive found that if you 'middle click' it works too. haha


thank you... it worked for me...

---

