---
title: "Mistakenly removed OOffice; how can I reinstall from the ubuntu cd?"
date: 2009-12-07
forum: General Help
---

### Post by emigrant on 2009-12-07
hi all,
i mistakenly removed Ooffice. now i want to install it back.
how can i do it from the ubuntu cd.
i have a very slow internet and cannot install from the interent.

thank you very much for your help.

---

### Post by t0p on 2009-12-07
To install from the cd, check that option in **System > Administration > Software Sources** and run an update.

Did you **completely remove** OOo?  In the past, I've found that sometimes when I remove an app, it hasn't actually been *removed*, just uninstalled.  So it can be reinstalled without having to download anything.  Just a thought.

---

### Post by emigrant on 2009-12-07
> **t0p said:**
> To install from the cd, check that option in **System > Administration > Software Sources** and run an update.

Did you **completely remove** OOo?  In the past, I've found that sometimes when I remove an app, it hasn't actually been *removed*, just uninstalled.  So it can be reinstalled without having to download anything.  Just a thought.

thanks for your reply.
it still goes for the internet (plz see the attachment).

this is what i did and the error message:

```
$ apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [0ddc3e464ef646872b157b6ee0d2b473-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
Copying package lists...gpgv: Signature made Mon 20 Apr 2009 08:00:13 PM IST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
W: Skipping non-exisiting file /cdrom/dists/jaunty/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/jaunty/restricted/binary-i386/Packages
E: Could not open file /var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_Release - open (13 Permission denied)
E: Could not open file /var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_Release.gpg - open (13 Permission denied)
```

---

### Post by t0p on 2009-12-07
I see you ran the command *apt cd-rom add* as normal user (ie without *sudo*).  You then got a permissions error.  So I'd suggest you try it with *sudo*.

As for the error in your 2nd thumbnail - it can't resolve the url.  Therefore you either have a problem with your internet connection, or the site is down.  Or something.  Try again/try later.

---

### Post by emigrant on 2009-12-07
i did sudo and and still get the same error.
as for the internet i deliberately disconnected it, to avoid fetch data from the internet as i completely want to install this ooffice from the cdrom and i have only a little amount of bandwith is left for the internet [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by t0p on 2009-12-07
> **emigrant said:**
> 
as for the internet i deliberately disconnected it, to avoid fetch data from the internet as i completely want to install this ooffice from the cdrom and i have only a little amount of bandwith is left for the internet [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

If you don't want to download this stuff from the internet, just uncheck all the repositories except the CD in System > Administration > Software Sources and run an update.

As for why you can't download lists from the CD... I dunno.  Anyone else?

---

### Post by emigrant on 2009-12-07
thanks for the reply. as shown in the first pic iv unchecked all sources except the cd. no problem lets wait for somebody else.

---

