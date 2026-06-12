---
title: "Dependency Hell"
date: 2006-03-04
forum: General Help
---

### Post by Krank on 2006-03-04
I think I just messed up... I need some serious help.

Situation:
I wanted to use the latest version of the MLdonkey p2p software. I found a .deb package (for sarge-unstable), and tried to install it. Turned out it needed quite a few files... New versions of files I already had. So, I make another search, and download the files needed, once again as deb's from Sarge... Used dpkg -i to install the files.

Whoopie, everything works. MLdonkey runs, and nothing seems to have changed.

...until the next time I tried doing a "sudo aptitude dist-upgrade". it deleted about 286 mb's of files from my HD, including GDM and most Gnome-related files...

OK, so I try reinstalling GDM. I get the following:

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  gdm: Depends: libbonobo2-0 (>= 2.8.0) but it is not installable
       Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
       Depends: libgconf2-4 (>= 2.9) but it is not installable
       Depends: libgnome2-0 (>= 2.8.0) but it is not installable
       Depends: libgnomeui-0 (>= 2.8.0) but it is not installable
       Depends: libgnomevfs2-0 (>= 2.11.3) but it is not installable
       Depends: libgsf-1 (>= 1.12.3) but it is not installable
       Depends: liborbit2 (>= 1:2.10.0) but it is not installable
       Depends: librsvg2-2 (>= 2.9.5) but it is not installable
```

Of course, I try to find and/or install/upgrade these packages - no luck. Similar messages, all the way.

The less graphical and thus less expendable systems (Samba, MLDonkey, the firewall scripts, the FTP/HTTP servers, and so on) seem unaffected - they run like they always have.

If anyone out there would happen to know *why* this has happened, and perhaps also *how* I can "undo the damage", I would be much obliged.

I'd rather not reformat all my partitions - I haven't the amount of DVD's to make a proper backup of everything I have there right now...

---

### Post by Xian on 2006-03-04
[QUOTE=Krank]If anyone out there would happen to know *why* this has happened....[/quote]

It happened because you used packages that are not binary-compatible with Ubuntu. In order to be assured of running a stable system you should always be extremely careful when using unsupported repositories. The applications that you install from those repos may run fine, but also result in breaking APT because of various conflicts with other system libraries and programs.

[QUOTE=Krank]...and perhaps also *how* I can "undo the damage", I would be much obliged.[/QUOTE]

Frankly, it may not be fixable. Your best course of action is:

1. Purge any and all packages from your system that came from the foreign repositories that you mentioned.
2. Replace them with Ubuntu supported builds.
3. Install the desktop meta-pkg again (ubuntu-desktop) to try and reinstall what APT automagically removed in its effort to fix the problem.

---

