---
title: "mediubuntu dosnt connect with me"
date: 2009-08-20
forum: General Help
---

### Post by gawadelnil2002 on 2009-08-20
mediubuntu dosn't want to give me the jaunty sources list when i type "wget http://www.medibuntu.org/sources.list.d/jaunty.list" it says waiting and waiting then retry and waiting, my ineternet connection is good and working very well, i think its server problem, do any one have the same problem today??????????? and can any one give me his sourceslist for mediubuntu "64bit", cause i see the "http://packages.medibuntu.org/" is working but "http://www.medibuntu.org/" is not working and i cant wait all the day for resetting the serever

---

### Post by gawadelnil2002 on 2009-08-20
now i can ping it the dns of mediubuntu "87.98.242.110" so its resolved and my isp have no problem as i see so what is the wrong plz some one have to answer me ???? im waiting

---

### Post by tgeer43 on 2009-08-20
Indeed, [www.medibuntu.org]("http://www.medibuntu.org") seems to be down at the moment (4:20 am EST).

Here is my 9.04 64-Bit sources.list. Be forewarned - I have a LOT of extra repositories enabled. If you use this list as-is, you will likely get some 'missing key' errors but there are comments next to each repository that contain commands that you can enter in a terminal to retrieve the keys. Also be aware that when you do an update after installing this list you will be running some experimental or pre-release packages. Having said that, I've had no problems with it other than the new Firefox (3.5?) 'Shiretoko' being incompatible with some of my extensions.

```
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEY

# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu jaunty main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty-updates main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.canonical.com/ubuntu jaunty-backports partner
deb http://archive.canonical.com/ubuntu jaunty-updates partner
deb http://archive.canonical.com/ubuntu jaunty-security partner
deb http://archive.canonical.com/ubuntu jaunty-proposed partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty-backports partner
deb-src http://archive.canonical.com/ubuntu jaunty-updates partner
deb-src http://archive.canonical.com/ubuntu jaunty-security partner
deb-src http://archive.canonical.com/ubuntu jaunty-proposed partner

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 033431536A423791
deb http://deb.opera.com/opera/ lenny non-free

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free

#shutter
deb http://ppa.launchpad.net/shutter/ppa/ubuntu jaunty main

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

# Depot PlayOnLinux
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://deb.playonlinux.com/ jaunty main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
deb http://ppa.launchpad.net/wvengen/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu jaunty main

#nautilus-dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

#Drizzle
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu jaunty main

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu jaunty main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu jaunty main

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main

#wine
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 58403026387EE263
deb http://wine.budgetdedicated.com/apt jaunty main

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu jaunty main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main

deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main #Blueman
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #OpenOffice.org
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main #Firefox
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu jaunty main #Ubuntu Mozilla Security Team
deb http://ppa.launchpad.net/gnome-games-experimental/ppa/ubuntu jaunty main #Experimental Gnome Games
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #Ubuntu X

deb http://www.pvv.ntnu.no/~knuta/xmms/jaunty ./

```p.s. This list was not created by me. The original author is in the first line of the file.

tgeer

---

### Post by gawadelnil2002 on 2009-08-20
actually your sources list dosnt have anything about mediubuntu but i appreciate what u did ,your sources list is very good for me it have alot ppas i needed it but i didnt know how i can get it 'like xmms" that is very good thank u

---

### Post by tgeer43 on 2009-08-20
Medibuntu is in there - have another look.

tgeer

---

### Post by gawadelnil2002 on 2009-08-20
> **tgeer43 said:**
> Medibuntu is in there - have another look.

tgeer

yeah yeah its there i didnt see it , i know now how much its hard to read big text content

plz, have a look on that  [http://ubuntuforums.org/showthread.php?t=1245046](http://ubuntuforums.org/showthread.php?t=1245046)

---

### Post by tgeer43 on 2009-08-20
Yeah, they got you good on that one. Sometimes it amazes me how people will post a long message with no formatting, punctuation, capitalization, grammar, or proper spelling whatsoever.
> i meen who wants 2 spend there time reeding a 5000 word post 2 try too help sum1 when they r 2 lazy or stoopid 2 apply even the most basik rulez of the language they expekt peeps 2 spend there time reserching and ansering there kwestions but they wont even take a minit 2 format there kwestion so it is reedable by humans no what i meenI truly enjoy helping folks on this forum and that's why I spend so much time on here. I really appreciate the help that I get in return as well. That's why I go to such lengths to make my posts easy to read and provide all of the information that I think is relevent. I'm not talking about you, mind you, but you brought it up and triggered my need to vent.

But this is getting way off topic so I'll try to wrap it up. I hope that the sources.list I provided helps you out. Good luck in all of your future Ubuntu endeavours.

If you *were* referring to the formatting of the list that I posted, please bear in mind that it *is* a list, after all. And as far as lists go, this one is quite readable with proper spacing and even a nice, easy to see heading for each section.

BTW: medibuntu.org is back online now (8:00 am EDT).

tgeer

---

