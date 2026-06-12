---
title: "Strange problems with Jaunty, not with Hardy"
date: 2009-08-31
forum: General Help
---

### Post by HANGBELLY on 2009-08-31
I started using Ubuntu about three years ago, but you can still call me a dumb user. I've had good success with the os and haven't had any major difficulties, thanks to using the books, "Beginning Ubuntu" and "Hacking Ubuntu" and the on-line forums.  But now, I've run into a problem that I've never seen before. I ordered the 8.04 "Hardy" cd and installed it on a (don't laugh) (ok laugh just don't point), a Dell CPt laptop (512 ram and a 500Mhz processor). This has been my workhorse for a while doing everything from e-mail, to editing sd video. I moved to 9.04 "Jaunty" so I could get a faster load time, and Kdenlive straight from the repositories. Again, no problems, everything reconised and working. Last week I joined the 21st centry and bought a Dell D505 laptop with a Pentium M processor and 1 gig of ram. I misplaced my "Jaunty" cd, so I burned another one, loaded it into the new laptop and fired it up. Once again everything worked out of the box so I downloaded the updates and went to install the applications I had on my old laptop. 
  Here's where I started having problems. When I tried to download, Kdenlive, ffmpeg, dvgrab, Hugin panorama maker, and anything related to codecs, I got the message, " There are programs installed on your system which prevent the installation of the applications. Check synaptic package manager to solve this" I checked synaptic and saw I had broken files. I removed then,tried to reintall the applications with the same results.
     I got my "Hardy" cd out and did a fresh install. Everthing works fine, all codecs, ffmpeg, dvgrab loaded and works just like my old system did. The only exception is Hugin panorama maker which still says " There are programs which conflict with this application. Check synaptic". 
    Am I missing something? I did everything just like I did before on my old system and I wouldn't have expected any problems. I also find it unusual that all the problems are related to codecs, Kdenlive, and Hugin, at least where Jaunty is concerned. Hardy, runs all the codecs but dosen't run Hugin. With a little more experience I might be able to solve this, but I'm still just a dumb user. 
   If anyone has any advice, please let me know.
                                                     Thanks.

---

### Post by zvacet on 2009-08-31
If you get message that you have brokenpackages you should fix then in synaptic or type in terminal

```
sudo apt-get -f install
```

---

