---
title: "Problems in 10.04"
date: 2010-08-07
forum: General Help
---

### Post by metasonix on 2010-08-07
First a bit of background: I have been running straight 32-bit Ubuntu on this same Shuttle Athlon-equipped PC with 1GB of memory, since version 5.10 in 2005. 

We installed 10.04 on it about 2 months ago. And so far, these are the major annoyances/bugs I have come across, just using it in the daily operations of my business. Otherwise 10.04 is the best version yet, very solid and easy to use. (I really appreciate the new update manager and things like Software Sources and the Ubuntu Software Center.)

1) OpenOffice--when I try to save a simple word-processor file in rtf format, OpenOffice will crash. Then it goes into its recovery process, so when I start it again, I get the workfile back unchanged. But then, when I try to save it as rtf, it does the same thing. Saving in native OO format works fine--just saving in rtf is a problem. And it only happens to certain files. I have not been able to discern a pattern.

2) after doing a lot of cut-pasting of text, occasionally the system will freeze after cutting some text--completely. As in, nothing happens. The screen is no longer updated. I have to do a hard reset. Memory running out? I doubt it. We're only talking a few hundred kB of text at a time, at the very most.

3) and as always, the worst problem is still the Flash player. Nothing causes more problems for Firefox than the damned Flash player. It routinely freezes or crashes the browser, usually during/after playing a video. Flash has been a miserable PITA since I started using Ubuntu. It appears that will never be "fixed" or "improved", and it's obviously Adobe's intransigence, so I can't blame Canonical or the kernel developers.

I'd say something about connecting MIDI or USB music hardware to the PC, but it's probably my own fault for not installing something. Sometimes it works, sometimes not. And both ALSA and Jack are obtuse and difficult to set up. But that's not what I would call a "problem", mostly my own ignorance.

---

### Post by mikewhatever on 2010-08-07
Are you asking for help here or just sharing your experience?

---

### Post by metasonix on 2010-08-07
> **mikewhatever said:**
> Are you asking for help here or just sharing your experience?
A little of both. I found nothing in the 10.04 known-problems thread that I haven't done already. Perhaps someone else has seen such behaviour.

The cut-paste system hanging is very weird, maybe it's a hardware problem but I doubt it--8.04 and 6.10 didn't do that, and we ran them on the exact same hardware....

---

### Post by mikewhatever on 2010-08-07
> **metasonix said:**
> ...

1) OpenOffice--when I try to save a simple word-processor file in rtf format, OpenOffice will crash. Then it goes into its recovery process, so when I start it again, I get the workfile back unchanged. But then, when I try to save it as rtf, it does the same thing. Saving in native OO format works fine--just saving in rtf is a problem. And it only happens to certain files. I have not been able to discern a pattern.

2) after doing a lot of cut-pasting of text, occasionally the system will freeze after cutting some text--completely. As in, nothing happens. The screen is no longer updated. I have to do a hard reset. Memory running out? I doubt it. We're only talking a few hundred kB of text at a time, at the very most.

3) and as always, the worst problem is still the Flash player. Nothing causes more problems for Firefox than the damned Flash player. It routinely freezes or crashes the browser, usually during/after playing a video. Flash has been a miserable PITA since I started using Ubuntu. It appears that will never be "fixed" or "improved", and it's obviously Adobe's intransigence, so I can't blame Canonical or the kernel developers.


1. RTF is not OO's native format. Why not use ODT instead?

2. You should check the state of RAM usage. Use the **free -m** command, htop or the System Monitor.

3. The latest version of both flash a Firefox are actually pretty stable. Is there any particular site that causes problems?

---

### Post by darolu on 2010-08-07
Problem 1 seems to be a bug, when I find this kind of trouble I usually solve them by re-instaling some fonts, maybe your pattern is a certain typography too. For your second problem, does it happens with OOo too? or with any application? seems to be a memory leak, and considering Bug #1 I wouldn't doubt they are related. I can't help much with these ones.

As for our 'beloved' flash plug-in, yes it is very unstable; I wish I was like mikewhatever and had a stable flash plug in and a fast firefox (I find it terribly slow, specially with javascript). I know GNash (free flash-plug in) is actively developed, maybe the newest version is stable and functional enough to use it instead of Adobe's plug in, give it a try. My recommendation is to use a different browser though, flash crashes less often in chromium-browser for me, it's pretty neat, you may like it.

---

### Post by metasonix on 2010-08-07
> **mikewhatever said:**
> 1. RTF is not OO's native format. Why not use ODT instead?
Some of the documents have to be sent to third parties, who usually don't have OO. RTF seems to be the safest way to send things so they look more-or-less as intended. (Saving in Word .doc format? I would do that but people have complained they can't open them in whatever random old version of Word they are using.)

> 2. You should check the state of RAM usage. Use the **free -m** command, htop or the System Monitor.
Tried that--no change in memory usage caused by cut-pasting. 

> 3. The latest version of both flash a Firefox are actually pretty stable. Is there any particular site that causes problems?
Nope, happens on any site with YouTube or other videos. I just updated the system, and am running Firefox 3.6.8 and Flash 10,1,53,64.

We can live with these problems, they're just more annoying and obscure than anything else. Hopefully someone else has seen this.

(Almost forgot---whenever starting Media Player, the screen blanks completely for about half a second, then it comes back as before, but with the media file playing. It's a generic Intel chipset video interface, not Nvidia or ATI.)

---

### Post by dino99 on 2010-08-07
most of the time there are usefull errors logged, use them to go ahead

---

### Post by lovinglinux on 2010-08-07
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://lh5.ggpht.com/_EPRFmO0pKhs/TFi0kGosJvI/AAAAAAAAAig/GNswcyQC75Y/s400/About_Plugins.jpg[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be locates at the bottom of the info dialog:

[IMG]http://lh5.ggpht.com/_EPRFmO0pKhs/TFi0kqRSPaI/AAAAAAAAAik/G3M3J5mmDOo/s400/Firefox_Version.jpg[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by metasonix on 2010-08-08
As you wish........

My Flash plugin info:

Shockwave Flash

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

****************

My Firefox info:

Ubuntu Architecture

Linux metasonix-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-08-08
I don't see anything wrong with your Flash and Firefox installations, so I would recommend creating a new Firefox profile to test if it works properly. If not, then create a new Ubuntu test user to see if the problem persists.

To create a new FF profile, use the Profile Manager:

```
firefox -P
```

---

### Post by The Chef on 2011-05-13
I had this problem too, with a 64 bit i5 Intel Shuttle.  It would crash all the time when there was flash running.  The precise symptom was that the whole screen would go very dark and the whole Gnome desktop and panels would disappear and you could just make out the cursor, but it would not react to mousing.  I would have to power off with the front panel switch.  This would happen about 1 to 2 times a week under normal personal use.

I think (touch wood) that I fixed it.  In Bios, I set IGD Graphics Mode to 64 MB (the lowest) and DVMT Memory to 128 MB (the lowest) and Internal HDMI to "Enabled" (which I think is default).  I have had hundreds of hours of processing since with no crash.  I can still edit HD video and have not noticed any performance effects -- but I am not a gamer.

I wonder whether some combination of the Ubuntu graphics driver, the i5 onboard graphics processing and the Shuttle Bios (AMIBIOS v104 build 7/27/10) is the cause.  The very same machine never displayed this problem with Windows 7 (64 bit) and the higher IGD/DVMI settings.  So, I do not believe the issue is just Bios/Processor.

---

