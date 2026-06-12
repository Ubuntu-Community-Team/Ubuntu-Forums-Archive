---
title: "How to install firefox 3.5.1"
date: 2009-07-30
forum: General Help
---

### Post by os56k on 2009-07-30
I have downloaded Firefox 3.5.1 for Linux from Mozilla website.

It is a tar.bz2 file and I extracted it.

Now don't know which file should I execute to install it on my ubuntu 9.04.

---

### Post by aysiu on 2009-07-30
This will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by os56k on 2009-07-30
Thank you but a new problem arose.

I installed and now have firefox 3.5.1 but don't know why I can't view any webpage.

In ubuntu I am connected to internet because my Pidgin works but firefox behaves as if i were not connected.

Also all the menus in the installed version is in my local language (Persian) but I want English. How can I change that ?

---

### Post by prshah on 2009-07-30
> **os56k said:**
> firefox behaves as if i were not connected.

all the menus in the installed version is in my local language (Persian) but I want English. 

Check if you are in offline mode: Click on File, and ensure that "Work Offline" is unselected / unticked / unchecked.

To change your language for webpages use Edit-Preferences-Content-(Language) Choose (last button).

To change the language for your menus, type the following in the address bar```
about:config
``` then "Filter" for ```
useragent
```, then find the value general.useragent.locale and change it to "en-US". I assume that the en-US langauge set is already installed, if not, install it from [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/xpi/)

---

### Post by vinutux on 2009-07-30
Disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.

1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle.
4. Restart your Mozilla application and try again.

---

### Post by lovinglinux on 2009-07-30
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by os56k on 2009-08-02
Thank you all a million for your help. IPv6 was the problem and I disabled it and  also changed my language although had to install en-GB.

I appreciate your help. From  day to day I'm going to love ubuntu more.:popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by colau on 2009-08-12
> **aysiu said:**
> this will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
+1

---

### Post by colau on 2009-08-12
> **aysiu said:**
> This will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
Installed firefox-3.5 running this command
```

if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox 

```

But now i can't find the original firefox icon at the top panel and from Applications>Internet.

dpkg -l | grep firefox
```

ii  firefox-3.5                                3.5~b4~hg20090330r24021+nobinonly-0ubuntu1   safe and easy web browser from Mozilla
ii  firefox-3.5-branding                       3.5~b4~hg20090330r24021+nobinonly-0ubuntu1   Package that ships the firefox branding

```

---

### Post by aysiu on 2009-08-12
You have only Firefox 3.5 installed, which isn't /usr/bin/firefox but /usr/bin/firefox-3.5

If you want the normal Firefox launcher, you should install through Synaptic the *firefox* package, which will be Firefox 3.0.

---

### Post by colau on 2009-08-13
> **aysiu said:**
> You have only Firefox 3.5 installed, which isn't /usr/bin/firefox but /usr/bin/firefox-3.5

If you want the normal Firefox launcher, you should install through Synaptic the *firefox* package, which will be Firefox 3.0.
I did this "sudo apt-get install firefox"
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-3.0 firefox-3.0-branding
Suggested packages:
  ubufox firefox-3.0-gnome-support
The following NEW packages will be installed:
  firefox firefox-3.0 firefox-3.0-branding
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 1159kB of archives.
After this operation, 4002kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com jaunty-security/main firefox-3.0-branding 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com jaunty-security/main firefox-3.0 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com jaunty-security/main firefox 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by colau on 2009-08-13
Bump.

---

### Post by robotsy on 2009-08-13
Same problem as "colau" above me. Have the packages(?) required been removed or something? They always appear as 404 errors to me.

---

