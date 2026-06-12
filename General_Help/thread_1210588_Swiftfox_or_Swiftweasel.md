---
title: "Swiftfox or Swiftweasel"
date: 2009-07-11
forum: General Help
---

### Post by LP_Faint on 2009-07-11
which has better performance Swiftfox or Swiftweasel?

---

### Post by vinutux on 2009-07-11
both are the same firefrox folks...

swiftfox = firefox

swiftweaseal = iceweasel (a patenet free version of firefox)

................

---

### Post by lovinglinux on 2009-07-11
Swiftfox and Swiftweasel are both compiled with PGO (Profile-Guided Optimization) and processor specific optimization flags, which gives 30% performance boost on my system. Actually I don't use them, but I compile Firefox myself, using the same optimizations techniques.

Nevertheless...

> 
From: [http://en.wikipedia.org/wiki/Swiftweasel](http://en.wikipedia.org/wiki/Swiftweasel)

Released under the terms of the Mozilla Public License, Swiftweasel is free and open source software. It is distinct from Swiftfox (another optimized version of Firefox) in that Swiftweasel is completely free while Swiftfox's binaries are proprietary.

So I would choose Swiftweasel instead.


If you want to compile Firefox 3.5 it yourself, visit the "Compiling Firefox" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by hummmingbirdie on 2009-07-12
lovinglinux,  Have read your earlier replies optimization howto. Awesome! Thanks! Moved from firefox 3.5 to swiftfox, and was loving it till I hit the flash player snag.. Somehow cannot get the flashplayer working in swiftfox, whereas it was and is working in firefox 3.5. Having tasted blood, in terms of speed of swiftfox, I do not want to go back to firefox 3.5, but also don't want to go roll my own build.   Also noted that swiftfox builds, even the amd64 labelled ones are all 32 bit ones. So wanted to try and move to swiftweasel.  Went to their site, downloaded the recently uploaded build, and tried to get it up and running. No luck! there also seems to be something wrong, as even the swiftweasel 3.5 builds uploaded 2 days ago are being shown for 'hardy'??   Is there a detailed how-to about swiftweasel? I am a total greenhorn, and do not wish getting into building it on my own...  Thanks in advance for any help    PS: I use an AMD Phenom (tricore, 64 bit) so was interested in a native 64 bit build of firefox that would have PGO.                                                                                 sorry about the format of the post, can't seem to get  line breaks even when put in.. :-(

---

### Post by lovinglinux on 2009-07-12
> **hummmingbirdie said:**
> lovinglinux,  Have read your earlier replies optimization howto. Awesome! Thanks! Moved from firefox 3.5 to swiftfox, and was loving it till I hit the flash player snag.. Somehow cannot get the flashplayer working in swiftfox, whereas it was and is working in firefox 3.5. Having tasted blood, in terms of speed of swiftfox, I do not want to go back to firefox 3.5, but also don't want to go roll my own build.   Also noted that swiftfox builds, even the amd64 labelled ones are all 32 bit ones. So wanted to try and move to swiftweasel.  Went to their site, downloaded the recently uploaded build, and tried to get it up and running. No luck! there also seems to be something wrong, as even the swiftweasel 3.5 builds uploaded 2 days ago are being shown for 'hardy'??   Is there a detailed how-to about swiftweasel? I am a total greenhorn, and do not wish getting into building it on my own...  Thanks in advance for any help    PS: I use an AMD Phenom (tricore, 64 bit) so was interested in a native 64 bit build of firefox that would have PGO.                                                                                 sorry about the format of the post, can't seem to get  line breaks even when put in.. :-(

Download [swiftweasel-3.5_amd-pgo_x86_64-ubuntu.tar.gz](http://sourceforge.net/projects/swiftweasel/files/Swiftweasel%203.5.%2A/swiftweasel-3.5_amd-pgo_x86_64-ubuntu.tar.gz/download), saving it in your home directory.

Then run this in the terminal:

```
sudo tar -xvf swiftweasel-3.5_amd-pgo_x86_64-ubuntu.tar.gz -C /opt
rm swiftweasel-3.5_amd-pgo_x86_64-ubuntu.tar.gz
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/swiftweasel/plugins
sudo ln -s /opt/swiftweasel/swiftweasel /usr/local/bin/firefox

```

Then just click the firefox launcher and it will launch swiftweasel instead.

To uninstall and revert all changes:

```
sudo rm /usr/local/bin/firefox && sudo rm -r /opt/swiftweasel
```

Swiftweasel profile is saved under ~/.sw35/swiftweasel

---

### Post by oiad on 2009-08-06
Is there an easy way like this to accomplish the same with swiftdove?

---

### Post by oiad on 2009-08-10
Bump

---

