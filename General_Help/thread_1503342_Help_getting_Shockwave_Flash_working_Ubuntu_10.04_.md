---
title: "Help getting Shockwave Flash working Ubuntu 10.04 64 bit"
date: 2010-06-06
forum: General Help
---

### Post by Terethian on 2010-06-06
Help getting Shockwave Flash working Ubuntu 10.04 64 bit

Okay, I am using firefox and I was unable to click the youtube videos and move the video cursor around so I tried to fix it... I have the 64 bit version. I tried using every install from the adobe web site, apt fails saying it's not virtual, deb fails, rpm fails etc.

I also downloaded the libflashplayer.so 10.1 pre-release and I cannot copy paste it into the usr/lib/mozzilla/plugins cause apparently I don't have access, I know the user and password for root but I don't see any option where I can enter one... it just has a pop up saying NO you can't do that now click cancel and stare at the screen you moron.
(the window actually said that!!! just kidding.)

So I also tried the synaptech manager and kpackagekit. I tried uninstalling and reinstalling. No matter what I do however the addons in firefox list the version as 9.0 r999 and all I can do is disable that not really remove it.

I have that .so file so if all I have to do is somehow get it into the plugins folder.. great! how the heck can I get it to let me. 

Help! =(

---

### Post by Smart Viking on 2010-06-06
Hey, this is an irritating bug with 64 bit.

Tips to help you survive:

1. When you are in someone's channel, the buttons work
2. To adjust the volume, click on the sound thing, and then adjust with the arrow keys.
3. To go back and fourth in the video, press on the video to put it on focus, then use arrow keys
4. And last, but not least, the buttons work in full screen, and to get in full screen, click in the video, then press "f".

I hope that helped you a little. :)

EDIT: Forgot a more important one, "space" button to play a video. :)

---

### Post by wojox on 2010-06-06
See here [Flash Optimization by lovinglinux]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

Look at 64 bit. :)

---

### Post by Smart Viking on 2010-06-06
> **wojox said:**
> See here [Flash Optimization by lovinglinux]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

Look at 64 bit. :)

Thank you! I have heard other people talk about it on freenode without solutions, so i assumed it was just ment to be that way haha, thanks! :)

---

### Post by Terethian on 2010-06-06
I installed flash aid and I was able to get youtube videos working perfectly in fact with working controls........


but now facebook flash apps like farmville won't work at all. It now crashes the browser. My wife won't be happy on ubuntu unless she can use all the facebook apps so I had to swap back to the windows hard drive for now. =( 

so in short.....

flash-aid hasn't worked for me with 64-bit and facebook apps. 

Maybe I should just go to 32bit install of ubuntu? I am a new user and I really wanted a more up to date OS, I have been using XP for a long long time and my cpu is capable of 64bit but I have never used it since I was always using the 32bit xp. I was hoping to experience a boost and generally use a more up to date OS for free...

---

### Post by wojox on 2010-06-06
> **Terethian said:**
> I installed flash aid and I was able to get youtube videos working perfectly in fact with working controls........


but now facebook flash apps like farmville won't work at all. It now crashes the browser. My wife won't be happy on ubuntu unless she can use all the facebook apps so I had to swap back to the windows hard drive for now. =( 

so in short.....

flash-aid hasn't worked for me with 64-bit and facebook apps. 

Maybe I should just go to 32bit install of ubuntu? I am a new user and I really wanted a more up to date OS, I have been using XP for a long long time and my cpu is capable of 64bit but I have never used it since I was always using the 32bit xp. I was hoping to experience a boost and generally use a more up to date OS for free...


```

sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
rm -f libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz

```


This has nothing to do with flash-aid.


> hoping to experience a boost

You really won't notice a boost between 64 vs. 32 bit.

---

### Post by Terethian on 2010-06-06
wojox: Ok I see there are two codes one for 32 bit and one for 64 bit.

As of right now I have youtube working GREAT but like i said facebook flash apps just crash firefox.

In a little bit I will reboot and try the 32 bit code listed and see if it makes a difference... if it doesn't i'll try the 64 bit one. If that doesn't work.... /shrug

---

### Post by sandyd on 2010-06-06
> **Terethian said:**
> Help getting Shockwave Flash working Ubuntu 10.04 64 bit

Okay, I am using firefox and I was unable to click the youtube videos and move the video cursor around so I tried to fix it... I have the 64 bit version. I tried using every install from the adobe web site, apt fails saying it's not virtual, deb fails, rpm fails etc.

I also downloaded the libflashplayer.so 10.1 pre-release and I cannot copy paste it into the usr/lib/mozzilla/plugins cause apparently I don't have access, I know the user and password for root but I don't see any option where I can enter one... it just has a pop up saying NO you can't do that now click cancel and stare at the screen you moron.
(the window actually said that!!! just kidding.)

So I also tried the synaptech manager and kpackagekit. I tried uninstalling and reinstalling. No matter what I do however the addons in firefox list the version as 9.0 r999 and all I can do is disable that not really remove it.

I have that .so file so if all I have to do is somehow get it into the plugins folder.. great! how the heck can I get it to let me. 

Help! =(
[[s]http://ubuntuforums.org/showthread.php?p=9378543#post9378543]("http://ubuntuforums.org/showthread.php?p=9378543#post9378543")

don't do if on 64bit[/s]

see signature (universal adobe tools)

---

### Post by rizzeh on 2010-06-06
Chromium browser on 64x plays youtube straight away, didnt have to do a thing :guitar:

---

### Post by Terethian on 2010-06-07
Well, after searching around (and since I didn't put a lot of effort porting things and making things in the OS) I decided to just go to a 32 bit install instead..... I do youtube videos as VGCodeMaster so when I noticed there is a Ubuntu studio version for video and audio I figured what the heck it could be interesting and helpful... So I installed Ubuntu studio 32 bit and was able to get facebook and youtube working great easily.

 I seem to be having some issues with my nvidia card driver but I am sure I can work it out. I went through installing it and I can't do the fancy window effects (even though in the 64 bit version I had no issues with this at all.) I don't really NEED these effects anyways but I would think the failure will effect other video editing as well down the road so I want to try to fix it. 

Ubuntu says the nvidia driver is installed so I will just have to keep looking into it.... So far I am feeling that squeaky clean feeling of a fresh OS and that feeling I had when I was a little kid that first started customizing his virtual space in windows 3.1... It's a pretty cool feeling to be able to kind of bring back since this is all a new learning experience!

:P

---

### Post by Sandertje on 2010-06-07
I've also had problems with flash on a 64bit linux OS. The trick was perform the following:
```
sudo gedit /usr/bin/nspluginwrapper/i386/linux/npviewer 
```
and then adding *BEFORE* the last line:
```
export GDK_NATIVE_WINDOWS=1
```

Save, and reboot the application that uses flash.

---

### Post by Terethian on 2010-06-07
Thanks. =)

I was also able to fix my nvidia drivers by simply removing them and reinstalling them. There was a wierd error the last time I tried to boot related to the drivers as I recall. I know I didn't do anything wrong... it just installed wrong in the first place and needed to be redone. 

Works GREAT now!  Facebook, videos, nvidia display drivers, everything is SNAPPY goodness.

---

### Post by dcstar on 2010-06-08
> **Terethian said:**
> Thanks. =)

I was also able to fix my nvidia drivers by simply removing them and reinstalling them. There was a wierd error the last time I tried to boot related to the drivers as I recall. I know I didn't do anything wrong... it just installed wrong in the first place and needed to be redone. 

Works GREAT now!  Facebook, videos, nvidia display drivers, everything is SNAPPY goodness.

So it's **solved**, is it?

---

### Post by Terethian on 2010-06-08
Well technically in Lieu of solving the problem with 64bit Ubuntu I started over fresh with 32bit which seems to have resolved all of my main issues... I highly recommend 32 bit and poo poo the 64 bit.

---

