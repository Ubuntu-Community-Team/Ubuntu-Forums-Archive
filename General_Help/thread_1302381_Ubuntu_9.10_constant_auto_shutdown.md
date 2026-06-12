---
title: "Ubuntu 9.10 constant auto shutdown"
date: 2009-10-27
forum: General Help
---

### Post by razorboy5 on 2009-10-27
Hi

I've had this problem with 9.04 but not very severe
until earlier today i've been using Ubuntu 9.04 sometimes it would shutdown once in a blue moon due to overheating

i understand that this is a good thing (for security purposes) but as soon as i installed 9.10 release candidate it keeps shutting off like 30-50min after booting.

does that mean my computer works harder to run 9.10? or the security limit on the 9.10 is lower? can i disable this feature?

thx

---

### Post by psycho5 on 2009-10-27
Um, what you really need to do is check your thermal paste for your processor, it might need replacing. The problem is your PC is overheating not that Ubuntu is shutting down.

---

### Post by razorboy5 on 2009-10-27
so its a hardware issue rather than software issue?

i figured it might be software since it started happening right after i made the switch :S

---

### Post by philinux on 2009-10-27
```
sudo apt-get install hardinfo
```

Then look under Apps>System tools>System Profiler and Benchmark

Run it and scroll down to Devices>Sensors. Have a look at the cpu core temps.

---

### Post by razorboy5 on 2009-10-27
daniel@daniel-gateway:~$ sudo apt-get install hardinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hardinfo


another thing with RC is that i can't install anything, not from software centre or synaptic

i'll try again in 2 days or so when 9.10 officially launches

---

### Post by philinux on 2009-10-27
Post your sources list.

```
cat /etc/apt/sources.list
```

---

### Post by P4man on 2009-10-27
can you check if your cpu fan is running?
Overheating is very much a hardware issue (and a serious one you should solve it ASAP), but it could be a problem with the acpi and your fans not running. What machine is it?

---

### Post by razorboy5 on 2009-10-27
it's a laptop

Gateway M6874h, just had it in the shop a month ago or so for overheating and they said they replaced the fans

```

daniel@daniel-gateway:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release Candidate i386 (20091020.3)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```also got hardinfo working

devices>sensors shows

TZ00 57 celcius

edit: jumped up to 59 celcius

up to 63 celcius

---

### Post by razorboy5 on 2009-10-27
i've seen it go up to 70 celcius atm

however i finally got to install my graphics driver (was practically impossible cuz it kept shutting down midway)

after driver has been installed temperature usually floats around 54-60

and has not shut itself off yet

is that a solution?

---

### Post by P4man on 2009-10-28
laptop cpu's wouldnt shut down at such temps. Their critical temperature is usually around 90-100C. Keep monitoring those temps

I also wasnt implying necessarily a faulty cpu fan. Ive seen laptops with a buggy bios where the fan works on some versions of windows (ones they are shipped with) but not with other operating systems (which can usually be fixed). Please make sure it actually runs. Try running some cpu intensive apps, and monitor your temps and listen/feel if the fans actually spin or not.

---

### Post by razorboy5 on 2009-10-28
yes

i didn't hear my fan necessarily,
usually it's a very loud fan compared to all my friend's laptops

will keep monitor the temp

---

