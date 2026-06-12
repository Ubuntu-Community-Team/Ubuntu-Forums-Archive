---
title: "Unity is lost again"
date: 2011-10-26
forum: General Help
---

### Post by qaissi on 2011-10-26
I know the definition of insanity is doing the same thing over and over again and expecting a different outcome.

So call me nuts!!!!!

This is the third time I have lost unity.  The last two times after looking around here for help and trying all the different suggestions I got fed up and just re installed 11.10.

So lets try this a different way.  I will start my own thread for my specific situation.

I installed Gnome 3 for 11.10 using:  sudo apt-get install gnome-shell.

I rebooted and went into the normal Ubuntu.  No Unity - No Indicator section at the top right hand corner of the screen.  Right clicking on the desktop gets me nothing.  No way to get into the terminal.  Nothing.

So I did a unity --reset where it froze at setting_update run_key and then nothing.

So I did a hard reboot and went into Gnome and put the terminal, firefox, and a sudo nautilus on the desktop.

Reboot back into Unity and still nothing of course.

Found and followed this:

[http://ubuntuforums.org/showthread.php?t=1868032&highlight=unity]("http://ubuntuforums.org/showthread.php?t=1868032&highlight=unity")

After trying everything there when I do a unity --rest now I get this.

```
des@des-1110:~/Desktop$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : false
Profile     : default
Adding plugins
libprotobuf ERROR google/protobuf/message_lite.cc:123] Can't parse message of type "metadata.PluginBrief" because it is missing required fields: info
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing snap options...done
Initializing vpswitch options...done
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing mousepoll options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libstaticswitcher.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'staticswitcher'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'

```

So that is where I am at.  And about ready to tell Ubuntu where to go to boot.

Any help would be appreciated.

---

### Post by svaens on 2011-10-31
same kinda problem here. 
Would be nice if things were stable before they were declared stable

---

### Post by gandaran on 2011-10-31
remove compiz completely first (it's better to use synaptic package manager for complete removal, you don't have synaptic install it)  then re-install while using either gnome-classic, gnome-shell or unity 2D
that should fix the compiz errors.

---

### Post by svaens on 2011-10-31
actually, I ended up in fixing the problems (apparently) caused by the installation and subsequent deinstallation of fglrx (because it no longer is able to configure my dual monitor setup correctly) in the way described at:

[http://onubuntu.blogspot.com/2011/10/manually-removing-fglrx-from-ubuntu.html](http://onubuntu.blogspot.com/2011/10/manually-removing-fglrx-from-ubuntu.html)

back to fairly normal now

---

