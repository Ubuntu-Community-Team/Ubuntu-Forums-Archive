---
title: "Flash playing problems"
date: 2010-12-14
forum: General Help
---

### Post by foofi22 on 2010-12-14
I'll try and describe this so it makes some sense...

I'm running 10.04, FF 3.6.13

If I open FF by clicking the icon I can watch Youtube videos fine, but Dailymotion videos (as an example of many) do not load (just a black screen)

If I run sudo firefox, then videos work on Dailymotion etc fine.

What is going wrong?

(Ubuntu newbie)

---

### Post by Dex73 on 2010-12-14
Is the page not loading at all or is it just the video.

If it's just the video, check the basics. I know it takes a lot longer for my computer to even start videos from daily motion, you may need to wait longer. If that doesn't work look for buttons to play with. Also, if you have any flashblock apps installed it will interfere and may only do this for select websites. Finally make sure all you plugins are up to date. 

Try that stuff first if you haven't already.

---

### Post by io5cml4z on 2010-12-14
How/where did you install flash? If you installed it via synaptic, try reinstalling it. If you're running 64-bit and you downloaded adobe flash player square, make sure the directory the plugin is in has the correct privileges and that the file is accessible to your user. :)

---

### Post by lovinglinux on 2010-12-15
First of all, you should never run Firefox with sudo. You just made things worse by doing that.

To fix that, see the first item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

To fix Flash, see [this]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html") and [this]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html").

---

### Post by foofi22 on 2010-12-15
Thanks for the replies.

Dex - the page loads fine, it's the video pane that just stays black (no controls etc appear either).  I have waited a  long time and nothing happened!

Hoot - I installed Flash from the Ubuntu Software Centre (Adobe Flash 10).  It's a 32-bit machine, I was thinking it was something to do with privileges but I exhausted my knowledge messing around with it.

lovinglinux - I'll give those suggestions a try tonight and post what happens here.

Thanks everyone.

---

### Post by foofi22 on 2010-12-15
> **lovinglinux said:**
> First of all, you should never run Firefox with sudo. You just made things worse by doing that.

To fix that, see the first item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

To fix Flash, see [this]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html") and [this]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html").

Well unfortunately that hasn't worked.

Flash is still working on Youtube, but not on Dailymotion (initially it came up with a black box but now even that doesn't appear).  

It works when using gksudo, although FF looks completely different (ie no bookmarks, plugins etc)

I've installed FLASH-AID too but that hasn't fixed it either

---

### Post by lovinglinux on 2010-12-15
> **foofi22 said:**
> Well unfortunately that hasn't worked.

Flash is still working on Youtube, but not on Dailymotion (initially it came up with a black box but now even that doesn't appear).  

It works when using gksudo, although FF looks completely different (ie no bookmarks, plugins etc)

I've installed FLASH-AID too but that hasn't fixed it either

Disable Ubuntu Firefox Modifications extension.

---

### Post by foofi22 on 2010-12-15
> **lovinglinux said:**
> Disable Ubuntu Firefox Modifications extension.

Disabled it and had no effect...

---

### Post by lovinglinux on 2010-12-15
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


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

### Post by foofi22 on 2010-12-15
```
File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102
```

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.04 (lucid) Firefox/3.6.13
```

```
Ubuntu Architecture

Linux matt-laptop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.0					deinstall
firefox-3.5					deinstall
firefox-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

akirad.list
opera.list
opera.list.distUpgrade

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/home/matt/.limewire/browser/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

---

### Post by lovinglinux on 2010-12-15
> **foofi22 said:**
> ```
File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102
```


Try the beta version from Adobe.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by foofi22 on 2010-12-16
> **lovinglinux said:**
> Try the beta version from Adobe.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Unfortunately that's not improved it - still the same performance (assuming I did it right)

From about:plugins

    File: /usr/lib/mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 10.2 d151

---

### Post by gradinaruvasile on 2010-12-16
Are you sure you dont have gnash installed?

---

### Post by foofi22 on 2010-12-16
> **gradinaruvasile said:**
> Are you sure you dont have gnash installed?

As far as I can tell, gnash is not installed.

---

### Post by foofi22 on 2010-12-20
Anyone any more ideas?  Thanks

---

