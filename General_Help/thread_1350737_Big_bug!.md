---
title: "Big bug!"
date: 2009-12-09
forum: General Help
---

### Post by pepsifx357 on 2009-12-09
What is the deal with the mscorefonts-intaller?

It's looking for a file called andale32.exe.  I know this seems weird that Ubuntu is trying to download an EXE file but it is.

It can't seem to resolve the url that this one file is located at.

I can find it on the net; I can download it, but Ubuntu can't.  So, if I can download it, then where can I put it so it will quit tryint to download this one FILE?!

EVERYTHING I try to install comes down to this one file then stops the install process, so I can't install anything:

> ben@Audio:~$ sudo apt-get install ttf-mscorefonts-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-09 16:25:20--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-09 16:25:30--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--2009-12-09 16:25:30--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-09 16:25:40--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-09 16:25:50--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-12-09 16:26:00--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following]
--2009-12-09 16:26:01--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-09 16:26:11--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-09 16:26:21--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net) [following]
--2009-12-09 16:26:21--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-09 16:26:31--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-12-09 16:26:41--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-12-09 16:26:51--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-12-09 16:27:01--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-09 16:27:11--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@Audio:~$ 


---

### Post by coffeecat on 2009-12-09
Yes it is a bug. A nasty one. It only seems to affect some people but you are one of the unlucky ones. See here:

[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

Try the workaround in post #21.

Or, if you have access to a Windows system, simply make a folder ~/.fonts and copy the appropriate *.ttf files into it. That way you'll have the ms corefonts without your system having to download them from sourceforge. Once you've done that you'll have to unmark ttf-mscorefonts-installer in Synaptic.

---

### Post by pepsifx357 on 2009-12-09
Yeah, I already did that.  I even found the file somehwere else online and changed the source and it still didn't download it.  I searched all over google and no one seems to have a solution that works for me.

Do I copy all of the Window's fonts?  Where are they?

Thanks for the help

---

### Post by rvndrk3233 on 2009-12-09
try winedoors installer. should give you the option. needs 'MS Core Fonts 'package.

the DL should be up now, it was down for awhile.this isnt a bug though, you DL or installed a package that needed it without installing the font package.

I use synaptic when possible, dpkg and apt-get sometimes miss dependancies.Or sometimes the name chages from what it expects.

---

### Post by coffeecat on 2009-12-09
> **pepsifx357 said:**
> Do I copy all of the Window's fonts?  Where are they?

They're in C:\Windows\Fonts. You want (from the ttf-msttcorefonts-installer pacakage description):

> Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings                      Just grab any *.ttf files that correspond with those names. 

Coincidentally, I was giving the same answers on another thread about the same problem, and someone came up with this post:

[http://ubuntuforums.org/showpost.php?p=8471186&postcount=5](http://ubuntuforums.org/showpost.php?p=8471186&postcount=5)

I've tried the link, but it's very slow displaying at the moment. Which is ironic. :rolleyes: But now it has displayed for me, it looks worth a try instead of copying stuff from Windows.

---

### Post by pepsifx357 on 2009-12-09
> **rvndrk3233 said:**
> try winedoors installer. should give you the option. needs 'MS Core Fonts 'package.

the DL should be up now, it was down for awhile.this isnt a bug though, you DL or installed a package that needed it without installing the font package.

I use synaptic when possible, dpkg and apt-get sometimes miss dependancies.Or sometimes the name chages from what it expects.

I just tried it.  I was trying to install gftp from synaptic and I got the same error.  Grrr

---

### Post by pepsifx357 on 2009-12-09
> **coffeecat said:**
> They're in C:\Windows\Fonts. You want (from the ttf-msttcorefonts-installer pacakage description):

Just grab any *.ttf files that correspond with those names. 

Coincidentally, I was giving the same answers on another thread about the same problem, and someone came up with this post:

[http://ubuntuforums.org/showpost.php?p=8471186&postcount=5](http://ubuntuforums.org/showpost.php?p=8471186&postcount=5)

I've tried the link, but it's very slow displaying at the moment. Which is ironic. :rolleyes: But now it has displayed for me, it looks worth a try instead of copying stuff from Windows.

Sweet!  It installed, now we'll see if it works.  Thanks!

---

### Post by pepsifx357 on 2009-12-11
Still didn't solve it.  I submitted a bug report.  It just keeps giving me that same output that I posted.

---

