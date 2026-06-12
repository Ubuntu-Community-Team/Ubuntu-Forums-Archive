---
title: "Failed to download repository information"
date: 2011-02-05
forum: General Help
---

### Post by Luigi37 on 2011-02-05
Hey there,
So when I try to check for updates AND also when I try and press "reload" in the Synaptic package manager, I get this error:
> Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Sometimes, I also get this red triangle with an exclamation point in my toolbar thing that tells me I have repository problems, or something along those lines.  I'm assuming they're all related.  I've been looking around, and I noticed people having similar errors and just being able to uncheck something in my Software settings, or something like that.  In my case, I'm not exactly sure what to uncheck though, don't wanna screw anything up any more!  I'm using 10.10, and I believe I'm using Maverick...I'm not sure what that means though.  I've only recently started using Linux, sorry for being a noob!
Thanks!

EDIT: Also, I should note that I recently changed the server to try and fix it.  I selected best server, but it still won't work.

---

### Post by spaceboy909 on 2011-02-06
> **Luigi37 said:**
> Hey there,
So when I try to check for updates AND also when I try and press "reload" in the Synaptic package manager, I get this error:


Sometimes, I also get this red triangle with an exclamation point in my toolbar thing that tells me I have repository problems, or something along those lines.  I'm assuming they're all related.  I've been looking around, and I noticed people having similar errors and just being able to uncheck something in my Software settings, or something like that.  In my case, I'm not exactly sure what to uncheck though, don't wanna screw anything up any more!  I'm using 10.10, and I believe I'm using Maverick...I'm not sure what that means though.  I've only recently started using Linux, sorry for being a noob!
Thanks!

EDIT: Also, I should note that I recently changed the server to try and fix it.  I selected best server, but it still won't work.
In my 'software sources', I have 4 items checked under the 'ubuntu software' tab, and 2 canonical archive sources checked under 'other software'.  Is that what yours looks like?

---

### Post by Luigi37 on 2011-02-06
Hmmm, on the Ubuntu Software tab, I have all 4 boxes checked.  But on the Other Software tab, I have 6 items...The Canonical Partners once are unchecked, then two Independent ones are checked.  The last two are the links provided in the error code I was getting so I unchecked them and now no error! 
Now I wonder though...what is this gdm2 setup thing?  I looked it up and it seems it's some Login screen editor or something.  I think I remember downloading something like that...I have this Login Screen item in my System>Administrator menu, but it doesn't really do anything.

---

### Post by Elfy on 2011-02-06
You are trying to use a ppa for lucid and karmic for maverick - there doesn't appear to be one

[http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/)

The PPA will be there in software sources - disable it from settings in update manager in the other software tab.

---

### Post by Spyderkid on 2011-02-06
(just for futur refrence)

If you ever have problems with the software centre its always best to check for updates.

---

### Post by Luigi37 on 2011-02-06
> **forestpiskie said:**
> You are trying to use a ppa for lucid and karmic for maverick - there doesn't appear to be one

[http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/)

The PPA will be there in software sources - disable it from settings in update manager in the other software tab.
Well I did that and it's working, but now what?  Is there a program (gdm2 setup) I have that won't update now or what?  Is it related to this Login Screen program I have?  I'd like to just get rid of it entirely now if I'm not using it..

---

### Post by Elfy on 2011-02-06
> **Luigi37 said:**
> Well I did that and it's working, but now what?  Is there a program (gdm2 setup) I have that won't update now or what?  Is it related to this Login Screen program I have?  I'd like to just get rid of it entirely now if I'm not using it..

Possibly - I have no idea what you have installed ;)

Check in synaptic or software centre to see if you have it installed.

If it's there then mark it for complete removal

---

### Post by Luigi37 on 2011-02-07
> **forestpiskie said:**
> Possibly - I have no idea what you have installed ;)

Check in synaptic or software centre to see if you have it installed.

If it's there then mark it for complete removal
Hmmm I checked there and I can't find anything...I searched for gdm2 and such to no avail, and searching login screen brought up important login files that I think are part of Ubuntu's core processes so I don't wanna mess with those lol.
Stupid mysterious program!  Oh well, I'll just pretend it doesn't exist, everything is working fine anyway now since I unchecked them in the Software Sources.  Thanks for the help guys! :)

---

