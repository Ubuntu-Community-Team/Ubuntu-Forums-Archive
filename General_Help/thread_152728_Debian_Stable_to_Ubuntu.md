---
title: "Debian Stable to Ubuntu"
date: 2006-03-30
forum: General Help
---

### Post by djpinger on 2006-03-30
I've searched everywhere and I can't seem to find any information on this.  If there is and I missed it, I apologize.

I currently have debian stable installed on a box, and I'd like to upgrade it to Ubuntu, without reinstalling the entire OS.  Is there a way I can safely upgrade using apt-get dist-upgrade?  If so, how would I go about doing this?  I can setup a VM for this, so maybe this could turn into a How-To in the future.

Thanks in advance for everyone's help.

---

### Post by endersshadow on 2006-03-30
Ubuntu uses Sid, not Woody, as the base system.  My thought is that you would have to reinstall everything.

However, if you're brave enough to try, do this:

Change your sources.list file to this:

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
```

Then do this:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

That's pushing it...if you were going from Sid instead of Woody I'd be more confident in doing it, but as it stands, I would suggest just doing the full Ubuntu install :-|

---

### Post by djpinger on 2006-03-30
Fortunately, VMWare workstation has the snapshot feature.  So if this breaks, no problem.  Would it be better if I upgrade from stable to testing first, and THEN upgrade to ubuntu?  I'm gonna run it on my VM and let you know how it goes.

---

### Post by endersshadow on 2006-03-30
[QUOTE=djpinger]Fortunately, VMWare workstation has the snapshot feature.  So if this breaks, no problem.  Would it be better if I upgrade from stable to testing first, and THEN upgrade to ubuntu?  I'm gonna run it on my VM and let you know how it goes.[/QUOTE]

Yeah, if you could move from Woody to Sid, it may make it a little less painful...

Keep in mind this is an experiment.  We here at endersshadow, Inc. take no responsibility for your computer blowing up.

---

### Post by cjazz on 2006-03-30
[QUOTE=endersshadow]Yeah, if you could move from Woody to Sid, it may make it a little less painful...
[/QUOTE]

Actually, the OP said he or she was using Debian stable. As of last June, that's Sarge, not Woody, just for the record. Still a big leap, though.

---

### Post by djpinger on 2006-03-30
Well, just a progress update, I setup the apt.sources file as listed above, and I also set the apt_preferences as follows:

Package: *
Pin: release a=ubuntu
Pin-Priority: 1000

I did an apt-get upgrade and it did most of the packages, but failed because some of the packages require postfix, but the standard debian install has exim4.  So I did an apt-get remove exim4-base, which automatically removed exim4 and installed postfix from the ubuntu archives.  Then, apt-get upgrade again and it worked well.  Follow that with an apt-get dist-upgrade and smooth as pie.  I checked the dpkg -l to see if there were any sarge packlages left, and only the kernel was listed (which I can upgrade later).  Now I am doing an apt-get install ubuntu-desktop.  I'll let you know how it finishes.

---

### Post by djpinger on 2006-03-30
SUCCESS!  After ubuntu-desktop installed, I installed the new 2.6 kernel (my debian VM had the 2.4).  After I installed the source, image, headers, tree, etc, I rebooted, it found all my hardware properly, and then loaded up GDM.  BAM, ubuntu desktop ;).

Mission: successful.  However, this was on a VM.  Will it work in the real world?  We'll find out this weekend.

---

### Post by endersshadow on 2006-03-30
[QUOTE=cjazz]Actually, the OP said he or she was using Debian stable. As of last June, that's Sarge, not Woody, just for the record. Still a big leap, though.[/QUOTE]

Ah...I'm behind on the Debian lingo...my fault.

As for the success... woohoo! \\:D/

---

### Post by erlyrisa on 2006-03-31
hmmm - is thier anyway to setup your computer to gain access to a dvd-drive on the netwrok and use that as an upgrade - I want to put my debian dvd's into a computer on the network and install extra stuff from that dvd - therfore not needing to download from the debian repositories. (as you can tell my ubuntu computer hasn't got a dvd player.)

---

### Post by justleen on 2006-03-31
[QUOTE=erlyrisa]hmmm - is thier anyway to setup your computer to gain access to a dvd-drive on the netwrok and use that as an upgrade - I want to put my debian dvd's into a computer on the network and install extra stuff from that dvd - therfore not needing to download from the debian repositories. (as you can tell my ubuntu computer hasn't got a dvd player.)[/QUOTE]

you could simply mount the DVD with samba, i'd say.. or NFS, for that matter (in my experience thats slightly trickier.. but ill bet thats just me)

---

### Post by djpinger on 2006-03-31
So I did it on my real life debian box last night, and in 1 hour (mostly downloading time) I had a fully operational ubuntu box.  Before rebooting after installing the new kernel and images and stuff, make sure you install ubuntu-desktop, that way on reboot, it detects your hardware properly from the get-go (new udev devices, etc).  That was totally easy.

---

### Post by endersshadow on 2006-03-31
Woohoo!  Glad you got it to work!

Welcome to Ubuntu :-D

---

### Post by erlyrisa on 2006-04-01
do ya wreckon all I'd have to do is add the mounted volume to the etc/apt/sources.list file? - I dunno - wreckon it wouldn't work - but I going to try it anyway.

---

