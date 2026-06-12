---
title: "Global name 'cd_path' is not defined"
date: 2011-10-05
forum: General Help
---

### Post by DARKZAY on 2011-10-05
Hi
I was wondering if someone could help me.  I have been trying to install ubuntu 11.10 daily build via wubi.  Unfortunatly when I have passed the user details and starts to extract and install, it comes up with 'Global name 'cd_path' is not defined'

The error log
[http://pastebin.com/eqQMQFic](http://pastebin.com/eqQMQFic)

List of things I have done.

Tried to install it via daemon tools.
Mounted the image and ran it as admin
Disconnected from the internet to prevent it downloading a new iso every time.

Please help if you can.

---

### Post by hwttdz on 2011-10-05
Looks like there's a bug in the wubi installer (not surprising given it's still not polished).  You could look at the \lib\wubi\application.py file and define the cd_path variable, it should probably be a path to the iso.

---

### Post by bcbc on 2011-10-05
Could be a problem with the daily-live ISO I suppose. But file a bug since it's getting close to release:
[https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug)

I've tested revision 236 of wubi.exe and it's worked okay but I haven't burned it to a cd (or mounted it like you)

PS... you don't need to mount the image. Just copy wubi.exe into the same directory that you have the ISO and it will use it.

---

### Post by DARKZAY on 2011-10-06
Thank you for your replies.  I have filed a bug report here [https://bugs.launchpad.net/wubi/+bug/869144](https://bugs.launchpad.net/wubi/+bug/869144)

Hopefully this will be fixed as soon as possible...

---

### Post by bcbc on 2011-10-06
Good work - I see they've released a fix already (quickest bug turnaround I've seen). Might take a little while to work its way into the daily-live image.

---

### Post by DARKZAY on 2011-10-06
I know I was amazed myself when they released a fix for this, and such a speed. (No dbz reference here lol)  
About the fix I don't know if this is the right place to ask but just wanted to know is it already integrated into wubi already or do i need to do anything to make it work?  (Sorry quite new to this)

---

### Post by bcbc on 2011-10-06
The new wubi.exe is published to [http://people.canonical.com/~evand/wubi/oneiric/](http://people.canonical.com/~evand/wubi/oneiric/)
It's possible to download this and test (I usually test from this location). But in your case, it won't work as you are testing from a mounted CD image and you can't just replace the wubi.exe on the mounted ISO (or even if you could the md5sum wouldn't match).

So that confirmation test would have to wait until the new wubi makes it to the daily-live CD ISO (hard to say when - depends on when they build the images I guess). By tomorrow for sure.

To save time updating the daily-live ISO I use a tool called [zsync]("https://help.ubuntu.com/community/ZsyncCdImage") which just downloads the changes to the ISO - and this usually means a download of < 200MB as opposed to downloading the full 700MB each time.

---

### Post by DARKZAY on 2011-10-06
[FONT="Arial"]WOW!!!  Never heard about this software thanks, I'll be giving it another whirl tomorrow.

Thank you once again for helping!  ^^[/FONT]

---

