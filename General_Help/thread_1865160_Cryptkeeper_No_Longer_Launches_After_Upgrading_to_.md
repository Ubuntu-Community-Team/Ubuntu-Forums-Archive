---
title: "Cryptkeeper No Longer Launches After Upgrading to 11.10"
date: 2011-10-19
forum: General Help
---

### Post by chiques on 2011-10-19
So I upgraded to Ubuntu 11.10 from 11.04 and among other applications not working, [COLOR="Red"]Cryptkeeper[/COLOR] appears to be one of them. 

Normally when I launch this application I get an icon on my top right of my task bar. I no longer see it on 11.10.

Any suggestions are greatly appreciated.

---

### Post by bibble235 on 2011-10-19
Hi,

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

from

[http://ubuntuguide.net/cryptkeeper-system-tray-applet-to-manage-encrypted-folders-in-ubuntu](http://ubuntuguide.net/cryptkeeper-system-tray-applet-to-manage-encrypted-folders-in-ubuntu)

---

### Post by noeldawe on 2011-10-20
> **bibble235 said:**
> Hi,

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

from

[http://ubuntuguide.net/cryptkeeper-system-tray-applet-to-manage-encrypted-folders-in-ubuntu](http://ubuntuguide.net/cryptkeeper-system-tray-applet-to-manage-encrypted-folders-in-ubuntu)

That worked for me in 11.04 but not in 11.10...

---

### Post by noeldawe on 2011-10-20
[https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/877473](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/877473)

---

### Post by finca on 2011-10-21
I had the same problem and then started playing with the interface options at login (The little wheel at the top right of the login button). Cryptkeeper worked in Ubuntu but not in Ubuntu 2D. Play with these and one of the interfaces should restore your so called lost programmes due to the upgrade.

With much more of this sort of stuff I think I'll go back to Windows.

Good luck

---

### Post by luissil on 2011-10-21
> **bibble235 said:**
> Hi,

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

from

[http://ubuntuguide.net/cryptkeeper-system-tray-applet-to-manage-encrypted-folders-in-ubuntu](http://ubuntuguide.net/cryptkeeper-system-tray-applet-to-manage-encrypted-folders-in-ubuntu)


doesn't work for me either!!

---

### Post by hktvenattu on 2011-10-22
you have to do:
***gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"***
and then
***setsid unity***

---

### Post by luissil on 2011-11-08
> **hktvenattu said:**
> you have to do:
***gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"***
and then
***setsid unity***

nope doesnt works for me, i got:

```
luis@luis-despacho:~$ gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
luis@luis-despacho:~$ setsid unity
luis@luis-despacho:~$ Checking if settings need to be migrated ...no
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
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x5400012 (unity-2d-p)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

---

### Post by Jivinathejamboree on 2012-01-16
put those words in bold in the terminal and it worked for me in 11.10.... thankyou

---

### Post by chiques on 2012-01-16
> **hktvenattu said:**
> you have to do:
***gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"***
and then
***setsid unity***

This worked for me!

---

### Post by telathos on 2012-02-04
That worked perfect for me. Thank you

---

### Post by dynaman on 2012-02-10
> **hktvenattu said:**
> you have to do:
***gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"***
and then
***setsid unity***


Worked perfectly for me too

---

### Post by Jivinathejamboree on 2012-02-16
It worked for me when I did it, but everytime I restart ubuntu, I have to do it again... anyone know a more permanent fix, or a cryptkeeper alternative that works with Unity 2D?

---

### Post by RcTomcat on 2012-03-09
Every time I enter the setsid unity command i get the following error

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
compiz (core) - Fatal: No composite extension
compiz (composite) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'composite'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: InitPlugin 'opengl' failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension
Segmentation fault


Any help on this?
I really need cryptkeeper to run...cant access a lot of my files at the moment

---

### Post by kalabalik on 2012-03-16
I've tried what you guys have written above, but it still doesn't show up for me in the System Tray :/

 Would really like to get it to work with 11.10!

Any further ideas??

After I've entered the "setsid unity" command this is the message I get in terminal;

```
denis@ubuntu:~$ setsid unity
denis@ubuntu:~$ Checking if settings need to be migrated ...no
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
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session

(metacity:8985): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
denis@ubuntu:~$ Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4e00006 (Displays)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c00044 ([SOLVED] C)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x42004ef (denis@ubun)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

---

### Post by Fury1306 on 2013-02-09
Hi

I just learned, that there will be no whitelist anymore in 13.04

[http://www.omgubuntu.co.uk/2013/02/raring-retires-system-tray-whitelist](http://www.omgubuntu.co.uk/2013/02/raring-retires-system-tray-whitelist)
[https://bugs.launchpad.net/ayatana-design/+bug/974480](https://bugs.launchpad.net/ayatana-design/+bug/974480)

Is there a tool similar to cryptkeeper, that will still work in 13.04?

I'd prefer a program that is in the official repositories, because this is privacy relevant and I don't want to a PPA for this.

---

