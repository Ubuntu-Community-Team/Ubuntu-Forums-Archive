---
title: "re: How to make the totally unsupported Lexmark X2500 Work"
date: 2010-02-17
forum: General Help
---

### Post by rockette morton on 2010-02-17
My post refers to the tutorial:

[http://ubuntuforums.org/showthread.php?t=1243920](http://ubuntuforums.org/showthread.php?t=1243920)

and also to post #8 of this thread:

[http://ubuntuforums.org/showthread.php?t=1223710](http://ubuntuforums.org/showthread.php?t=1223710)

which explains how to get above tutorial to work with a x64 bit system.

Okay, details in full:  I am trying to get my Lexmark x2550 printer to work in Ubuntu 9.10.  I have done a lot of searching in the forums (which has been mostly positive) but I believe I am having a problem that has not yet been accounted for.

I have downloaded the Lexmark driver (debian package) which may be found here:

[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_UK&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_UK&locale=en)

I am now following Magic_Spehar's instructions (to the T) in order to adjust the package for a x64 system as follows:

[I]* download lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip for Ubuntu 32 bit from the Lexmark website
* unzip 'lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip'
* enter in a terminal:  sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
* Now go to your directory lexmark_install
* In that directory you'll find a file named arch.tar   Unzip that file.
* Once unzipped you'll find lexmark-inkjet-08-driver-1.0-1.i386.deb

[/I]All fine up until this point.  In my lexmark_install directory there is no arch.tar, and I've searched around for anything like *driver*.deb and came up with nothing.  The procedure would then normally go:
[I]
* Ok, now download and install the program getlibs from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) (just get getlibs-all.deb and install) Getlibs is a wonderful tool that takes care of all the missing 32 bit libs automatically.
* enter in a terminal: sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
* now your Lexmark should do its job ...[/I]

Ta da.  Here is a copy of the contents of my directory:

about             installscreen.lua        pacman.lua
bin               instarchive_all          rpm.lua
config            instarchive_all.sizes    selectdirscreen.lua
deb.lua           langscreen.lua           slack.lua
files_extra       lexribbon.png            startupinstaller.sh
finishscreen.lua  licensescreen.lua        summaryscreen.lua
generic.lua       packagedirscreen.lua     utils.lua
groups.lua        package.lua              utils-public.lua
info              package-public.lua       welcomescreen.lua
install.lua       packagetogglescreen.lua  xdg-utils

Is it possible that Lexmark have changed the structure of their debian package?  If anyone could shed some light on this I would be, needless to say, extremely grateful.

---

