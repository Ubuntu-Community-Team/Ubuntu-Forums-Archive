---
title: "DVDs not playing"
date: 2010-03-24
forum: General Help
---

### Post by thomasthefinch on 2010-03-24
I tried watching the Sopranos DVD earlier, and it said Disc could not be read, so I downloaded VLC and tried that, and that said file not found, for everything.  Then I tried different DVDs and they all did the same thing.

Anyone any the wiser?  Is it a driver issue?

---

### Post by nitstorm on 2010-03-24
tried downloading the libdvdcss package from the synaptic manager?

---

### Post by thomasthefinch on 2010-03-24
> **nitstorm said:**
> tried downloading the libdvdcss package from the synaptic manager?


Nope.  I'm a linux noob, how would I go about doing that?

---

### Post by coffeecat on 2010-03-24
> **nitstorm said:**
> tried downloading the libdvdcss package from the synaptic manager?

Except that you need to enable the Medibuntu repository first.

@thomasthefinch, have a look here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the link for the repository howto to add Medibuntu to your sources. Then open Synaptic and libdvdcss2 (which you need to decrypt commercial DVDs) will be available for download and installation.

You may also need the library libdvdread4, so mark that as well if it isn't already installed. In fact, while you're about it, mark ubuntu-restricted-extras for installation which gives you a lot of multimedia goodies that you might need at some point.

---

### Post by 2hot6ft2 on 2010-03-24
You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube.... let's just cut to the end and install it all at once so you can play pretty much everything. What do you think?

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these 2 commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then for all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```

And you're done.
VLC Player will be in Applications > Sound and Video > VLC

---

### Post by nitstorm on 2010-03-24
<edited coz i was too slow to type and was a bit wrong>

---

### Post by thomasthefinch on 2010-03-24
> **2hot6ft2 said:**
> You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube.... let's just cut to the end and install it all at once so you can play pretty much everything. What do you think?

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these 2 commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```then for all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```And you're done.
VLC Player will be in Applications > Sound and Video > VLC

Thanks very much, this is the solutions that worked :)

But all of the other stuff was working before, youtube etc, java

---

### Post by 2hot6ft2 on 2010-03-24
> **thomasthefinch said:**
> Thanks very much, this is the solutions that worked :)

But all of the other stuff was working before, youtube etc, java
Welcome. Glad it helped. You could have just installed the libdvdcss2 codec to just make dvds play then but I still think that comes from the medibuntu repositories so you would have still had to enable them.

---

### Post by thomasthefinch on 2010-03-25
> **2hot6ft2 said:**
> Welcome. Glad it helped. You could have just installed the libdvdcss2 codec to just make dvds play then but I still think that comes from the medibuntu repositories so you would have still had to enable them.


The plot thickens!

I switched my computer off last night, started it this morning, and it's doing the same thing it did yesterday, but I've tried reinstalling those things that people posted, and nothing, it still doesn't work.

But this time it isn't registering the dvd.  It doesn't acknowlege there is something in the drive by asking me how I want to open it.

---

### Post by bhakeman on 2010-03-25
> **nitstorm said:**
> tried downloading the libdvdcss package from the synaptic manager?

I get an error message:

E: tff-mscorefonts-istaller: subprocess installed post-installation script returned error exit status 1

details also said that andale32.exe: Failed open or read
sha256sum:  warning: 1 of 1 listed file could not be read 
checksum mismatch for andale32.exe, abortin1
dpkg:  error processing ttf-mscorefonts-installer (--configure):
subprocess installed post-installation script returned error exit status 1
errors were encountered while processing:
ttf-mscorefonts-installer

---

### Post by coffeecat on 2010-03-25
> **bhakeman said:**
> I get an error message:

E: tff-mscorefonts-istaller: subprocess installed post-installation script returned error exit status 1

details also said that andale32.exe: Failed open or read
sha256sum:  warning: 1 of 1 listed file could not be read 
checksum mismatch for andale32.exe, abortin1
dpkg:  error processing ttf-mscorefonts-installer (--configure):
subprocess installed post-installation script returned error exit status 1
errors were encountered while processing:
ttf-mscorefonts-installer

This is not related to the OP's problem and is an issue with the ttf-mscorefonts-installer package. I guess you tried to install ubuntu-restricted-extras which includes the mscorefonts installer. See this bug report:

[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

I suggest you open your own thread if you need help.

---

### Post by wojox on 2010-03-25
Just go to System-> Administration->Synaptic Package Manager and search for "ttf-mscorefonts-installer" and make a right click and choose option "Mark for Complete Removal" and click on "Apply "

---

