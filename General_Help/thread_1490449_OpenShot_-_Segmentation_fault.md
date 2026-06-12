---
title: "OpenShot - Segmentation fault"
date: 2010-05-22
forum: General Help
---

### Post by alket on 2010-05-22
I just installed OpenShot from Ubuntu Software Center.
When I want to launch it, it displays nothing, then i try from terminal and I get this:
```
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
Process no longer exists: 15049.  Creating new pid lock file.
A new frmMain has been created
Segmentation fault
```

2 month early I was at Ubuntu 10.04 beta and this problem occurred in : VLC, OpenArena, FileZilla etc. and I made a fresh install in April. So please help me, I configured Ubuntu and have lots of important files, A fresh install isn't an option for me.

---

### Post by Sealbhach on 2010-06-02
I get the same segfault when I try to start Openshot.

I tried the install from the Lucid repos and from the Openshot PPA.

I'm using Ubuntu Lucid Lynx 64-bit.

```
$ openshot
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
Process no longer exists: 15439.  Creating new pid lock file.
A new frmMain has been created
Segmentation fault

```

.

---

### Post by soro2005 on 2010-06-03
Me too. Here's a bug report: [https://bugs.launchpad.net/openshot/+bug/573792](https://bugs.launchpad.net/openshot/+bug/573792)

---

### Post by soro2005 on 2010-06-09
I have solved my problem, which consisted in a version of cairo that I had acquired with a different ppa. Restored the regular cairo that comes with lucid --> openshot now starts again without segfault.

---

### Post by hellocatfood on 2010-06-11
> **soro2005 said:**
> I have solved my problem, which consisted in a version of cairo that I had acquired with a different ppa. Restored the regular cairo that comes with lucid --> openshot now starts again without segfault.

How did you downgrade cairo, or which package in particular did you reinstall?

---

### Post by soro2005 on 2010-06-13
> **hellocatfood said:**
> How did you downgrade cairo, or which package in particular did you reinstall?

I had the cairo package from a [ppa containing an svn version of the GIMP]("https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn"), and I've removed it using the very useful ppa-purge, which you can find in the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") (make sure you don't install all the ppa if you only want to grab ppa-purge). So I don't know what exact packages were downgraded, but from what I see, it should be several whose name starts with libcairo-.

---

### Post by psoulocybe on 2010-06-23
Wow, same issue.
I'll see about rolling back cairo packages, but I'll probably just move on to another editor.

---

### Post by LXCC on 2010-07-24
I have segmentation fault error too.
OpenShot installed from Ubuntu Software Center on Ubuntu 10.04.

```

$ uname -a
Linux uesr-desktop 2.6.32-24-generic-pae #38-Ubuntu SMP Mon Jul 5 10:54:21 UTC 2010 i686 GNU/Linux


$ openshot
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
Process no longer exists: 2442.  Creating new pid lock file.
A new frmMain has been created
state saved
on_mnuOpenProject_activate called with self.mnuOpenProject
A new frmOpenProject has been created
project modified:  Opened project
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Changed visibility of clip
state saved
project modified:  Moved clip
state saved
project modified:  Changed visibility of clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Changed audio of clip
state saved
project modified:  Moved clip
state saved
project modified:  Changed audio of clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Changed audio of clip
state saved
project modified:  Moved clip
state saved
project modified:  Changed audio of clip
state saved
project modified:  Changed audio of clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
project modified:  Moved clip
state saved
on_nbFiles_switch_page
Init Effects tab
project modified:  Added effect burningtv
state saved
on_tlbPlay_clicked called with self.tlbPlay
GenerateXML for an Effect
on_tlbPlay_clicked called with self.tlbPlay
project modified:  Changed visibility of track
state saved
GenerateXML for an Effect
project modified:  Changed audio of clip
state saved
project modified:  Added effect burningtv
state saved
GenerateXML for an Effect
GenerateXML for an Effect
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
project modified:  Changed visibility of track
state saved
project modified:  Changed visibility of track
state saved
GenerateXML for an Effect
GenerateXML for an Effect
on_tlbUndo_clicked
on_tlbUndo_clicked
on_tlbUndo_clicked
on_tlbUndo_clicked
on_tlbUndo_clicked
on_tlbUndo_clicked
project modified:  Added effect frei0r.cartoon
state saved
GenerateXML for an Effect
Segmentation fault

```Any ideas?

---

### Post by altonbr on 2010-07-29
> **soro2005 said:**
> I had the cairo package from a [ppa containing an svn version of the GIMP]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn"), and I've removed it using the very useful ppa-purge, which you can find in the [xorg-edgers ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") (make sure you don't install all the ppa if you only want to grab ppa-purge). So I don't know what exact packages were downgraded, but from what I see, it should be several whose name starts with libcairo-.
Same problem here.

I had this exact problem until I downgraded libcairo2 from 1.9.6-6~mrw4 to 1.8.10-2ubuntu1.

---

