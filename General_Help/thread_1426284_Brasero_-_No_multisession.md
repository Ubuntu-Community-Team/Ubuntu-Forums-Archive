---
title: "Brasero - No multisession"
date: 2010-03-10
forum: General Help
---

### Post by praveenmarkandu on 2010-03-10
this blew my mind today, because i've been using ubuntu for 2 and half years. Brasero 2.28.2 in Karmic does not have an option enable multisessions when burning disc or import a disc which has a multisession. 

Seriously, wtf is going on? This is supposed to be Ubuntu's default CD authoring software.

---

### Post by ghostborg on 2010-06-13
Ubuntu 10.04
I second the Brasero wtf. I don't get a "Leave disc open" option at the burn dialog. hmmm.

K3b said it couldn't handle joilet extension at this time.

 I had to use NeroLinux.
But even Nero had problems. I had to move files in order for it to work.

I got this from another forum/thread:
Many of you experiences issues with Nero Linux 4 when continuing a multisession disc. Apparently, Nero Linux 4 is looking for some shared libs in the wrong folder, so, of course it is _NEVER_ possible to continue a multisession disc.

This issue will of course be fixed in the next release (don't ask for a date ), but you can use the following trick to make it work for now. As root,

    * - Go in /usr/lib/nero (/usr/lib64/nero for the 64-bit version)
    * - Once you are there, copy the files libISOFS.so and libUDFImporter.so to the /usr/lib (/usr/lib64 for the 64-bit version).

This should let you use the multisession features of Nero Linux 4.
Also remember to manually delete these 2 files before you uninstall or upgrade the nero linux package.

---

### Post by Linuxforall on 2010-06-13
Try gnomebaker, everything works on it for now, Brasero also fails to save to image :(

---

### Post by tagnu on 2010-12-02
Would love to see the multi-session feature in Brasero, at least a message notifying the user that multi-session support is currently unavailable.  Thank you for the new tool suggestion.  Edit: It seems, Brasero multi-session feature is related to the dvd writer's driver. [http://ubuntuforums.org/showthread.php?t=1586517](http://ubuntuforums.org/showthread.php?t=1586517)

---

### Post by ellgor on 2010-12-02
Hi,

A work-around, earlier versions of K3b did multi-sessions, I found a post that has links to it,remove any verion of K3b before starting (load in the data and lib packs first or an error will occur, it will also pull in a few other packages, this is normal) :

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

And to stop apt from updating to newer versions do this:

sudo gedit /etc/apt/preferences

add these lines and save

Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001

Hope this of use,

Regards, Ellgor.

---

