---
title: "Wally"
date: 2010-04-05
forum: General Help
---

### Post by cancer10 on 2010-04-05
Hi
I just downloaded Wally and was trying to install it but got this error

```

Error: Dependency is not satisfiable: libqt4-network (>= 4.5.1)
```


Any idea how to fix it?

---

### Post by gldearman on 2010-04-10
Hmmm ... I got a different error message related to dependencies.  But maybe the problem has a similar source (I did, eventually, get Wally installed properly.).  Did you install these packages?

```

libqt4-dev
qt4-qmake
qt4-dev-tools

```

They are all dependencies that are required for Wally to compile properly.

Hope this helps.

---

### Post by gldearman on 2010-04-10
OK, now that I try to re-install wally from source, I see that I am having a completely different experience.  This version appears to use cmake to compile; the last version I installed did not.

Of course, re-reading your post, it looks like you downloaded the Debian package and tried to install it rather than compiling from source.  Let me know if you are successful at that, since I'm getting cmake errors when I try to compile.

---

### Post by gldearman on 2010-04-10
OK, I gave up trying to compile.  I downloaded the .deb file from the [ wally homepage]("http://www.becrux.com/index.php?page=projects&name=wally").  Then, in terminal, I navigated to the folder where I put that file, and typed:

```
sudo dpkg -i wally_2.3.2-1_i386.deb
```

That worked fine, and I was able to run wally.  So, try that.  And make sure you have the wally dependencies I listed above.  Hope it works for you.

---

### Post by cancer10 on 2010-04-11
HI

It seems its looking for version 4.5.1 for  libqt4-network but i have 4.5.0 on my system


How do I upgrade?



```
shouvik@White-Rabbit:~/Desktop$ sudo dpkg -i wally_2.3.2-1_i386.deb
Selecting previously deselected package wally.
(Reading database ... 134313 files and directories currently installed.)
Unpacking wally (from wally_2.3.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of wally:
 wally depends on libqt4-network (>= 4.5.1); however:
  Version of libqt4-network on system is 4.5.0-0ubuntu4.3.
 wally depends on libqt4-sql (>= 4.5.1); however:
  Version of libqt4-sql on system is 4.5.0-0ubuntu4.3.
 wally depends on libqt4-svg (>= 4.5.1); however:
  Version of libqt4-svg on system is 4.5.0-0ubuntu4.3.
 wally depends on libqt4-xml (>= 4.5.1); however:
  Version of libqt4-xml on system is 4.5.0-0ubuntu4.3.
 wally depends on libqtcore4 (>= 4.5.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.3.
 wally depends on libqtgui4 (>= 4.5.1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.3.
 wally depends on libstdc++6 (>= 4.4.0); however:
  Version of libstdc++6 on system is 4.3.3-5ubuntu4.
dpkg: error processing wally (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wally

```

---

### Post by gldearman on 2010-04-11
You're on jaunty?  Is upgrading to karmic an option?  Because it looks like the version in jaunty's repository is 4.5.0, and there isn't a higher-one in jaunty-backports.  But the version in karmic's repository is 4.5.2.

Another option is to install an earlier version of wally.  There are earlier stable releases available on the wally homepage.  I know I ran wally on jaunty, and I installed libqt4 from the normal repository, so there is an older version that only required libqt4.5.0

---

### Post by cancer10 on 2010-04-12
I was unable to compile the older versions, wondering is there any alternate to wally?

---

### Post by gldearman on 2010-04-12
[Drapes]("http://packages.ubuntu.com/jaunty/drapes") is in the repositories. I have never tried it, but it does not appear to be able to pull wallpapers off the internet like wally, just out of your wallpapers directory.

[Wallpaper-tray]("http://packages.ubuntu.com/jaunty/wallpaper-tray") is a Gnome applet that is also in the repositories.  Again, I haven't tried it, but it does not appear to be able to pull wallpapers off the internet.

[Webilder]("http://www.webilder.org/") is not in the repositories, but appears to be the closest thing to wally out there, since it can pull pics off of Flickr.

Sorry wally wasn't working for you. I really love it.  If you decide to switch to karmic, be sure to give it a try.

---

### Post by cancer10 on 2010-04-12
Hi I have installed drapes but I do not see it anywhere under my Applications menu.


Any idea where can I find it?




Thanks

---

### Post by gldearman on 2010-04-13
Have you tried typing "drapes" at the command line?

---

### Post by cancer10 on 2010-04-13
That worked!

But do I need to type via command line everytime  I need to launch it? Is there anyway I can have ubuntu launch it automatically when I turn on my machine?



THanks

---

### Post by gldearman on 2010-04-14
I'm not sure about this, but, I think that, when it launches, it adds an icon in the system tray.  Click (or right-click) on that icon, and I think there should be a "run at startup" option.

---

