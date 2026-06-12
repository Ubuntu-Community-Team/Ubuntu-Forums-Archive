---
title: "How to: Electricsheep Screensaver 2.7 in Jaunty (9.04)"
date: 2009-07-02
forum: General Help
---

### Post by omegamike3 on 2009-07-02
As some of you may have noticed, the server for electricsheep 2.6 (default version in 9.04) has been shut down, which means no more new sheep! On the [official site]("http://electricsheep.org"), they do have a link to a [script]("http://electricsheep.org/makesheep.sh") for handling the dependencies and compiling the latest version, however I haven't been having much luck with it. There is also a PPA available from electricsheep but they currently only have versions ready for 8.04 and 8.10, though they say there should soon be versions for 9.04.
Luckily, I've come across the surfed PPA which currently has the newest versions of flam3 and electricsheep since I'm impatient. :D

What you'll need to do:

Edit your sources by either opening:
```
/etc/apt/sources.list
```
in your favorite editor (you'll need to be root/use sudo) or by going to System > Administration > Software Sources and then adding the following sources:

```
deb http://ppa.launchpad.net/surfed/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/surfed/ppa/ubuntu jaunty main 
```

You can then either add the key by downloading it, or just do it the quick way and paste this into a terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EDFCDC98
```

Click on Close and Reload if you're using the GUI or just run a:
```
sudo apt-get update
```
and the updates should become available to you if you already have electricsheep installed. If not, either search for it in Synaptic or install by running:
```
sudo apt-get install electricsheep
```


Hopefully this keeps all you shepherds out there happy. Yay new sheep! :D

---

### Post by mvaniersel on 2009-07-04
Here is another method. Today I installed electric sheep on Ubuntu 9.04 using the instructions here: [http://community.sheepserver.net/node/51](http://community.sheepserver.net/node/51)
The makesheep.sh script basically works, it is just missing a dependency: libavformat-dev. To make it work with makesheep.sh, all you have to do is

```
sudo apt-get install libavformat-dev
```

Then you can proceed according to the official instructions

```
wget electricsheep.org/makesheep.sh
sh makesheep.sh
```

---

### Post by spotspot on 2009-07-08
> **mvaniersel said:**
> Here is another method. Today I installed electric sheep on Ubuntu 9.04 using the instructions here: [http://community.sheepserver.net/node/51](http://community.sheepserver.net/node/51)
The makesheep.sh script basically works, it is just missing a dependency: libavformat-dev. To make it work with makesheep.sh, all you have to do is

```
sudo apt-get install libavformat-dev
```

Then you can proceed according to the official instructions

```
wget electricsheep.org/makesheep.sh
sh makesheep.sh
```

thanks, i updated the script.  i also checked in some more fixes.  everyone: please pass on fixes to electric sheep to me by email or on our forum!

[http://community.sheepserver.net/node/51](http://community.sheepserver.net/node/51)

---

### Post by spotspot on 2009-07-08
Also: 9.04 binaries should be out soon, after i get back from this trip.

And: please please please we need help getting this package into debian or ubuntu standard! our package maintainer quit!

---

### Post by ntrgc89 on 2009-07-11
Sry to bump a post with a not particularly relevant addition, but I just installed electric sheep on my jaunty laptop, and when I launch it I get the following messages:

$ electricsheep
please be patient while the first sheep is downloaded...
curl: (7) couldn't connect to host
lost contact with v2d6.sheepsever.net, cannot retrieve sheep.

It's not working on my Windows 7 machine either, and the website (community.sheepserver.net) won't load. It appears to be down, is it just scheduled maintenance?

Is anyone else having these issues?

---

### Post by phinullfermata on 2009-07-30
I'm having this exact problem as well.

---

### Post by CKDewey on 2009-08-11
According to [http://community.electricsheep.org/node/211](http://community.electricsheep.org/node/211) the server is down and the problem will be resolved soon. 

After making electricsheep appear under 'Fractals' in 'Screen Saver Settings' from the fix at [http://n0t3s.wordpress.com/2009/05/06/electricsheep-and-kde/](http://n0t3s.wordpress.com/2009/05/06/electricsheep-and-kde/) , I downloaded three sheep AVIs from [http://v2d7c.sheepserver.net/cgi/status.cgi](http://v2d7c.sheepserver.net/cgi/status.cgi) and placed them in ~/.electricsheep .

Now it works in Settings but not when invoked as a module.

---

### Post by spotspot on 2009-08-16
The 2.7 server is back but the 2.6 version is obsolete and won't be returning.

---

### Post by M!SF!TS on 2009-09-02
I ran this: sudo apt-get install libavformat-dev

and got this...

nick@linux-box:~$ sudo apt-get install libavformat-dev
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat-dev: Depends: libavcodec-dev (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed
E: Broken packages



its not working for me :(

---

### Post by mikeym on 2009-09-20
The guide to compiling it yourself on [http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51) has a post which recommends running (for jaunty):

```
sudo apt-get install libavutil49
sudo apt-get install libavcodec-dev
sudo apt-get install libavformat-dev
sh makesheep.sh
```

Unfortunately that put me into dependency hell as I have *libavutil-unstriped-49* installed and the devs clash horribly with it and it wants to uninstall half my system to switch package. 

I eventually got it compiled but had to break my package tree temporarily first. See [here]("http://ubuntuforums.org/showthread.php?t=1270861").

Note once I'd made the program I installed it with chekcinstall:

```
sudo apt-get install checkinstall
```

And changing into the folder and running checkinstall

```
cd electricsheep*
cd client
sudo checkinstall

```

change the long (repeated) version number to just the version number once and then *-svn* and then I did the date without spaces. Like:

*2.7b12-svn20090920* 

and change the package name to *electricsheep*. 

Seemed to work but the PPA linked above will be much easier if it works.

Also has anyone got gnome-screensaver working so that you can vote on sheep?

---

### Post by green0eggs on 2009-12-09
Err this post does not strictly live under this topic (since I'm on 8.10): I get the error:

```

abc@abcde:~$ electricsheep
please be patient while the first sheep is downloaded...
curl: (6) Couldn't resolve host 'v2d6.sheepserver.net'
lost contact with v2d6.sheepserver.net, cannot retrieve sheep.

```

but I'm using Intrepid 8.10

what is the solution to this? I've read that I need to compile from source?!... but I'm pretty much a noob so I'd be very grateful if someone could explain this in dummy dummy language.

---

