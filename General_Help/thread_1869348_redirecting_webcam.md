---
title: "redirecting webcam"
date: 2011-10-25
forum: General Help
---

### Post by nuttycyclist on 2011-10-25
Can anybody help with this?  I've been using ubuntu for some time now, but am still a relative newbie when it comes to complex matters.  I am using ubuntu 10.04

I'm sure this is possible, but have not been able to work out how to do this.

I have a working webcam, and all is ok.  

Skype detects that I have just one camera, and works fine.  I have installed webcamstudio and that is working fine too.

/dev/video0   /dev/video1  /dev/video2  all exist at present; video0&video1 having been installed by webcamstudio, and video2 appears when the USB webcam is plugged in.  However Skype only shows the USB camera in its dropdown options for webcams.

What I'd like to do is to create a virtual webcam, which takes its output from webcamstudio, and then have skype take see this virtual webcam as a "real" camera for its input.

i.e. I want to be able to take advantage of the special effects within webcamstudio in order to manipulate the image shown in skype during a conversation.

Please can anybody provide simple instructions as to how to do this.

I think I need to 
a) create the new virtual webcam (/dev/video3 ?)
b) pipe webcamstudio output to new device somehow.  V4L2 somehow?

As I said, as a relative newcomer to complex tweaking like this, simple instructions would be appreciated; and I might need to ask for confirmation on some steps if I get stuck.

Thanks in advance.

---

### Post by dino99 on 2011-10-25
a thread about broadcasting

[http://ubuntuforums.org/showthread.php?t=1418586](http://ubuntuforums.org/showthread.php?t=1418586)

---

### Post by nuttycyclist on 2011-10-25
thanks for the reply :)    Unfortunately I'm still stuck :(

I don't think I'm after streaming to another machine, as per part 2 of that, and I certainly don't have usernames and passwords as in that example.


The first part though, possibly, is what I'm after having read the linked site ([http://www.lavrsen.dk/foswiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/foswiki/bin/view/Motion/VideoFourLinuxLoopbackDevice))

But...
that site says 
> 1) A simple example (all applications use the same resolution) Do  "modproble vloopback" then "resize /dev/video0 /dev/video1 320x240  320x240". Now, you can run as many webcam applications as you want with  input as /dev/video2 (however you might have to tell your application  the picture size, see below). 

modprobe vloopback on my machine gives me the following
> FATAL: Module vloopback not found.


I can't work out how to install this (sorry, I did say I was a bit of a newbie :$)  looking at my kernel I think I need what is referred to on that site as "svn trunk for kernel version >= 2.6.32 "

but when I follow the link for that site, can't see any source, nor can I add the "svn co [http://www.lavrsen.dk/svn/vloopback/trunk/](http://www.lavrsen.dk/svn/vloopback/trunk/) vloopback" as a repository.   

I've found and installed "vloopback-source" in the synaptic package manager, but that's not got me over my hurdle either as modprobe is still giving me module not found.   The "make insmod vloopback.ko" doesn't sense to me either, and when I tried it as a last ditch effort that gave me "make: *** No rule to make target `insmod'. Stop."


lastly, I'm getting the same error as that person on the other thread.  resize gives me "Usage: resize [-u] [-c] [-s [rows cols]]"


All in all, I'm stuck where I have been for the last two days.  Vague information on the tinterwebs, a belief that it should be possible, but no results.



Sorry to be thick, but any chance of a step by step guide?  Please?

---

### Post by nuttycyclist on 2011-10-25
Aahhh, hang on, found source on disk and associated README files....   investigating.

---

### Post by nuttycyclist on 2011-10-25
Nope, sorry, still stuck :(

> Essentially, you must download the vloopback source, as with kernel-package

Then you can run `module-assistant build <vloopback_source>`


What do I type in place of <vloopback_source>?

These are the files downloaded by package manager.
> 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/vloopback-source
/usr/share/doc/vloopback-source/FAQ
/usr/share/doc/vloopback-source/README
/usr/share/doc/vloopback-source/README.Debian
/usr/share/doc/vloopback-source/changelog.Debian.gz
/usr/share/doc/vloopback-source/copyright
/usr/src
/usr/src/vloopback.tar.bz2


(Sorry to ask all this, I feel a right muppet!)

---

### Post by nuttycyclist on 2011-10-27
ok, cold light of day, more coffee, more research.   still no further ahead :confused:


sussed the module-assistant.  
"sudo module-assistant build vloopback"  (simple really...)

That ran through and finished with output
"Done with /usr/src/vloopback-modules-2.6.32-34-generic_1.3-2+2.6.32-34.77_i386.deb ."


But following the link in the original reply is still getting me nowhere.  Output below.

user@laptop:~$ modprobe vloopback
FATAL: Module vloopback not found.
user@laptop:~$ resize /dev/video2 /dev/video3 320x240 320x240
Usage: resize [-u] [-c] [-s [rows cols]]


Can anybody explain where I'm going wrong and how to use vloopback?

---

