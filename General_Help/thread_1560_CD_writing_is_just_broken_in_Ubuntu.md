---
title: "CD writing is just broken in Ubuntu?"
date: 2004-10-21
forum: General Help
---

### Post by stodge on 2004-10-21
Am I right in thinking that CD writing is just broken in Ubuntu? I've always had success with SCSI emulation in other distros, but U is the first one that's not worked for me.

Thanks

---

### Post by cybrjackle on 2004-10-21
error message and some details go along way for support questions.

 :D

---

### Post by stodge on 2004-10-21
Haha! Good point!  :oops: 

cdrecord -scanbus
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to &lt;cdrtools@packages.debian.org&gt;.
      The original author should not be bothered with problems of this version.

cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by FLeiXiuS on 2004-10-21
I recorded a cd VIA nautilus cdrecord...worked out alright.   Give it a shot..

---

### Post by Smeggy on 2004-10-21
You shouldn't need ide-scsi emulation for CD burning in kernel 2.6.x

---

### Post by stodge on 2004-10-21
I have a CDRom and a CDWriter on the secondary IDE channel. How would I use it? I've tried cdrecord with a device of /dev/hdd.

Thanks

---

### Post by cybrjackle on 2004-10-21
[http://www.togaware.com/linux/survivor/Nautilus_CD.shtml](http://www.togaware.com/linux/survivor/Nautilus_CD.shtml)

---

### Post by mikew777 on 2004-10-23
[QUOTE=stodge]I have a CDRom and a CDWriter on the secondary IDE channel. How would I use it? I've tried cdrecord with a device of /dev/hdd.

Thanks[/QUOTE]

stodge
You can write in Ubuntu if you download K3B from universe. Then when you want to burn go to, Applications, System Tools, Root Terminal. Type in K3B then just wait till K3B comes up and it should have found all your drives, then burn away. You will get a error message that cdrdro wasn't found, you can disregard that message or go ahead and install it and you will not get the error. The burn will work either way. I can burn CD's and DVD's with no problems. If you don't use the above Root Terminal as suggested when you boot out you will no longer be able to log back in as it will change your ICE.authority file. You then have to edit that file in a terminal B4 you can get back in. Doing it the way I have discribed you will have no problems. Hope this helps...
Mike

---

### Post by im_ka on 2004-10-23
i love the simplicity of nautilus-cdburner

---

### Post by elwis on 2004-10-23
Actually, this is the weak spot I just noticed too, which will get me back to SuSe again.

I've got a cd-recdord and a DVD reader, Ubuntu won't have anything of it. The Cd-recorder is a cd-rom and my dvd is also a cd-rom.. according to Ubuntu. If I put a DVD record in it the system hangs and I'll pull the plug.

I found it strange, this has worked flawless in every other distro I've tried on this machine for the last 3 years, would be nice if they could get it going.
Until then, I'm a SuSe man again.. though I will aurely miss the speldnid Gnome, and will stay sleepless with the thought of having to tackle RPM's again :(

---

### Post by mikew777 on 2004-10-23
[QUOTE=elwis]Actually, this is the weak spot I just noticed too, which will get me back to SuSe again.

I've got a cd-recdord and a DVD reader, Ubuntu won't have anything of it. The Cd-recorder is a cd-rom and my dvd is also a cd-rom.. according to Ubuntu. If I put a DVD record in it the system hangs and I'll pull the plug.

I found it strange, this has worked flawless in every other distro I've tried on this machine for the last 3 years, would be nice if they could get it going.
Until then, I'm a SuSe man again.. though I will aurely miss the speldnid Gnome, and will stay sleepless with the thought of having to tackle RPM's again :([/QUOTE]

elwis
I had this same problem and couldn't play music CD's (it saw my writer & dvd drive as the writer) but the writer still couldn't write CD'. I had to go into applications, multimedia, CD Player and under the prefrences part of the CD menu (looks like and screwdriver & wrench) you have to change it to what & where your DVD Player is and then you can play music and the like. The default on my system was /dev/cdrom and the "real location was" /dev/hdd. Yours might be somewhat different but you get the idea. The writing issue I fixed under this same thread.  
Hope this helps....
Mike

---

### Post by stodge on 2004-10-23
[QUOTE=elwis]Actually, this is the weak spot I just noticed too, which will get me back to SuSe again.

I've got a cd-recdord and a DVD reader, Ubuntu won't have anything of it. The Cd-recorder is a cd-rom and my dvd is also a cd-rom.. according to Ubuntu. If I put a DVD record in it the system hangs and I'll pull the plug.

I found it strange, this has worked flawless in every other distro I've tried on this machine for the last 3 years, would be nice if they could get it going.
Until then, I'm a SuSe man again.. though I will aurely miss the speldnid Gnome, and will stay sleepless with the thought of having to tackle RPM's again :([/QUOTE]

I'm with elwis - it won't see my burner. The first distro to do that.

---

### Post by gamehack on 2004-10-23
Hmm...

I have similar problem. Nautilus-cd-burner detects my cd-writer, but cd-record could not, why does this happen?

Thanks

---

### Post by FLeiXiuS on 2004-10-23
I would recommend installing k3b from the universe repository.  Then just 
```
sudo k3b
```
to burn cd's.

---

### Post by stodge on 2004-10-23
k3b requires KDE right? I'm running a KDE free desktop :)

Thanks though!

---

### Post by nuopus on 2004-10-23
I think there is something wrong with xcdroast ubuntu package or one if its dependencies. It scans but does not find any burner, yet k3b sees it for what it is just fine! I can even burn with the nautilus cd burner.
 
 I want to use xcdroast though. Does anyone know what is going on here?

---

### Post by jgeorgeson on 2004-10-24
[QUOTE=nuopus]I want to use xcdroast though. Does anyone know what is going on here?[/QUOTE]

I think the problem is you prefer xcdroast! :p

I have run 'sudo k3bsetup' to set a group with write permission, and k3b doesn't list my cdrw as a writer. However, under Settings->Configure K3b, the reader listing for my device does say it can write CDRWs, just not CDs. The nautilus burn interface works just fine. The cdrecord -scanbus command reports the same error for me about /dev/pg* and SCSI emulation. 

The unfortunate truth is that at this time nothing from the KDE world (like k3b) is supported, so since the nautilus interface works, I don't think this is receiving any attention from the ubuntu developers. Looking at the k3b home page, I've noticed that people there are saying kernel 2.6.8.1 doesn't have all that a certain version range (which includes the version ubuntu ships) are a little flaky.

---

### Post by nuopus on 2004-10-24
Okay I finally got xcdroast to work. Apparently it didnt detect automatically ... but when I added it manually by using the device (/dev/hdc) it found the device name and everything.
 
 OH ... I also compiled a new version of xcdroast with gtk2 support so that it looks MUCH better with gnome 2.8. I don't understand why they have a distro based around gnome 2.8 and gtk2 and have compiled xcdroast with only gtk1 support. Hmmmmmm oh well.
 
 Does anyone want a deb of xcdroast with gtk2 support?

---

### Post by elwis on 2004-10-24
[QUOTE=nuopus]Okay I finally got xcdroast to work. Apparently it didnt detect automatically ... but when I added it manually by using the device (/dev/hdc) it found the device name and everything.
 
 OH ... I also compiled a new version of xcdroast with gtk2 support so that it looks MUCH better with gnome 2.8. I don't understand why they have a distro based around gnome 2.8 and gtk2 and have compiled xcdroast with only gtk1 support. Hmmmmmm oh well.
 
 Does anyone want a deb of xcdroast with gtk2 support?[/QUOTE]
 You bet you.. send it away to elwesthal at gmail dot com

And I'll buy you a beer whenever we meet :)

---

### Post by FLeiXiuS on 2004-10-24
[QUOTE=stodge]k3b requires KDE right? I'm running a KDE free desktop :)

Thanks though![/QUOTE]



No it doesn't require KDE, I'm using it with GDM

---

### Post by vulpes on 2004-10-24
Some of you may be bitten by the problem that was introduced (apparently) in kernel 2.6.8. On my FC2 laptop, CD burning works fine with 2.6.7, but not at all with 2.6.8. Here's some detailed information:
[http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=130576](http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=130576)

---

### Post by stodge on 2004-10-24
[QUOTE=FLeiXiuS]No it doesn't require KDE, I'm using it with GDM[/QUOTE]

What I mean is, does it still require the KDE libraries to be installed? If so, then I won't use it.

Thanks

---

### Post by nuopus on 2004-10-24
[QUOTE=vulpes]Some of you may be bitten by the problem that was introduced (apparently) in kernel 2.6.8. On my FC2 laptop, CD burning works fine with 2.6.7, but not at all with 2.6.8. Here's some detailed information:
 [http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=130576]("http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=130576")[/QUOTE] 
 That would hold water with me if I wasn't using Gentoo previously and burning happily with the 2.6.8 kernel.

---

### Post by im_ka on 2004-10-24
[QUOTE=vulpes]Some of you may be bitten by the problem that was introduced (apparently) in kernel 2.6.8. On my FC2 laptop, CD burning works fine with 2.6.7, but not at all with 2.6.8. Here's some detailed information:
[http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=130576](http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=130576)[/QUOTE]

fact is, that i have ubuntu with linux 2.6.8 and i'm happily burning cd's with xcdroast and nautilus(cdburner)

---

### Post by snowx1000 on 2004-10-27
My burning is effed up also, worked fine in mepis.

---

### Post by mark on 2004-10-28
[QUOTE=snowx1000]My burning is effed up also, worked fine in mepis.[/QUOTE]I have now successfully burned data & music CDs using the *Nautilus* burner...the data being backups and .ISO files, the music being .OGG versions that I "ripped" from existing audio CDs (for the test - I've since blanked the target CD-R/Ws).  If there's a problem, I haven't seen it.

BTW, K3B can be installed even with Gnome as the environment - just use *apt-get*  or *Synaptic* and accept the dependencies...

---

### Post by stodge on 2004-10-28
[QUOTE=nuopus]Okay I finally got xcdroast to work. Apparently it didnt detect automatically ... but when I added it manually by using the device (/dev/hdc) it found the device name and everything.
 
 OH ... I also compiled a new version of xcdroast with gtk2 support so that it looks MUCH better with gnome 2.8. I don't understand why they have a distro based around gnome 2.8 and gtk2 and have compiled xcdroast with only gtk1 support. Hmmmmmm oh well.
 
 Does anyone want a deb of xcdroast with gtk2 support?[/QUOTE]

You bet - how big is the file?

Thanks!

---

### Post by thorhr on 2004-10-28
[QUOTE=mikew777]stodge
You can write in Ubuntu if you download K3B from universe. Then when you want to burn go to, Applications, System Tools, Root Terminal. Type in K3B then just wait till K3B comes up and it should have found all your drives, then burn away. You will get a error message that cdrdro wasn't found, you can disregard that message or go ahead and install it and you will not get the error. The burn will work either way. I can burn CD's and DVD's with no problems. If you don't use the above Root Terminal as suggested when you boot out you will no longer be able to log back in as it will change your ICE.authority file. You then have to edit that file in a terminal B4 you can get back in. Doing it the way I have discribed you will have no problems. Hope this helps...
Mike[/QUOTE]
 This works great thanks!

---

### Post by emperor on 2004-10-28
"xcdroast"  does not auto-detect my cdrom's either but you can configure it manually by using "/dev/hdc" and "/dev/hdd" as the device names.  "xcdroast" is a gui that actually uses "cdrecord" to do the work!.  So, at the commandline "cdrecord" should work as well using the actual device names. I  successfully copied a CD last night using "xcdroast", so I know cdrecord does work in Ubuntu.

---

### Post by jivens on 2004-10-28
[QUOTE=nuopus]Okay I finally got xcdroast to work. Apparently it didnt detect automatically ... but when I added it manually by using the device (/dev/hdc) it found the device name and everything.
 
 OH ... I also compiled a new version of xcdroast with gtk2 support so that it looks MUCH better with gnome 2.8. I don't understand why they have a distro based around gnome 2.8 and gtk2 and have compiled xcdroast with only gtk1 support. Hmmmmmm oh well.
 
 Does anyone want a deb of xcdroast with gtk2 support?[/QUOTE]
 I would love to have a deb if you have one available and its not too much trouble. My email is [email]swordwielder@earthlink.net[/email].
I wonder if there is a way  to actually post it on th forum for anyone to download?
Thanks, Jeff

---

