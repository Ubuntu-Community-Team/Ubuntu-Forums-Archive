---
title: "Firefox freezed the entire Ubuntu (10.04) on some website"
date: 2010-10-04
forum: General Help
---

### Post by mark.altern on 2010-10-04
Hi guys, 

I was viewing this website, this evening:
[HTML]http://www.hermanmiller.com/[/HTML]It is a famous chair manufacture, which produce the famous line "Aeron Chairs". When you are on that web page, if you move your mouth to the "product" tag near the top of the page and click on "seating", you will see all their fancy chairs. Then after I click on the first model, I realize my entire ubuntu (10.04) was hung. 

The month can still move, but sluggish and everything else lost responses, including keyboard and gnome panel and etc. And the only thing I can do is a hard reboot. And this problem is reproducible. 

I can't find any error message from .xsession-errors, or dmesg, or syslog, or user.log or any log. 

Is this a known bug for firefox or ubuntu? Does a similar problem ever happen to you? Please help me, any suggestion is appreciated.

---

### Post by mikewhatever on 2010-10-04
The site works for me, Firefox 3.6.10, Karmic.

---

### Post by sikander3786 on 2010-10-04
I've also visited the link and it's working here too.

Is it a new method of marketing/advertisement on the forums? :-) Just joking. LOL.

Is it a single site or you have problems with some other websites too? If so, try disabling ipv6 in firefox. That sometimes causes problems like this.

---

### Post by lovinglinux on 2010-10-04
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

### Post by mark.altern on 2010-10-04
Thanks guys. Yes, it's a new marketing strategy, targeting Linux users who spend most of their day on a chair in front of computer, so they need a good one ](*,)

Joking aside,**_[COLOR=Black] the first thing I thought of is flash, but I have tried rm .mozilla. And with a vanilla firefox, without any ad-on, the same problem remains.[/COLOR]_** But here is the output anyway: 

Please continue to help me, many thanks. :popcorn:

**1. Flash version **
**Shockwave Flash**

 File:  /home/mark/.mozilla/plugins/libflashplayer.soVersion:   Shockwave Flash 10.2 d161[B]

2. Firefox version and architecture[/B]
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

**3. System Info**
> [FONT=monospace]
[/FONT]Ubuntu Architecture 
Linux home 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux 
Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources
globalmenu-team-ppa-lucid.list
globalmenu-team-ppa-lucid.list.save
kde3-maintainers-ppa-lucid.list_backup
lucid-bleed-ppa-lucid.list

Flash packages

Plugin locations

/home/yingwu/.mozilla/plugins/libflashplayer.so


Flash symlinks
/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)[FONT=Verdana]
[/FONT]

---

### Post by mark.altern on 2010-10-04
Also, by the way, I forget to mention the other thing I tried to resolve this problem. 

I reboot my computer with a USB, which has the Ubuntu 10.04.1 (x64) image inside. I clicked the "Try out Ubuntu" to boot into a vanilla ubuntu system with a vanilla firefox. 

Then visiting the same website, the first time it was fine, the second time I visit it again, system hungs, exactly the same problem, sluggish mouth with nothing else responding. 

So the problem is there with a vanilla ubuntu and firefox!! That is when I decide to post it here, asking for help. :(

---

### Post by Dustin2128 on 2010-10-04
hm, does it freeze on, say, chromium?

---

### Post by mark.altern on 2010-10-04
OK, finally I find some error message. You guys should try to visit that website a few more times. Now I have successfully replicate the exact same problem in my computer lab, where all have ubuntu 10.04. 

Here is what I found, when the compute is frozen. I can log in it from another computer remotely while the original one is frozen, where I find the error message in Xorg.0.log
```

[mi] EQ overflowing. The server is probably stuck in an infinite loop.

```
Notice, you can see this error message after you reboot the computer in Xorg.0.log.old too.
[COLOR=DarkRed]
[COLOR=Black]**So it is now confirm that it may be a[COLOR=Red] Xorg[/COLOR] problem or a [COLOR=Red]fundamental firefox [/COLOR]problem[COLOR=Red] (not any Add on problem),[/COLOR] and though it doesn't happen every time, it takes place fairly often and has been replicated in multiple laptops and Dell desktop, with Ubuntu 10.04 installed. **[/COLOR][/COLOR]

---

