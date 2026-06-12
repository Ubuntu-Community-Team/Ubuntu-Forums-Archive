---
title: "Eclipse is outdated"
date: 2009-10-19
forum: General Help
---

### Post by james2504 on 2009-10-19
Hi All,

Being new to Ubuntu (Or any version of Linux) I'm after a IDE that I'm reasonably familiar with and I found that I can get Eclipse. However it appears to be a *very* old version.

I checked many places and found several threads all of which seem to indicate the package was updated (Somewhere between a few weeks ago and yesterday). See the very end of this really long post at [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064)

However when I run apt-cache policy eclipse I get 

>   Installed: (none)
  Candidate: 3.2.2-5ubuntu3
  Version table:
     3.2.2-5ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages

and obviously if I use apt-get I get the really old version of eclipse which is of no use to me.

What am I doing wrong? Some clue please?!?

---

### Post by sdowney717 on 2009-10-19
[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

get it direct from them. you dont need a deb file.

unpack it and run it from the directory

you might need to run it like the "./nameofexecutablefile"

and you can make a desktop launcher for the program

---

### Post by james2504 on 2009-10-19
Sorry, I should have been a bit more clear. I realise that I can simply download the package from Eclipse and install it anywhere I want. However the package on Eclipse's site is a general package and there's no guarantee it will be able to find everything it needs to run correctly (Although it probably will be OK). In addition it won't install in my (For want of a better word) "Start" menu.

There are several posts saying that I should be able to use Synaptic Package manager to get the Eclipse package I want but it's not working.

So my question is what is wrong with Synaptic package manager that it can't find the update everyone says is there?

---

### Post by akakingess on 2009-10-19
Within the download it should include the libs, etc. that are necessary and if any are missing than you can install them through synaptic, also once it is installed, you can add the application to your startup applications without any issues.

---

### Post by 1clue on 2009-10-19
I have been using Eclipse for years.  It never occurred to me to try to use the Ubuntu version, since we want very specific features and versions.

Eclipse needs a Java JDK, and possibly a Tomcat and a few other things all of which run on a Java JVM.  Everything which has a plug-in site, you get through Eclipse's plugin mechanism, not through any other source.

Apps which have their own plug-in mechanism are rarely supported well in anybody's package manager.

The "start" menu, click on "applications" and then go down to "add/remove."

FWIW, I install my own Sun JDK, tomcat, ant, gant, etc, even though there is an Ubuntu-managed install of the same exact thing.  I manage the current version with symlinks, and my builds are always built with exact versions I can't accidentally change to some other version.  If something is needed which I don't actually need a specific version of, I use the Ubuntu version.

All this is stuff you would want to decide on for any professional development environment.  If you're working on Ubuntu's distro, you would probably manage everything through Synaptics, but in a general sense you would want to be very careful of your dependency chain no matter what language or IDE you are using.

---

### Post by Sam on 2009-10-19
System-wide installation (latest version):


Download the package from [eclipse.org](http://www.eclipse.org/downloads/) (Eclipse Classic 3.5.1).

Run:
```
sudo tar xzf eclipse-SDK-3.5.1-linux-gtk.tar.gz -C /opt
sudo ln -s /opt/eclipse/eclipse /usr/local/bin
gksudo gedit /usr/share/applications/eclipse.desktop
```


Paste this in gedit:
```
[Desktop Entry]
Name=Eclipse
Comment=Develop applications in a variety of different programming languages
Exec=/usr/local/bin/eclipse
Icon=/opt/eclipse/plugins/org.eclipse.sdk_3.5.1.v200909170800/eclipse48.png
Terminal=false
Type=Application
Categories=Development;
StartupNotify=true
```

Save, close gedit and enjoy ! ;)

---

### Post by james2504 on 2009-10-20
Thanks very much! Clear instructions that I could adapt to what I wanted to do :P

---

