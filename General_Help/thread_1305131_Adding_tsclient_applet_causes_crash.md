---
title: "Adding tsclient applet causes crash"
date: 2009-10-29
forum: General Help
---

### Post by gregh on 2009-10-29
I am using Karmic and if I add the tsclient applet to the panel it causes a crash.
I have tried it on my laptop and also my desktop pc and the result is the same.

"The panel encountered a problem while loading "OAFIID:GNOME_TSClientApplet
Do you want to delete the applet from your configuration?"

-G

---

### Post by Technoviking on 2009-10-29
I see this problem also. Created a bug report, you should confirm it when you get a chance.

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-applets/+bug/463877](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-applets/+bug/463877)

T-V

---

### Post by gregh on 2009-10-29
> **Technoviking said:**
> I see this problem also. Created a bug report, you should confirm it when you get a chance.

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-applets/+bug/463877](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-applets/+bug/463877)

T-V

done !

---

### Post by petay on 2009-10-30
I have the same problem!!! i do a lot of remote desktop connections for work and the applet is really handy!! i have been hunting about and found that if you upgrade to the latest version of tsclient solves it!! I will try to upgrade manually and see if this is true!

---

### Post by networkthinking on 2009-11-08
Any update on this?

---

### Post by troyzero on 2009-11-09
I would also like to know the status of this. I use this applet quite a lot so it is a little bit of a pain. Just a little pain though.
:)

---

### Post by tixetsal on 2009-11-14
Same problem here.  No luck compiling from source.  I get this error.  I wish that someone could explain how to properly determine dependencies / requirements when attempting to compile from source.  Running into this problem when attempting to compile is frustrating, and I haven't been able to find anything definitive on this topic via the WWW.

checking for TSC... configure: error: Package requirements (glib-2.0 gmodule-2.0 gobject-2.0 gtk+-2.0 libglade-2.0 libgnome-2.0 gnome-desktop-2.0 gnome-vfs-2.0 libnotify gconf-2.0 libnm_glib) were not met:

No package 'libglade-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libnotify' found
No package 'gconf-2.0' found
No package 'libnm_glib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables TSC_CFLAGS
and TSC_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by sandman74 on 2009-11-25
I was able to fix this on my laptop by removing tsclient and installing the package from jaunty. My applet works fine, and all my saved connections are still there as well.:)

---

### Post by ivago on 2009-12-02
I also just installed Jaunty's 64-bit tsclient and all seems fine, your connectiosn are in the hidden .tsclient folder in your home directory so you can easily migrate this to a new account.

But how can I exclude tsclient from updating to the newer versin when doing a normal system upgrade?

The 64-hit deb can be fownloaded from this link:

[https://launchpad.net/ubuntu/+source/tsclient/0.150-1ubuntu6/+build/927068/+files/tsclient_0.150-1ubuntu6_amd64.deb](https://launchpad.net/ubuntu/+source/tsclient/0.150-1ubuntu6/+build/927068/+files/tsclient_0.150-1ubuntu6_amd64.deb)

---

### Post by Aenima99x on 2009-12-02
I worked around the problem by adding it through the "application Launcher" - then choosing Internet/terminal Server Client instead of using the one directly in the Add to panel menu.

---

### Post by freakalad on 2009-12-08
> **ivago said:**
> The 64-hit deb can be fownloaded from this link:

[https://launchpad.net/ubuntu/+source/tsclient/0.150-1ubuntu6/+build/927068/+files/tsclient_0.150-1ubuntu6_amd64.deb](https://launchpad.net/ubuntu/+source/tsclient/0.150-1ubuntu6/+build/927068/+files/tsclient_0.150-1ubuntu6_amd64.deb)

Worked a charm; thanks ivago :)

---

### Post by Simstud on 2009-12-09
> **sandman74 said:**
> I was able to fix this on my laptop by removing tsclient and installing the package from jaunty. My applet works fine, and all my saved connections are still there as well.:)

Thanks a bundle, that works! Here's the download link for everyone: [http://packages.ubuntu.com/jaunty/tsclient](http://packages.ubuntu.com/jaunty/tsclient)

---

### Post by Braveheart1980 on 2009-12-13
> **Simstud said:**
> Thanks a bundle, that works! Here's the download link for everyone: [http://packages.ubuntu.com/jaunty/tsclient](http://packages.ubuntu.com/jaunty/tsclient)

Thanx m8 !

PS Does anyone know a way so even if i "sudo apt-get update" and then "sudo apt-get upgrade" the tsclient won't upgrade to the new buggy one?

---

### Post by Simstud on 2010-02-11
> **Braveheart1980 said:**
> Thanx m8 !

PS Does anyone know a way so even if i "sudo apt-get update" and then "sudo apt-get upgrade" the tsclient won't upgrade to the new buggy one?
go to the package manager, search for tsclient, click on it to highlight it, then click "package" from the menu bar, and check "lock version".

---

### Post by rnerwein on 2010-02-11
> **gregh said:**
> I am using Karmic and if I add the tsclient applet to the panel it causes a crash.
I have tried it on my laptop and also my desktop pc and the result is the same.

"The panel encountered a problem while loading "OAFIID:GNOME_TSClientApplet
Do you want to delete the applet from your configuration?"

-G

hi
got some thing else and wrote a bug report too: Bug #516483 reported

and a looked in my ./.xsession-errors
and found:
 ** (gnome-panel:2287): WARNING **: panel-applet-frame.c:1273: failed to
 load applet OAFIID:GNOME_IndicatorApplet:
 System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0
 ** (update-notifier:2322): DEBUG: --security-updates-unattended: 0

 LoadPlugin: failed to initialize shared library
 /usr/lib/mozilla/plugins/libflashplayer.so
 [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

looed in /usr/lib/mozilla/plugins and what i see ---> /[COLOR=Red]libflashplayer.so: wrong ELF class: ELFCLASS32][/COLOR]
i'm running 9.10 64bit !
this library must come with any update - system was running before for month with any problems.
ciao

---

### Post by conejero on 2010-04-09
Really sick and tired of this error. I can not understand how something so simple hasn't been fixed yet.

---

### Post by robot_chicken_parm on 2010-05-07
im also experiencing this problem.  its really urking me.  for now i replaced AWN with a custom gnome panel on the bottem with simmilar attributes,  but i really miss my awn terminal emulator and i wanted to see what that network sharing thing is all about.  i really hope this bug gets fixed soon!!!  also is it possible (and if so how to) for me to download more applets for the gnome terminal?  really i would prefer to have AWN working properly with all my stuff on it, i sure do miss the difference.

desktop with AWN:

[IMG]http://hphotos-snc3.fbcdn.net/hs609.snc3/32070_120266511325927_100000277362563_221379_6103617_n.jpg[/IMG]



Current Desktop:

[IMG]http://hphotos-sjc1.fbcdn.net/hs553.snc3/30284_120837167935528_100000277362563_223000_6526515_n.jpg[/IMG]

i much prefer the more interactive applets available for the avant window navigator instead of te custom gnome panel at the bottem of my sccreen.  somebody please fix this!  tanks guys.  much love.  UBUNTU FOREVER!!
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

