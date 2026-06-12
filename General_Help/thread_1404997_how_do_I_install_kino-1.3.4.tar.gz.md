---
title: "how do I install kino-1.3.4.tar.gz"
date: 2010-02-12
forum: General Help
---

### Post by charonred on 2010-02-12
I've just downloaded the latest build of Kino, but can't figure out how to install the package kino-1.3.4.tar.gz

I already have kino-1.3.3 installed via synaptic, but it won't export h264 to mp4 ([see here]("http://ubuntuforums.org/showthread.php?p=8813363")), so I'm hoping the latest build may fix it.

---

### Post by elliotn on 2010-02-12
Read the read me
File or or the install text file in the archive

---

### Post by charonred on 2010-02-12
been through that but can't make much out of it; all referred files seem to be installed according to Synaptic, but it's the 
```
./configure 
make 
make install
``` 
that doesn't seem to work correctly in Terminal - I'm just not that familiar with that aspect of using Linux.

From what I can make of it Kino is set to use it's own version of ffmpeg, but needs to use the shared (restricted) version - but I need step by step to do that.

In Hardy all I did was install Kino and the restricted drivers etc from Medibuntu and I could edit my video files like Movie Maker in Windows; but after migrating to Karmic and installing Kino (and all restricted packages), the h264export to mp4 just doesn't happen - so I'm trying to fix Kino, but with limited Linux know-how, I'm not doing very well.

---

### Post by IcarusR on 2010-02-12
Need to install 'build-essentail' package, (contains compiler etc) to compile packages.
In terminal type the following.

```
build-essentail
```

Then extract tarball 

```
tar xvjf tarball.tar.bz2
```

```
cd /to/extracted/folder/
```

Then you can run the commands listed in the readme....

```
./configure 
make 
make install
```

This will not install any dependancies, need to install them separately.

---

### Post by charonred on 2010-02-12
ok did this 
```
sudo apt-get install build-essential
```
 and that seems to be fine, but after extracting kino-1.3.4, then changing to the extracted folder, and doing this
```
./configure 
make 
make install
```
It  seemed to get nearly all the way through, but I got this at the very end of script
```
checking for intltool-update... no
checking for intltool-merge... no
checking for intltool-extract... no
configure: error: The intltool scripts were not found. Please install intltool.
mypc:~/tarsrc/kino-1.3.4$ make 
make: *** No targets specified and no makefile found.  Stop.
mypc:~/tarsrc/kino-1.3.4$ make install

```
as far as I can tell via Synaptic 'intltool' is installed, so don't know what I'm doing wrong 

.

---

### Post by charonred on 2010-02-12
bump

---

### Post by charonred on 2010-02-14
bump 2

---

### Post by gmargo on 2010-02-15
Are you sure **intltool** is installed?  No offense intended, but are you interpreting Synaptic correctly?  (The box in the S column should be green.)

Or check via the command line (this is the current version on Karmic):
```

$ **dpkg -l intltool**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
ii  intltool                0.41.0-0ubuntu1         Utility scripts for internationalizing XML

```

---

### Post by charonred on 2010-02-15
thanks, I double checked Synaptic and intltool-debian was installed, but not intltool; now it is, but I may leave installing latest version of Kino as have existing version now exporting to mp4 thanks to fakeoutdoorsman writing [new ffmpeg_h264.sh]("http://ubuntuforums.org/showpost.php?p=8825897&postcount=19") for Kino in Karmic; so will see how it goes.

---

### Post by teledyn on 2010-03-08
is it possible to build the package using dpkg-buildpackage?  I am constrained by my ATI graphics card to use Hardy and need to create a kino for 8.04

---

### Post by charonred on 2010-03-08
I didn't have a problem with Kino in Hardy, I just installed Kino via Synaptic and it worked, my problem was with Kino after after migrating to Karmic.

But after seeing that Kino has had no development for a couple of years, and is unlikely to have any further, I'm now playing with kdenlive instead which has no problem identifying and capturing from my JVC mini-dv, though it seems a lot more complex and will take some getting used to.

---

### Post by marcellux on 2010-04-16
> **gmargo said:**
> Are you sure **intltool** is installed?  No offense intended, but are you interpreting Synaptic correctly?  (The box in the S column should be green.)

Or check via the command line (this is the current version on Karmic):
```

$ **dpkg -l intltool**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-======
ii  intltool                0.41.0-0ubuntu1         Utility scripts for internationalizing XML

```

*************************************************************************

I have the same problem! also using koala karmic, build essentials are up to date, initltool is properly installed, but when I type "MAKE" I get following message:

"
make: *** No targets specified and no makefile found.  Stop." 

and this is happening with tar.gz and tar.bz2

---

### Post by charonred on 2010-04-16
I reposted this because of a problem I had with Kino (using the Kino installed by Synaptic)

start reading here
[http://ubuntuforums.org/showthread.php?t=1404228](http://ubuntuforums.org/showthread.php?t=1404228)

solution at gets Kino exporting to H.264 (single pass), but I'm now using kdenlive instead of Kino for video editing

---

