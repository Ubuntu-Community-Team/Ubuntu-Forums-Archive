---
title: "Ubuntu Keeps Crashing"
date: 2009-11-07
forum: General Help
---

### Post by PostChache on 2009-11-07
Okay, for some reason Ubuntu keeps freezing for no apparent reason! The programs I have open when it crashes is Firefox, Skype, Pidgin. Pidgin has been open every time it crashes but I don't know if it's the cause of it. 

I'm using 9.04 64bit

---

### Post by garvinrick4 on 2009-11-07
For starters uninstall all three from synaptic or terminal which ever easiest.

Then code:
              sudo apt-get clean

Then install all three from synaptic or Terminal which ever you want.

Will at least get you new downloads of each, the ones in cache might be defective who knows.

If works great if doesn't at least you know it is not the Apps themselves. 

In boot up have three different kernals of Linux, try booting with another one.

I am just saying to eliminate possibilities.  You get the my what I mean.
Post what your fix was.

Have you just downloaded on of the programs recently?
You can usually get to the root of the problem or at least eliminate some reasons.

---

### Post by skylark on 2009-11-07
You should also try and eliminate possible hardware causes.

First test your RAM using a tool like [**_memtest86+_**]("http://www.memtest.org/") (you can do the test by booting up with a Ubuntu live-cd and selecting the memory/ram test option).

Second do a system stress test of some sort. Maybe use the [**_stress linux distro_**]("http://www.stresslinux.org/").

If you experience any errors/lockups with these sort of independent tests then most likely you have a hardware fault (RAM, flaky power-supply or faulty motherboard are all possible). Also worth checking if you have overclocked your CPU or RAM as this can affect system stability.

If your system has no problem with these tests then you probably have an issue specific to your Ubuntu install.

A test that is easy to carry out to make sure your install has not been corrupted:
```
sudo apt-get install debsums
debsums | grep FAILED
```
This tests the integrity of installed packages. Ignore any "*.desktop" files that fail the test however (and any packagese with missing md5sums).

If you have lots of corrupt packages then something is causing your filesystem to become corrupt or there was some sort of data-corruption associated with the media/device you used to install Ubuntu.

---

### Post by PostChache on 2009-11-07
Okay I've uninstalled and reinstalled the programs! Hopefully that'll fix it. I also did that debsums and only 1 thing showed up 

```
 /usr/lib/openoffice/basis3.0/share/config/javasettingsunokpginstall.xml 
```

If it does it again I'm going to do the thing with the live CD

---

### Post by PostChache on 2009-11-10
Okay after running  [**_memtest86+_**]("http://www.memtest.org/") and getting no errors my computer is still crashing... I think it might have something to do with Flash Player? So I reinstalled it and it was working for a while then it crashed again. It only crashes when I have Firefox open and I've uninstalled and reinstalled it.

---

