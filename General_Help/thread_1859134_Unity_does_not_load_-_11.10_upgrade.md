---
title: "Unity does not load - 11.10 upgrade"
date: 2011-10-13
forum: General Help
---

### Post by psyopper on 2011-10-13
Help. Please. 

I just completed the upgrade from 11.04 to 11.10. Unity does not load and is not falling back to 2d. I get no side bar, nor a top panel. I have to manually navigate to my Firefox.bin to launch the browser. Opening a terminal with Ctl Alt T trying to launch unity there fails.

I presume this is because I'm running an AMD/ATI 5700 series card and need to load updated drivers to get compositing to work correctly. How do I update the drivers?

```
brad@ubuntu-desktop:/usr/lib$ unity
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
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
Initializing mousepoll options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwobbly.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wobbly'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libobs.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'obs'
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing place options...done
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscreenshot.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'screenshot'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "run_command_terminal_key"


```

---

### Post by effenberg0x0 on 2011-10-13
Hey, try to follow the procedures I described in this thread, post 5 and on.
[http://ubuntuforums.org/showthread.php?t=1857059](http://ubuntuforums.org/showthread.php?t=1857059)

Regards,
Effenberg

---

### Post by zemadz on 2011-10-13
While you have not resolved this problem, can you not login with "Ubuntu 2D" mode? Top right icon near the user name in the login screen allows you to access that.

BTW, I am also having a problem with missing panels. The hardware is older though and maybe not exactly the same reason, but who knows.

---

### Post by psyopper on 2011-10-13
> **effenberg0x0 said:**
> Hey, try to follow the procedures I described in this thread, post 5 and on.
[http://ubuntuforums.org/showthread.php?t=1857059](http://ubuntuforums.org/showthread.php?t=1857059)

Regards,
Effenberg

Thanks, that was a big help.

1. FGLRX wasn't installed
2. I downloaded the driver and created the packages
3. I installed the packages named fglrx*.deb, not amd*.deb
4. They failed to install because I was missing dkms
5. I did an apt-get install of DKMS which then triggered completing the install of  FGLRX

Reboot and now it works as it should. My fear at this point is reliance on the ATI proprietary drivers. Every time the kernel upgrades am I going to have to go through this again?

---

### Post by effenberg0x0 on 2011-10-13
Have a read on this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Summary: Not necessarily.

Regards,
Effenberg

---

### Post by Stewinashoe on 2011-10-14
I am having the same problem. When I get the ati proprietary drivers installed, unity works but I can't get my dual monitors working. I change the settings in catalyst and when I click apply, catalyst just closes. If I remove fglrx, my dual monitors work fine but unity doesn't load! Any suggestions? If I can't figure it out then tomorrow I'm just going to reinstall.

---

### Post by BluSpoon on 2011-10-14
I've had the same issue. 

I've re installed the ati drivers and did the following:
Ctrl alt T

Jockey-gtk and installed the ati again.
rebooted.
In Terminal ran:
sudo aticonfig --initial=dual-head
Rebooted
Ran catalyst admin to set up xinerama.

No idea if the reboots are all needed but its working for me so far.

Ps, sorry poor formatting and apelling as I'm having to post from my phone.

---

### Post by Cynical on 2011-10-14
> **Stewinashoe said:**
> I am having the same problem. When I get the ati proprietary drivers installed, unity works but I can't get my dual monitors working. I change the settings in catalyst and when I click apply, catalyst just closes. If I remove fglrx, my dual monitors work fine but unity doesn't load! Any suggestions? If I can't figure it out then tomorrow I'm just going to reinstall.

The reason unity doesn't load is because Ubuntu is still trying to load the fglrx driver even though it is uninstalled. Follow my instructions _[here]("http://ubuntuforums.org/showthread.php?p=11343771#post11343771")_ in order to return your system to using the open source radeon driver.

---

### Post by Stewinashoe on 2011-10-14
Worked! Thank you so much!

---

### Post by Rebootkid on 2011-10-15
How about some love for those of us seeing this problem with Nvida cards?
I tried to adapt the directions to work, and clearly screwed something up, because this didn't work for me.

---

### Post by effenberg0x0 on 2011-10-15
@Rebootkid,

Try this thread, post #13:
[http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia+grub](http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia+grub)

And some of the posts below, which have Unity/compiz tests and additional info.

Please report back.

Effenberg

---

