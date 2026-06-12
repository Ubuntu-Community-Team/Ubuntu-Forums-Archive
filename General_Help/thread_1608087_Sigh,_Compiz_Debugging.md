---
title: "Sigh, Compiz Debugging"
date: 2010-10-28
forum: General Help
---

### Post by Lamez on 2010-10-28
Back, again, I have a new problem. I like learning about how Linux as an OS works. I seem to break things on my way. Anywho somehow I broke my installation of Compiz Fusion. I have tried completely uninstalling the packages and reinstalling them. That did not work. When I try to enable the desktop effects, it does not work and says "Desktop Effects Could Not Be Enabled". Then it locks down the application. I have used them before, I have checked my graphics driver and they seem to work. Any guesses? Thanks!

---

### Post by 3Miro on 2010-10-28
Go to Terminal (Applications -> Accessories). Then type
```
 compiz --replace 
```
this should output a bunch of stuff as well as more details on what the problem is.

To test your driver (which is the usual culprit for visual effects) run glxgears in the terminal. You should get hundreds of FPS (I have 880 on an Intel integrated video).

---

### Post by Lamez on 2010-10-29
Okay I know it is not my graphics card drivers, here is the output from the gears or what not:

```

31687 frames in 5.0 seconds = 6337.392 FPS
31981 frames in 5.0 seconds = 6396.152 FPS
31469 frames in 5.0 seconds = 6293.727 FPS
31399 frames in 5.0 seconds = 6279.722 FPS

```

However, this is what I get from the compiz:
```

lamez@studio:~$  compiz --replace
Starting gtk-window-decorator

(gtk-window-decorator:2989): Gdk-WARNING **: GdkWindow 0x160025e unexpectedly destroyed

(gtk-window-decorator:2989): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gtk-window-decorator:2989): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gtk-window-decorator:2989): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gtk-window-decorator:2989): Gdk-WARNING **: GdkWindow 0x16003a2 unexpectedly destroyed

(gtk-window-decorator:2989): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gtk-window-decorator:2989): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gtk-window-decorator:2989): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

What does it mean?

---

### Post by WorMzy on 2010-10-29
Looks like the Window Decoration plug-in is causing problems. Open ccsm and double-check your settings for it and, if necessary, disable it.

---

### Post by Lamez on 2010-10-29
That is funny because I cannot set any settings using CCSM, here is what it looks like when I open up CCSM:

[http://i.imgur.com/tdoVi.png](http://i.imgur.com/tdoVi.png)

---

### Post by WorMzy on 2010-10-29
Most of those General plug-ins look like non-standard ones. Have you been installing extra plug-ins from somewhere? Could one of them have caused ccsm to stop working?

You could try manually editing ~/.config/compiz/compizconfig/Default.ini if you're feeling adventurous. Or just rename that file and Compiz should default back to it's original settings the next time you run it.

---

### Post by Lamez on 2010-10-29
What would happen if I deleted the folder? Also I notice I have these folders:

compiz
compiz-1

under .config

What have I done?

---

### Post by WorMzy on 2010-10-29
I have a compiz-1 folder too, I assumed it'd been left over from when I installed compiz++.

If you delete the compiz folder it should be recreated with the default contents when you start compiz. I'm not sure about the compiz-1 folder any more, unless you've installed compiz++ too?

---

### Post by Lamez on 2010-10-29
Crap I have no idea, I will leave it be. I am going to delete the folder and let you know what happens.

---

### Post by Lamez on 2010-10-29
I noticed something intresting. I deleted both folders, rebooted and tried to enable desktop effects. No luck there. Then opened up CCSM and tried setting some plugins, no luck then looked at the config folder and found the folder compiz-1 that is intresting. 

My next thought is to try to completly remove compiz and install back to default just like when I installed the OS, any idea how I can achieve this?

---

### Post by WorMzy on 2010-10-29
Well, this should remove the standard packages:

```
sudo apt-get purge compiz compiz-core compiz-dev compiz-fusion-bcop compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-kde compiz-plugins compizconfig-backend-gconf compizconfig-backend-kconfig compizconfig-settings-manager libcompizconfig0 libcompizconfig0-dev python-compizconfig
```

If you've installed any non-standard packages you'll need to remove those as well.

After you've removed everything, you may want to remove the /usr/share/compiz and /usr/lib/compiz folders, just to make sure that there's no remnants of the packages left over.
```
sudo rm -r /usr/share/compiz /usr/lib/compiz
```

Also remove the ~/.local/compiz & compiz-1 folders again, as well as ~/.compiz

Then reinstall the packages you want.

---

### Post by Lamez on 2010-10-29
Well I am not sure what packages I need to install. I removed everything. What should I install?

---

### Post by Lamez on 2010-10-29
Could I just install it using the Ubuntu Software Center?

---

### Post by WorMzy on 2010-10-29
Install compiz, and you'll get all the normal packages. If you want extra plugins, install compiz-fusion-plugins-extra as well.

```
sudo apt-get install compiz compiz-fusion-plugins-extra
```

Or use the software centre if you prefer.

---

### Post by Lamez on 2010-10-29
Okay I got this error before, and I know what a dependency is, but I don't know the name of it, so I get this:

> 
[sudo] password for lamez: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages



I am unsure on how to fix this and I do want the extra plugin.
How can I fix this?

Also, thank you for you contributing your time.

Also I am using Ubuntu 10.10.

---

### Post by WorMzy on 2010-10-29
Odd, that package is a virtual package should be "installed" when you installed compiz-core (which is an integral part of compiz, as the name suggests).

Have you added any third-party repositories to your software sources which may be causing the wrong packages to be downloaded and installed?

---

### Post by Lamez on 2010-10-29
No, I have not.

> 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

# deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) maverick main


Also that last line has been commented out before I did all that stuff.

---

### Post by WorMzy on 2010-10-29
Have you done
```
sudo apt-get update
```
since commenting it out/disabling it? If not, then you've probably downloaded packages from that repository. Try manually installing compiz-core-abiversion and the extra plug-ins with
```
sudo apt-get update && sudo apt-get install compiz-core compiz-core-abiversion-20091102 compiz-fusion-addons-extra
```

---

### Post by Lamez on 2010-10-30
I am a bit confused now. Why is this not working?

```

Package compiz-core-abiversion-20091102 is a virtual package provided by:
  compiz-core 1:0.8.6-0ubuntu9.1 [Not candidate version]
  compiz-core 1:0.8.6-0ubuntu9 [Not candidate version]

E: Package 'compiz-core-abiversion-20091102' has no installation candidate
E: Unable to locate package compiz-fusion-addons-extra

```

---

### Post by WorMzy on 2010-10-30
I think you must have installed a newer version of compiz from that launchpad repository.

Open a terminal and run
```
compiz --version
```

If you've installed the version from the launchpad repository, then it'll say something like "Compiz 0.9.0"
But if you've installed the standard version, it'll say something like "Compiz 0.8.6".

If you want the extra plugins, you're going to have to uninstall everything again, run
```
sudo apt-get update
```
and, just in case
```
sudo apt-get clean
```
And then
```
sudo apt-get install compiz compiz-fusion-plugins-extra
```

---

### Post by Lamez on 2010-10-30
Okay, I think I found the problem.

take a look at this and tell if you notice something:
```

lamez@studio:~$ sudo apt-get install compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-plugins libdecoration0
Suggested packages:
  nvidia-glx
The following NEW packages will be installed:
  compiz-core compiz-plugins libdecoration0
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,398kB of archives.
After this operation, 9,155kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main compiz-core i386 1:0.9.0-0ubuntu1~ppb1 [363kB]

```

Notice where it is downloading it from? I doubled checked my sources and it is still commented out, then I did an update (sudo apt-get update) tried to install the core again and still it is looking at the lauch pad for the packages!

---

### Post by Ancanus on 2010-10-30
> **Lamez said:**
> Okay, I think I found the problem.

take a look at this and tell if you notice something:
```

lamez@studio:~$ sudo apt-get install compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-plugins libdecoration0
Suggested packages:
  nvidia-glx
The following NEW packages will be installed:
  compiz-core compiz-plugins libdecoration0
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,398kB of archives.
After this operation, 9,155kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main compiz-core i386 1:0.9.0-0ubuntu1~ppb1 [363kB]

```

Notice where it is downloading it from? I doubled checked my sources and it is still commented out, then I did an update (sudo apt-get update) tried to install the core again and still it is looking at the lauch pad for the packages!

Tried this? You may have to install ppa-purge if you do not have it already.

```
ppa-purge ppa:compiz/ppa
```

---

### Post by Lamez on 2010-10-30
That worked! I did as Ancanus said todo, then install the packages and boom! Thanks Guys!

---

### Post by WorMzy on 2010-10-31
I take it that everything is working correctly now? No more gtk-window-decorator errors?

---

### Post by Lamez on 2010-10-31
Everything works correctly, no errors. At first it was a bit laggy then I disabled the cylinder plugin, then it worked great. I restarted and tried it again now it was like the day I installed 10.10. Thanks for all your help!

---

### Post by cpmman on 2010-10-31
Please goto the top of the thread "Thread Tools" and mark it "Solved"

---

