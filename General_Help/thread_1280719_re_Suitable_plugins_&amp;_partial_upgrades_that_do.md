---
title: "re: Suitable plugins &amp; partial upgrades that don't"
date: 2009-10-02
forum: General Help
---

### Post by JesseJones on 2009-10-02
Hi all, I've been using Ubuntu on another (crappier) system for about 6 months now. I'm not really overly Linux savvy but I hate Microsoft and being virus free really does appeal to me. anyway long story short, bought a new comp off my sister, Installed Ubuntu Jaunty Jack. Then when I copied my music library onto my comp and tried to play it in rhythm box I get the error:  


**Search for suitable plugin?**
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

-So I select "search"

**No packages with the requested plugins found**
The requested plugins are:

MPEG-1 Layer 3 (MP3) decoder

Any help?

Also when I first installed and the system updates manager appeared for the first time it said "too many new updates to install please do a partial upgrade" So I would click update and some nice little menus and bars would appear making it seem as though it was upgrading

and I get a message that says :

Do you want to start the upgrade?

Details: Remove Linux-generic
Install linux-headers-2.6.28-15
Install linux-headers-2.6.28-15-generic
Install linux-image-2.6.28-15-generic
Upgrade linux-headers-generic
Upgrade linux-image-generic

I click start upgrade and the manager closes, nothing happens. If I re-open the manager then I have to start the whole process overagain.

Please help!

Thankyou.
J.

---

### Post by Giblet5 on 2009-10-02
Open a terminal and do it the manual way:
```
sudo apt-get update
sudo apt-get upgrade
```

(The servers are seriously overloaded today, due to 9.10 beta last night, so you may want to wait a couple of days)

As for the audio codec issues, many of the really useful ones, eg gstreamer, lame, etc, don't install by default for legal, commercial, DMCA, and other stupid reasons.

```
sudo apt-get install ubuntu-restricted-extras
```
will install most of what you'll need.

---

### Post by JesseJones on 2009-10-02
I tried the code for the suitable plug in but no dice,

jesse@jesse:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

---

### Post by Giblet5 on 2009-10-02
In synaptic, edit your repositories and enable the Ubuntu restricted repository, then reload and try again.

---

### Post by Giblet5 on 2009-10-02
This installs a LOT of good stuff. You'll be glad. Unless I left out a step again. ;)

---

### Post by jward3010 on 2009-10-02
> **Giblet5 said:**
> (The servers are seriously overloaded today, due to 9.10 beta last night, so you may want to wait a couple of days)
Or if you want, in Software Sources pick a different repository. Might not be as loaded.

If you want to install support for MP3, WMA, MOV, AVI, DIVX, DVD playback etc. get the package called "ubuntu-restricted-extras".

First go to medibuntu site ([www.medibuntu.org](www.medibuntu.org)). See the instructions for adding that software source (Repository Howto), then in a terminal type:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by JesseJones on 2009-10-02
@ Giblet5 I tried both codes and both seemed to work. Meaning they both downloaded and seemed to install (after I unlocked the repositories in synaptic)  but when I open Rythem box and try to play a song I get the exact same problem. And when I open update manager it still says " too many updates to install run a partial upgrade"

i kept the log from terminal if it will help i can post it but its pretty long.

@jward followed the link typed in the code to get Medibuntu

i wont post the whole log but there were a bunch of errors @ the end of it:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

Thanks for the help guys anymore ideas?

---

### Post by jward3010 on 2009-10-02
1. This could be a current problem with overloaded servers at the moment as Ubuntu 9.10 BETA has just been released, not unusual.
2. Try the following:

Firstly:```
sudo apt-get update
```
Above should complete without problems. If it has problems assume overloaded servers or your connection. If not your connection read bottom.

Then try..
```
sudo apt-get dist-upgrade
```
This will do the updates that are being held back.

If there are problems with downloading any of the files try a different repository. Go into "Software sources" and pick Ireland for example, my updates came through fine today and I got the 9.10 ISO at full speed - and it's a 20Gb fibre connection! Plenty of overhead.

---

### Post by JesseJones on 2009-10-02
okay I followed your steps and it worked, I restarted my comp and when I opend update manager it said system up to date. THANKS!!!

however I still cant seem to get any media working. After updating I tried the code sudo apt-get install ubuntu-restricted-extras and I got:

jesse@jesse:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil-unstripped-49 libxvidcore4 linux-headers-2.6.28-11 libx264-65
  linux-headers-2.6.28-11-generic libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jesse@jesse:~$ 

help???

(ps Im going on a very long roadtrip in 2 hours if I dont get this solved it means no tunes for a very, very long time -_-)

---

### Post by jward3010 on 2009-10-02
Ok, try this for broken dependencies:
```
sudo apt-get check
```

---

### Post by jward3010 on 2009-10-02
If you don't manage to get it working install VLC, it'll play anything.
```
sudo apt-get install vlc
```

---

### Post by JesseJones on 2009-10-02
okay I did:

jesse@jesse:~$ sudo apt-get check
[sudo] password for jesse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jesse@jesse:~$ 


now what? Should I try the: sudo apt-get install ubuntu-restricted-extras

again?

---

### Post by JesseJones on 2009-10-02
ugh, sorry for double posting but i didnt notice your post about VIC before. I tried to get the other one and then I tried VIC neither will work!

jesse@jesse:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.9a-2ubuntu1) but it is not going to be installed
       Depends: libqtgui4 (>= 4.5.0~+rc1) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libtar but it is not installable
E: Broken packages


Sorry for being a pain, and thanks alot for your help... any other ideas?

---

### Post by jward3010 on 2009-10-02
How many times did you try installing - just the once? If so try again, I'm thinking the servers are jammed and download requests are being timed out all the time.

But as to why Rhythmbox can't implement the codecs is very strange. I think you can run Rhythmbox in a verbose way from the terminal (i.e. you run it from terminal, the program starts as normal but the terminal in the background shows any errors that occur like missing gstreamer or something). I'll try find that out. 

Also try:
```
sudo apt-get install gstreamer0.10-plugins-ugly (something like that - maybe search in package manager)
```
This gstreamer package is the one that contains the MP3 codecs as far as I know, and maybe it's unusually missing - although I wouldn't be surprised at all if it says "You have latest version".

---

### Post by jward3010 on 2009-10-02
I still think you have a broken packages problem somewhere - although I'm surprised "apt" isn't saying it to you. Open terminal and type:
```
sudo dpkg --configure -f
```
and then
```
sudo apt-get install -f
```
These commands should run through any unmet dependencies, any broken unfinished apt jobs etc. If you get results from running these commands then try installing vlc again after that.

It's a pity someone with more apt and Rhythmbox experience isn't looking at this post, there's probably easier ways to figure out if something is fully installed or not.

---

### Post by JesseJones on 2009-10-05
Sorry I was out of town for the weekend.

so I tried (sudo dpkg --configure -f) and I wasn't really sure where to go from here:

jesse@jesse:~$ sudo dpkg --configure -f
dpkg: conflicting actions -f (--field) and -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jesse@jesse:~$ 



Also that other code you gave me didn't tell me I had the latest version


sudo apt-get install gstreamer0.10-plugins-ugly

jesse@jesse:~$ sudo apt-get install gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate
jesse@jesse:~$ 

when I got home I also retried all the solutions you gave me before only to be met with the same results.

---

### Post by jward3010 on 2009-10-05
Damn it to hell, I gave you the wrong command, its:
```
sudo dpkg --configure **-a**
```

---

### Post by JesseJones on 2009-10-05
all right I tried sudo dpkg --configure -a

all I got was:
jesse@jesse:~$ sudo dpkg --configure -a
[sudo] password for jesse: 
jesse@jesse:~$

then I tried 
sudo apt-get install -f:

jesse@jesse:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil-unstripped-49 libxvidcore4 linux-headers-2.6.28-11 libx264-65
  linux-headers-2.6.28-11-generic libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jesse@jesse:~$


Still nothing -_- I'm starting to think I should just re-install

---

### Post by jward3010 on 2009-10-05
I'm now trying to look around for rhythmbox config files with the idea of clearing them out and causing rhythmbox to regenerate and start again. But not with much luck, I think you have a slightly sick system bearing in mind you can't get VLC either. 

Anyone else around here with apt-get or Rhythmbox knowledge, come on, HELP THIS DUDE!

---

### Post by JesseJones on 2009-10-15
Ummm.... bump?

please someone help! I just don't know what to do, I don't want to go back to windows but I cant live without music.

---

### Post by jward3010 on 2009-10-16
Could you post one of the tracks your having trouble with, and also tell us what formats your exactly trying to play.

Also I found the a command you can run to test.

Firstly install:
```
sudo apt-get install gstreamer0.10-tools
```

then try:
```
gst-launch-0.10 --tags playbin uri=file:///directory/example
```

If the song plays it's a possible Rhythmbox issue.

---

