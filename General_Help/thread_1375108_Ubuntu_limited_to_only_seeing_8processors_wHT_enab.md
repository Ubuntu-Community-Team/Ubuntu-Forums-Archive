---
title: "Ubuntu limited to only seeing 8processors w/HT enabled"
date: 2010-01-07
forum: General Help
---

### Post by buffalosolja on 2010-01-07
Sorry to be asking this but I have installed Ubuntu like 5x (different versions) to see if it is able to see my 2-Xeon processors with Hyperthreading enabled.  Only reason I am asking is because my fedora disk is able to see the 16.  Is there something I can do for this, if not oh well I just love Ubunu's setup and would like to get the maximum benefit for the hardware I have.

---

### Post by llawwehttam on 2010-01-07
Firstly are those xeons 64-bit and if so are you using the 64 bit version. I used ubuntu on xeons last year and it didn't go too well.

---

### Post by llawwehttam on 2010-01-07
sorry, forgot in the last post. Could you post the output of ```
cat /proc/cpuinfo
```

then I may be able to help you further

---

### Post by llawwehttam on 2010-01-07
Just to add another option i found this thread [http://ubuntuforums.org/showthread.php?t=556602](http://ubuntuforums.org/showthread.php?t=556602) which is similar.

It seems 8 cores is the max in ubuntu and you need to compile your own kernel to use more.
Hope this helps.

---

### Post by buffalosolja on 2010-01-08
thanks big guy understand its free, and I will on monday when I go in (cat the cpu and all)  again I love linux :)

---

