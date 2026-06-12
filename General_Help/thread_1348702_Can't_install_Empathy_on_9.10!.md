---
title: "Can't install Empathy on 9.10!"
date: 2009-12-07
forum: General Help
---

### Post by raouiband on 2009-12-07
I know Empathy is supposed to come installed with Karmic Koala, but I'm not seeing it under Applications > Internet, or Applications > Anywhere! So, I try to install it, but I get this result:

```
ashley@pan:~$ sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: empathy-common (= 2.29.3-1~ppa9.10+1) but it is not going to be installed
E: Broken packages
```

Can anyone tell me why I'm getting this?

---

### Post by LeifAndersen on 2009-12-07
Mmm, in the command line, try running ```
 empathy 
``` if that works, your golden, otherwise, my favorite line for fixing broken applications is ```
 sudo apt-get install -f 
```.  From there, you may need to reinstall empathy.

Good luck.

---

### Post by mickie.kext on 2009-12-07
Change mirror repository. On top panel go System ---> Administration ---> Software sources, and in "Download from" chose another server. If it happens again, change server again. When it says that package is broken, usualy means that server is borked.

---

### Post by dato1989 on 2009-12-07
> **raouiband said:**
> I know Empathy is supposed to come installed with Karmic Koala, but I'm not seeing it under Applications > Internet, or Applications > Anywhere! So, I try to install it, but I get this result:

```
ashley@pan:~$ sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: empathy-common (= 2.29.3-1~ppa9.10+1) but it is not going to be installed
E: Broken packages
```

Can anyone tell me why I'm getting this?


ok let see this link [http://cosp.org.pk/blog/shoaibi/2009/12/04/open-source/packages-being-kept-back/](http://cosp.org.pk/blog/shoaibi/2009/12/04/open-source/packages-being-kept-back/) i hope it will help you 
thanks

---

### Post by raouiband on 2009-12-07
> **LeifAndersen said:**
> Mmm, in the command line, try running ```
 empathy 
``` if that works, your golden, otherwise, my favorite line for fixing broken applications is ```
 sudo apt-get install -f 
```.  From there, you may need to reinstall empathy.

Good luck.

I did that, and got:

```
ashley@pan:~$ empathy
The program 'empathy' is currently not installed.  You can install it by typing:
sudo apt-get install empathy
empathy: command not found
ashley@pan:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ashley@pan:~$ sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: empathy-common (= 2.29.3-1~ppa9.10+1) but it is not going to be installed
E: Broken packages
```

> **mickie.kext said:**
> Change mirror repository. On top panel go System ---> Administration ---> Software sources, and in "Download from" chose another server. If it happens again, change server again. When it says that package is broken, usualy means that server is borked.

I've changed mirrors about four or five times and still no luck. Should I just keep going or what?

> **dato1989 said:**
> ok let see this link [http://cosp.org.pk/blog/shoaibi/2009/12/04/open-source/packages-being-kept-back/](http://cosp.org.pk/blog/shoaibi/2009/12/04/open-source/packages-being-kept-back/) i hope it will help you 
thanks

The link isn't really loading for me. :C

---

### Post by snowpine on 2009-12-07
Is your system fully updated?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by raouiband on 2009-12-07
> **snowpine said:**
> Is your system fully updated?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
Fetched 3,739B in 13s (287B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Tried installing it afterwards and still didn't go.

---

### Post by snowpine on 2009-12-07
Hmm, what about:

```
cat /etc/apt/sources.list
```

?

---

### Post by raouiband on 2009-12-07
> **snowpine said:**
> Hmm, what about:

```
cat /etc/apt/sources.list
```?

```
ashley@pan:~$ cat /etc/apt/sources.list
# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu karmic partner
deb http://archive.canonical.com/ubuntu karmic-backports partner
deb http://archive.canonical.com/ubuntu karmic-updates partner
deb http://archive.canonical.com/ubuntu karmic-security partner
deb http://archive.canonical.com/ubuntu karmic-proposed partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic-backports partner
deb-src http://archive.canonical.com/ubuntu karmic-updates partner
deb-src http://archive.canonical.com/ubuntu karmic-security partner
deb-src http://archive.canonical.com/ubuntu karmic-proposed partner

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main

#skype
deb http://download.skype.com/linux/repos/debian stable non-free

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
deb http://deb.opera.com/opera/ lenny non-free

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#nautilus-dropbox
deb http://linux.getdropbox.com/ubuntu karmic main

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
# deb http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
deb http://ppa.launchpad.net/freenx-team/ubuntu karmic main
deb-src http://ppa.launchpad.net/freenx-team/ubuntu karmic main

#Back In Time
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A423FD95416E75D
deb http://le-web.org/repository stable main

#shutter
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main

# ifuse for iphone/itouch
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main

#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu karmic main

#Drizzle
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main

deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

```

---

### Post by snowpine on 2009-12-07
> **raouiband said:**
> ```
ashley@pan:~$ cat /etc/apt/sources.list
# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu karmic partner
deb http://archive.canonical.com/ubuntu karmic-backports partner
deb http://archive.canonical.com/ubuntu karmic-updates partner
deb http://archive.canonical.com/ubuntu karmic-security partner
deb http://archive.canonical.com/ubuntu karmic-proposed partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic-backports partner
deb-src http://archive.canonical.com/ubuntu karmic-updates partner
deb-src http://archive.canonical.com/ubuntu karmic-security partner
deb-src http://archive.canonical.com/ubuntu karmic-proposed partner

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main

#skype
deb http://download.skype.com/linux/repos/debian stable non-free

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
deb http://deb.opera.com/opera/ lenny non-free

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#nautilus-dropbox
deb http://linux.getdropbox.com/ubuntu karmic main

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
# deb http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
deb http://ppa.launchpad.net/freenx-team/ubuntu karmic main
deb-src http://ppa.launchpad.net/freenx-team/ubuntu karmic main

#Back In Time
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A423FD95416E75D
deb http://le-web.org/repository stable main

#shutter
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main

# ifuse for iphone/itouch
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main

#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu karmic main

#Drizzle
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main

deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

```

No wonder, you've added about 2 dozen software sources! Rather than using the Ubuntu Karmic repository (an excellent collection of stable applications tested specifically to work in 9.10) as your sole software source, you are pulling unstable, testing-only applications willy-nilly from dozens of different places!

Here's what I recommend:

Make a backup of your current sources.list:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Then, edit the sources.list:

```
gksu gedit /etc/apt/sources.list
```

Then, comment out (by typing a # symbol at the start of the line) every line that is not an ubuntu.com or canonical.com URL. (You might also want to comment out "proposed" and "backports").

Once you've restored your sources list to a sensible state, save the file, and try this again:

```
sudo apt-get update && sudo apt-get install empathy
```

*Any file outside your /home folder is an important system file that should not be modified unless you know exactly what you're doing and are willing to take the risk of breaking your system!*

Once you have a working system again, you *might* consider adding some of those sources back (deleting the # symbol to uncomment the line), if and only if you have a specific reason to do so. Whoever told you to add all that stuff deserves a smack. :)

---

### Post by raouiband on 2009-12-07
I changed sources.list to:

```
# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse

#Canonical Commercial Repository
#deb http://archive.canonical.com/ubuntu karmic partner
#deb http://archive.canonical.com/ubuntu karmic-backports partner
#deb http://archive.canonical.com/ubuntu karmic-updates partner
#deb http://archive.canonical.com/ubuntu karmic-security partner
#deb http://archive.canonical.com/ubuntu karmic-proposed partner
#deb-src http://archive.canonical.com/ubuntu karmic partner
#deb-src http://archive.canonical.com/ubuntu karmic-backports partner
#deb-src http://archive.canonical.com/ubuntu karmic-updates partner
#deb-src http://archive.canonical.com/ubuntu karmic-security partner
#deb-src http://archive.canonical.com/ubuntu karmic-proposed partner

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
#deb http://packages.medibuntu.org/ karmic free non-free
#deb-src http://packages.medibuntu.org/ karmic free non-free

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
#deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
#deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
# deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
# deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
# deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
# deb http://ppa.launchpad.net/compiz/ubuntu karmic main

#skype
# deb http://download.skype.com/linux/repos/debian stable non-free

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
# deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
#deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
#deb http://deb.opera.com/opera/ lenny non-free

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
#deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
#deb http://dl.google.com/linux/deb/ stable non-free

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
#deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
#deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
#deb http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
#deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
#deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#nautilus-dropbox
#deb http://linux.getdropbox.com/ubuntu karmic main

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
#deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
#deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
# deb http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
#deb http://download.virtualbox.org/virtualbox/debian karmic non-free

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
#deb http://ppa.launchpad.net/freenx-team/ubuntu karmic main
#deb-src http://ppa.launchpad.net/freenx-team/ubuntu karmic main

#Back In Time
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A423FD95416E75D
#deb http://le-web.org/repository stable main

#shutter
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
#deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main

# ifuse for iphone/itouch
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
#deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main

#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
#deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu karmic main

#Drizzle
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
#deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
#deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
#deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic maina
```I actually got it from [here]("http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/"). :S

After that, I 

```
sudo apt-get update && sudo apt-get install empathy

```

and got

```
ashley@pan:~$ sudo apt-get update && sudo apt-get install empathy
Hit http://security.ubuntu.com karmic-proposed Release.gpg
Ign http://security.ubuntu.com karmic-proposed/main Translation-en_US
Ign http://security.ubuntu.com karmic-proposed/restricted Translation-en_US
Hit http://archive.ubuntu.com karmic Release.gpg
Ign http://archive.ubuntu.com karmic/main Translation-en_US
Ign http://security.ubuntu.com karmic-proposed/universe Translation-en_US
Ign http://security.ubuntu.com karmic-proposed/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-proposed Release
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic/universe Translation-en_US
Hit http://archive.ubuntu.com karmic-backports Release.gpg
Ign http://archive.ubuntu.com karmic-backports/main Translation-en_US
Ign http://archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-backports/universe Translation-en_US
Ign http://archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com karmic-updates Release.gpg
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US
Hit http://security.ubuntu.com karmic-proposed/main Packages
Hit http://archive.ubuntu.com karmic-security Release.gpg
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com karmic Release   
Hit http://security.ubuntu.com karmic-proposed/restricted Packages  
Hit http://security.ubuntu.com karmic-proposed/universe Packages    
Hit http://security.ubuntu.com karmic-proposed/multiverse Packages  
Hit http://security.ubuntu.com karmic-proposed/main Sources         
Hit http://archive.ubuntu.com karmic-backports Release              
Hit http://archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-proposed/restricted Sources   
Hit http://security.ubuntu.com karmic-proposed/universe Sources     
Hit http://security.ubuntu.com karmic-proposed/multiverse Sources   
Hit http://archive.ubuntu.com karmic-security Release               
Hit http://archive.ubuntu.com karmic/main Packages
Hit http://archive.ubuntu.com karmic/restricted Packages
Hit http://archive.ubuntu.com karmic/multiverse Packages
Hit http://archive.ubuntu.com karmic/universe Packages
Hit http://archive.ubuntu.com karmic/main Sources
Hit http://archive.ubuntu.com karmic/restricted Sources
Hit http://archive.ubuntu.com karmic/multiverse Sources
Hit http://archive.ubuntu.com karmic/universe Sources
Hit http://archive.ubuntu.com karmic-backports/main Packages
Hit http://archive.ubuntu.com karmic-backports/restricted Packages
Hit http://archive.ubuntu.com karmic-backports/universe Packages
Hit http://archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://archive.ubuntu.com karmic-backports/main Sources
Hit http://archive.ubuntu.com karmic-backports/restricted Sources
Hit http://archive.ubuntu.com karmic-backports/universe Sources
Hit http://archive.ubuntu.com karmic-backports/multiverse Sources
Hit http://archive.ubuntu.com karmic-updates/main Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Packages
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/universe Packages
Hit http://archive.ubuntu.com karmic-updates/main Sources
Hit http://archive.ubuntu.com karmic-updates/restricted Sources
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://archive.ubuntu.com karmic-updates/universe Sources
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/main Sources
Hit http://archive.ubuntu.com karmic-security/restricted Sources
Hit http://archive.ubuntu.com karmic-security/universe Sources
Hit http://archive.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: empathy-doc (= 2.28.1.1-0ubuntu1) but 2.28.1.1-1+ppa9.10+1 is to be installed
E: Broken packages
```

---

### Post by snowpine on 2009-12-07
You can read more about the "backports" and "proposed" repositories here, decide if you really need them:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Maybe some kind soul who runs Karmic can help you out with the default sources.list so you can get back to the original list. 

I am sorry your experience with Karmic was soured by the bad advice to enable unstable/untrusted software sources. :(

---

### Post by raouiband on 2009-12-07
Wugh. ;_ ; Thank so very much for your help! I really do appreciate it. I'll make a thread asking if anyone has the default Karmic sources.list.

---

### Post by jas007 on 2009-12-08
Hi I had the exactly the same problem (error message - in relation to empathy-commons). I tired changing the server location, but still got the same problem. In the end I had to add 
```

deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main 

```
to my source list
```

sudo gedit /etc/apt/sources.list

```
I didnt need to add the key but here it is
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271

```
```

sudo apt-get update

```

after this 
```

sudo apt-get install empathy 

```
it worked.

I'm pretty sure that i removed the sources by accidental a couple of days ago, or maybe it happened during the upgrade from 9.04 to 9.10 yesterday.


hope this helps
Jason

---

### Post by raouiband on 2009-12-08
:S I just did that and it didn't seem to do anything. I still got the end result, and when I tried the key I got

```
ashley@pan:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271
gpg: requesting key FA3A1271 from hkp server keyserver.ubuntu.com
gpg: key FA3A1271: "Launchpad PPA for Telepathy" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ashley@pan:~$ 

```

Did I do something wrong? x_ x

---

### Post by raouiband on 2009-12-09
NEVERMIND. It works perfectly! Thank you very much. You rock.

---

