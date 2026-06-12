---
title: "Where do I find synce-dccm"
date: 2010-10-16
forum: General Help
---

### Post by glendavee on 2010-10-16
I'm trying to synce several windows mobile devices without much success. All  the instructions I've read say that synce-dccm should be installed. I can't find it (or synce-odccm) either via synaptic or using apt-get install. Has this package been re-named or incorporated into something else or just redundant? I have the repository  "launchpad.net/synce/ppa/ubuntu lucid" added to my sources.
Any suggestions?

---

### Post by TBerk on 2010-10-16
I am looking for it also.

I'm currently running 10.10 RC, I have a pocket pc (Axim) and while it might be nice at some point to fully integrate the calendar and contacts function, I'd settle for the moment with having it show up on the desktop.


TBerk

---

### Post by glendavee on 2010-10-16
bump

---

### Post by TBerk on 2010-10-16
OK, it looks like we'll be the actual ones helping ourselves, and perhaps others. eventually.

Lets start here:

[SynCE.Org]("http://www.synce.org/moin/")   ...

I tried to see what happens if I just ran the given instructions, given I've been here before w/ ver8.x and maybe Lucid as well, (and had success), But now I'm running 10.10. 

Since I have an older device running WinCE 2003 (Axim) I went to the link for legacy devices;

[http://www.synce.org/moin/LegacyDevices/Ubuntu](http://www.synce.org/moin/LegacyDevices/Ubuntu)

I find the following at the top of that page very interesting;

> If you want to use just the file browsing or program installation stuff, you only need to install synce-hal and librapi2-tools. If you want to sync, see below... 

In any case, I tried to plug the standard install in:

```


xxx@computer:~$ sudo apt-get install multisync-tools opensync-plugin-evolution opensync-plugin-synce-legacy
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opensync-plugin-synce-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  opensync-plugin-synce-rra

E: Unable to locate package multisync-tools
E: Package 'opensync-plugin-synce-legacy' has no installation candidate
xxx@computer:~$ 

```

Just for grins I'm including  the relevant portion I hand entered in my 'sources' file; (note differing OS version:)

```

#SynCE Repositories
#
deb http://ppa.launchpad.net/synce/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/synce/ppa/ubuntu lucid main

```

Thats what I have so far. Actually I've rebooted at least once since all this so let me see what happens if I re-plug the device in via it's USB cable...

eh, at least I was able to 'see' the pda before, but as of right now the SynCE tray icon doesn't.


TBerk

---

### Post by glendavee on 2010-10-17
Thanks TBerk. I've tried to follow the legacy route, as one of my devices is Mobile 2003. When I added the repositories and then tried apt-get install, I got the following error messages :

[COLOR="Red"]Err [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid Release.gpg
  Something wicked happened resolving 'opensync.gforge.punktart.de:http' (-5 - No address associated with hostname)
Err [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) sid/main Translation-en_GB
  Something wicked happened resolving 'opensync.gforge.punktart.de:http' (-5 - No address associated with hostname)
Ign [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid Release                              
Ign [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid/main Packages                        
Ign [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid/main Sources                         
Ign [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid/main Packages
Ign [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid/main Sources
Err [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid/main Packages
  Something wicked happened resolving 'opensync.gforge.punktart.de:http' (-5 - No address associated with hostname)
Err [http://opensync.gforge.punktart.de](http://opensync.gforge.punktart.de) sid/main Sources
  Something wicked happened resolving 'opensync.gforge.punktart.de:http' (-5 - No address associated with hostname)
Fetched 832B in 19s (43B/s) 

[COLOR="Black"]I'm not going any further for now, as I think, amongst other things, that my USB to iPAQ cable is suspect, so I've ordered a new one.
Good luck[/COLOR][/COLOR]

---

### Post by Dmitriy Ps on 2011-01-01
I also have this trouble with HP ipaq rx3715. I downloaded the package from [http://packages.ubuntu.com/dapper/otherosfs/synce-dccm ]("http://packages.ubuntu.com/dapper/otherosfs/synce-dccm")
and install it. After this all working well.
ps ubuntu 10.10
pps sorry for my english :-)

---

### Post by paul.drover on 2011-02-24
This is cross-posted with the synce how-to thread as well. I'm here as well hoping for a wider audience.

Running Maverick. I blithely followed the howto to install synce 'cause I'd kinda like to have my Ubuntu machine talk to my phone (htc). There was an indication that dccm was needed as well, so I apt-got synce-dccm. Now my machine fails to boot - black screen no disk activity after the grub2 os selection. How do I go about undoing what I've done? I'm guessing that it starts with booting from a CD, but what then?

Help... please.

Paul.

---

### Post by Dmitriy Ps on 2011-03-01
Maybe this isnot whery good idea, but..
I think that you can start the livecd and then via chroot remove package.
If you want i can describe it step-by-step
(but i never try it)

---

### Post by paul.drover on 2011-03-03
> **Dmitriy Ps said:**
> Maybe this isnot whery good idea, but..
I think that you can start the livecd and then via chroot remove package.
If you want i can describe it step-by-step
(but i never try it)

Hi Dmitriy. That's pretty much what I expected to have to do, but I don't know where to go to remove the package. A step-by-step would be appreciated.
Cheers,
Paul.

---

### Post by drgrumpy on 2011-04-28
I just figured out the answer to this - you don't in Maverick.

It seems that it is now included in synce-connector which is listed in synaptic from the synce ppa.

There seems to be a problem with the packages: I installed synce-connector first, then synce trayicon, which in turn installed synce-hal and uninstalled synce-connector. But then if I subsequently installed synce-connector which uninstalled synce-hal byt left the trayicon and at least I can get as far as synce-pls giving a list of files and the tray icon shows the device status.

Also If I try to install synce-gvfs it wants to uninstall synce-connector.

---

