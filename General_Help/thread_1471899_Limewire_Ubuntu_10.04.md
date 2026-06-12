---
title: "Limewire Ubuntu 10.04"
date: 2010-05-03
forum: General Help
---

### Post by 81golfcaddy1 on 2010-05-03
I upgraded to 10.04 been using ubuntu for years and love it. but I can not get Limewire to work at all. I have tried all that I know which isn't much. like this [http://ubuntuforums.org/showthread.php?t=1466334](http://ubuntuforums.org/showthread.php?t=1466334) it worked for this guy but I am having issues still. I am still getting the same error.

---

### Post by gletob on 2010-05-03
What this guy did was:

Open up a terminal, and copy/paste these in in order pressing enter after each one.
```
 add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
then
```
sudo apt-get update
```
then
```
 sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Then try installing Limewire like normal.

---

### Post by CoreyB. on 2010-05-04
You could also try installing FrostWire instead.  I use the FrostWire from the GetDeb repository with openjdk and it works great.  If you are interested I will post back in greater detail.

---

### Post by Mychell on 2010-05-24
I got the same problem.

Thank you @gletob , it worked well :)

---

### Post by IncredibleStorm on 2010-07-17
I have been taking a look around for what P2P software I wanna use on this machine. Bare in mind, I am running Xubuntu on some hardware that really isn't fit to run. LOL

I'm on a neverending quest to reduce the resources used. I got plenty of HD space, but 256Mb of ram and a 1Gh>proc have made it slow going. However, I have enough bandwidth, lol.....go figure. 

Vuze has been useless for me, I started peeking at limewire again (just getting back to working with Linux). I had been under the impression that limewire was piggybacking on the gno/gnutella protocols. However, I haven't had any decent results from there in a long while. Again, I had assumed that Limewire was doing something to block searches. At any rate, their client is WAY heavier and slower than it needs to be. 

I'm checking out this "Frostwire" bit, because I'd gladly even HELP if software means not being taken advantage of. Pffft, Gator, Limewire used to MAKE you install Gator and all of THAT adware. LOL. 

Thanks again for the Frostwire hint. I'll try to get back about my results. 

Oh, Xubuntu 10.04 Lucid Lynx.....although, with Xubuntu it IS a bit more like a kitty cat. LOL

---

### Post by IncredibleStorm on 2010-07-17
Frostwire looks like it's running the same interface from limewire from a couple versions back. 

I will take my risks with limewire, but mostly just because I haven't found a decent way to limit searching by file size with that interface. 

Naturally, people have designed protocol stacks to issue false responses for ANY search that someone does. I've just found that most of them are under 20mb, so I generally search above that size.

---

### Post by DinosaursBark on 2010-08-27
I can't install the package because, apparently, I have another application running. I don't think I do.. So I restarted the computer and tried to download it again and the same problem came up. Help??

---

### Post by linux18 on 2010-08-27
> **DinosaursBark said:**
> I can't install the package because, apparently, I have another application running. I don't think I do.. So I restarted the computer and tried to download it again and the same problem came up. Help??
run this:

sudo killall synaptic || sudo killall aptitude || sudo killall mintinstall || sudo killall software-center
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo chmod 755 /usr/bin/dpkg && sudo apt-get upgrade dpkg
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade

---

