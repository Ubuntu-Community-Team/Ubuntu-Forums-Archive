---
title: "FireFox problems"
date: 2010-08-21
forum: General Help
---

### Post by harecanada on 2010-08-21
I downloaded Fire Fox 3.6.9pre. Having too many problems. Is there a simple way to go back to an earlier version and keep my current settings?

---

### Post by lovinglinux on 2010-08-21
First of all, how did you get Firefox 3.6.9pre?

If you installed a PPA repository like *ubuntu-mozilla-daily*, then go to "System >> Software Sources >> Other Software" and disable it. The re-install Firefox with the command below:

```
sudo apt-get install --reinstall firefox 
```

Your settings won't be affected.

---

### Post by harecanada on 2010-08-22
Hi lovinglinux,

I don't know how I got 3.6.9pre. You know how it goes. I was messing around and ended up with it.
I tried "System >> Software Sources >> Other Software"  but there is no tab that says Other Software
What do you suggest?

---

### Post by lovinglinux on 2010-08-22
> **harecanada said:**
> Hi lovinglinux,

I don't know how I got 3.6.9pre. You know how it goes. I was messing around and ended up with it.

I advise to make notes of anything you change in your system and understand what they do and how you can revert before applying anything.

> **harecanada said:**
> I tried "System >> Software Sources >> Other Software"  but there is no tab that says Other Software
What do you suggest?

Check if you have a "Third-party..." tab. You should see something like this:

[IMG]http://tinyurl.com/26by7te[/IMG]

Remove the entry inside the circle.

---

### Post by harecanada on 2010-08-23
Hi lovinglinux,
I removed that line then tried sudo apt-get install --reinstall firefox
This is what I got:

harecanada@harecanada-desktop:~$ sudo apt-get install --reinstall firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of firefox is not possible, since it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harecanada@harecanada-desktop:~$ 

What does this mean?

---

### Post by lovinglinux on 2010-08-23
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installation, so I don't need to guess what might be happening to your system:


**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**2 - System Info**

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
firefox ~/Desktop/firefox-report.txt
```

---

### Post by harecanada on 2010-08-24
Here's what I got:

1] Mozilla/5.0 (X11; U; Linux x86_64; en-US; 
rv:1.9.2.9pre) Gecko/20100820 Ubuntu/9.04 (jaunty) Namoroka/3.6.9pre

2]Ubuntu Architecture

Linux harecanada-desktop 2.6.28-19-generic #64-Ubuntu SMP Wed Aug 18 21:59:08 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Firefox Packages

firefox                        install
firefox-3.0                    install
firefox-3.5                    deinstall
firefox-3.5-branding                install
firefox-3.5-gnome-support            install
firefox-3.6                    install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9pre/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
opera.list
opera.list.distUpgrade
opera.list.save
playonlinux.list
playonlinux.list.distUpgrade
playonlinux.list.save

What's this mean?

---

### Post by lovinglinux on 2010-08-24
Run these to remove all FF versions and install the default again:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get purge firefox-3.5
sudo apt-get purge firefox-3.6
sudo apt-get install firefox
```

---

### Post by harecanada on 2010-08-24
Ok, I did this and now I have 3.6.8. However, video won't work. Youtube and other video on other sites won't run. What do you think that might be?

---

### Post by lovinglinux on 2010-08-24
Please post the flash version data from Firefox again.

---

### Post by lovinglinux on 2010-08-24
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by harecanada on 2010-08-24
Thought I should add this. When I tried Quicktime Movie Trailers I was sent to one of the movie sites and when I clicked on "Watch Trailer" I got booted off the net.

---

### Post by harecanada on 2010-08-24
Flash aid helped. I got Youtube and some other sites videos working. Quicktime still boots me off the net and some other sites with video won't work. Any other pointers?

---

### Post by harecanada on 2010-08-24
Also, I downloaded Media Player Conectivity and Default User Agent for Fire Fox but don't know how to use them

---

### Post by lovinglinux on 2010-08-24
> **harecanada said:**
> Flash aid helped. I got Youtube and some other sites videos working. Quicktime still boots me off the net and some other sites with video won't work. Any other pointers?

See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

> **harecanada said:**
> Also, I downloaded Media Player Conectivity and Default User Agent for Fire Fox but don't know how to use them

[http://membres.multimania.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html](http://membres.multimania.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html)

[http://chrispederick.com/work/user-agent-switcher/help/](http://chrispederick.com/work/user-agent-switcher/help/)

---

### Post by harecanada on 2010-08-25
Well I got a lot of the video stuff working. Apple Quicktime Trailers will not work. 
lovinglinux I appreciate all your help on all this. I think I'm out of luck on the movie trailers but I'll keep trying and let you know if I figure it out unless you have any more ideas?

---

### Post by lovinglinux on 2010-08-25
> **harecanada said:**
> Well I got a lot of the video stuff working. Apple Quicktime Trailers will not work. 
lovinglinux I appreciate all your help on all this. I think I'm out of luck on the movie trailers but I'll keep trying and let you know if I figure it out unless you have any more ideas?

See the troubleshooting section of that tutorial. There is a fix for quicktime that might help.

---

