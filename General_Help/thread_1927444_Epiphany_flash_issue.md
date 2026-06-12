---
title: "Epiphany flash issue"
date: 2012-02-18
forum: General Help
---

### Post by lurgee on 2012-02-18
Hi, all

I've been happily using Epiphany for ages, and everything seemed to be working well.  LAst week, Epiphany talked to Flash nicely, and played video clips.  Today, it doesn't.  If I try to play a clip, I'm told there is a missing plugin.

I have multiple browsers on this computer, and they play clips fine.  The problem seem to be local to Epiphany, and arose in the last few days.  Updates were downloaded the other night, and there was a disc check during boot today, but I don't see how this could have affected things.

Epiphany extensions are installed.  I have tried removing and reinstalling.  I feel I'm missing something simple.  Tell me what it is.

---

### Post by Rodney9 on 2012-02-18
This may help - [http://ubuntuforums.org/showthread.php?t=1852167](http://ubuntuforums.org/showthread.php?t=1852167)

I must admit I just like Chromium in Lubuntu, quiet light and doesn't memory leak, plays flash too.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by lurgee on 2012-02-18
Thanks for pointing m in the direction of that thread, but reconfiguring flash plugin didn't resolve (I've rebooted since then, just to give it a fair shot).

The problem doesn't seem to be with flash per se, as I have Seamonkey on this computer, and it runs fine.  I downloaded Firefox as well, as a test for flash, and it also worked well.  Only Epiphany seems to be having trouble.

I didn't like Chrome/Chromium all that much - it might sound odd, but I always felt I might somehow break the browser if I pressed the buttons too hard.  Epiphany - while it has its faults - felt a bit more robust.  Only it won't play videos, all of a sudden.

---

### Post by lurgee on 2012-02-18
Bump.

There seem to be a couple of other people experiencing flash related problems, post upgrade.

---

### Post by lurgee on 2012-02-21
Just ran
> $ nspluginwrapper -v -n -a -i
And got the following result:
> Auto-install plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/flashplugin-alternative.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/gecko-mediaplayer.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/flashplugin-alternative.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /home/jt/.mozilla/plugins
Looking for plugins in /home/jt/.mozilla/pluginsDoes this shed any light on anything for anyone?  All I can see is that my elves are erring.  Bloody little tykes, I knew I was being too lenient on them ...

---

### Post by lurgee on 2012-02-23
Finally managed to work my way to a solution on this.

1 - I purged flash from my laptop.  I have no idea what the technical aspects are, but it boils down to Flash and Epiphany not liking each other.  I used the following series of commands:
> sudo apt-get purge flashplugin-nonfree flashplugin-installer gnash gnash-common mozilla-plugin-gnash swfdec-mozilla
 sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
 sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
 sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
 sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
 rm -f ~/.mozilla/plugins/*flash*so

2 - Then I installed gnash through symantic, and the 'Browser-plugin-gnash' package.

3 - This still didn't work, but after putting a check against the HTML5TUBE plugin on Epiphany (TOOLS > PLUGINS > check the box that says HTML5TUBE).  I'd checked and unchecked this box a million times over the last few days, but finally seemed to have got everything right ... Success!!

---

### Post by rolfijn on 2012-03-05
I don't think the issue is resolved. HTML5 Youtube works for most videos without any flash plugin at all (be it adobe, gnash, lightspark or whatever...). HTML5 Youtube can be enabled through [www.youtube.com/html5](www.youtube.com/html5), which I think is the same as enabling the HTML5tube extension. 

I have the same problem as the original poster. I can view most videos on [www.youtube.com](www.youtube.com) and [www.vimeo.com](www.vimeo.com) through html5. Some videos enforce sponsoring and need flash (on youtube at least...). Grooveshark.com complains there's no flash available when I have "Enable Plugins" **disabled** in the  privacy tab of the options dialog and works when I enable this option. So, it seems that flash is available within epiphany, just not for video.

---

### Post by missmoondog on 2012-03-26
as much of a pain as flash can be, almost still have to have it sometimes, at least. 

you mean it is possible to get flash to work in epiphany? never thought i'd hear of the day!

epiphany could be a killer browser, just for the simplicity of it, but it always seems to be a day late and dollar short in areas you need it to work.

---

### Post by mdye on 2012-09-13
Why is this thread marked SOLVED? It's not solved at all - people want to use *Flash* which is not just used in YouTube.  It's awesome that YouTube is using HTML5 - would that *everyone* were doing that (e.g., Hulu, etc.) But they just don't.  At the risk of sounding snarky, I'm pretty sure GNOME and KDE people don't actually ever use the internet (though, to be fair, Epiphany has improved a *lot* - you can now use Google Drive. I never thought I'd see the day when it was that useful.)  If the Epiphany developers could just address the gaping holes in this nice application it'd be great.

---

### Post by vasa1 on 2012-09-14
> **mdye said:**
> ...  If the Epiphany developers could just address the gaping holes in this nice application it'd be great.
You could start your own thread with specifics.

---

### Post by claracc on 2012-09-14
> **mdye said:**
> Why is this thread marked SOLVED? It's not solved at all - people want to use *Flash* which is not just used in YouTube.  It's awesome that YouTube is using HTML5 - would that *everyone* were doing that (e.g., Hulu, etc.) But they just don't.  At the risk of sounding snarky, I'm pretty sure GNOME and KDE people don't actually ever use the internet (though, to be fair, Epiphany has improved a *lot* - you can now use Google Drive. I never thought I'd see the day when it was that useful.)  If the Epiphany developers could just address the gaping holes in this nice application it'd be great.


For me it is solved in the web version 3.4.1, with adobe flashplayer 11.2.232.238 and installing nspluginwrapper and nspluginviewer. I can see flash videos with web without any problem.

It is certain, that it has been a long time for epiphany webkit to work with flashplayer, but now they have got.

---

### Post by vasa1 on 2012-09-14
> **claracc said:**
> For me it is solved in the web version 3.4.1, with adobe flashplayer 11.2.232.238 and installing nspluginwrapper and nspluginviewer. I can see flash videos with web without any problem.

It is certain, that it has been a long time for epiphany webkit to work with flashplayer, but now they have got.

@claracc, you may be interested to know that Midori plays Flash without needing the wrapper.

---

### Post by claracc on 2012-09-14
> **vasa1 said:**
> @claracc, you may be interested to know that Midori plays Flash without needing the wrapper.

I didn't know. Thanks.

Do you recommend better to use midori instead epiphany in an old pIII 1GHz CPU, 512 MB ram?.

Is midori using less resources (CPU and ram) than epiphany or are they similar?

---

### Post by vasa1 on 2012-09-14
> **claracc said:**
> I didn't know. Thanks.

Do you recommend better to use midori instead epiphany in an old pIII 1GHz CPU, 512 MB ram?.

Is midori using less resources (CPU and ram) than epiphany or are they similar?

@claracc, I think they're very similar in resource usage but Midori seems more user friendly, AFAICT, and the [Midori QnA at Launchpad]("https://launchpad.net/midori") is decent as well. But, to get the latest, you'll have to install it via its Launchpad ppa (which is what I've done).

I had a problem with Epiphany when I tried to use a custom ad blocker. Another potential concern is that the Epiphany devs are keen to ensure it works primarily with a GNOME environment.

---

### Post by claracc on 2012-09-14
> **vasa1 said:**
> @claracc, I think they're very similar in resource usage but Midori seems more user friendly, AFAICT, and the [Midori QnA at Launchpad]("https://launchpad.net/midori") is decent as well. But, to get the latest, you'll have to install it via its Launchpad ppa (which is what I've done).

I had a problem with Epiphany when I tried to use a custom ad blocker. Another potential concern is that the Epiphany devs are keen to ensure it works primarily with a GNOME environment.

Thankyou. I will try.

---

### Post by The_Cunning_Stunt on 2012-12-30
> **claracc said:**
> For me it is solved in the web version 3.4.1, with adobe flashplayer 11.2.232.238 and installing nspluginwrapper and nspluginviewer. I can see flash videos with web without any problem.

It is certain, that it has been a long time for epiphany webkit to work with flashplayer, but now they have got.
This doesn't work for me

I ran
```
$ sudo apt-get install nspluginwrapper nspluginviewer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia k3b k3b-data k3b-i18n kdevelop-l10n
  kdevelop-php-docs-l10n kdevelop-php-l10n language-pack-kde-en
  libasprintf0c2:i386 libflac++6 libgomp1:i386 libk3b6
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nspluginviewer:i386 nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 202 kB of archives.
After this operation, 583 kB of additional disk space will be used.
Get:1 http://ie.archive.ubuntu.com/ubuntu/ quantal/multiverse nspluginviewer i386 1.4.4-0ubuntu4 [86.0 kB]
Get:2 http://ie.archive.ubuntu.com/ubuntu/ quantal/multiverse nspluginwrapper amd64 1.4.4-0ubuntu4 [116 kB]
Fetched 202 kB in 0s (380 kB/s)      
Selecting previously unselected package nspluginviewer.
(Reading database ... 202461 files and directories currently installed.)
Unpacking nspluginviewer (from .../nspluginviewer_1.4.4-0ubuntu4_i386.deb) ...
Selecting previously unselected package nspluginwrapper.
Unpacking nspluginwrapper (from .../nspluginwrapper_1.4.4-0ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Setting up nspluginviewer (1.4.4-0ubuntu4) ...
Setting up nspluginwrapper (1.4.4-0ubuntu4) ...
plugin dirs:
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
Auto-update plugins from /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins

```

Then I ran
```
$ nspluginwrapper -v -n -a -i
Auto-install plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libcinnamon-browser-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins

```
If I open [this page](http://www.rte.ie/player/ie/show/10098423/), it stills tells me that i need flash

---

