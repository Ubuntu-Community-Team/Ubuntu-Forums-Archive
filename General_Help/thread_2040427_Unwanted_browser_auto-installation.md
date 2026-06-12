---
title: "Unwanted browser auto-installation"
date: 2012-08-11
forum: General Help
---

### Post by awfullook on 2012-08-11
Hi,

Lubuntu 12.04 64bit

I recently installed Chrome from a downloaded .deb package, it works fine, so removed Lubuntu's default browser Chromium with:

```
sudo apt-get autoremove --purge chromium-browser
```

After confirming with 'Y' I walked off, later returning to find that Firefox had been automatically installed as a replacement! Upon trying to remove Firefox in the same way I notice that the terminal prompt is now telling me Epiphany must be installed?

How can I remove Firefox without auto-installing another unwanted browser?

```

rory@rong:~$ sudo apt-get autoremove --purge firefox
[sudo] password for rory: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  epiphany-browser epiphany-browser-data gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gstreamer-0.10 gir1.2-json-1.0 gnome-js-common
  gnome-user-guide libavahi-gobject0 libclutter-1.0-0 libclutter-1.0-common
  libcogl-common libcogl-pango0 libcogl9 libjavascriptcoregtk-3.0-0
  libjson-glib-1.0-0 libseed-gtk3-0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libyelp0 yelp yelp-xsl
Suggested packages:
  epiphany-extensions
The following packages will be REMOVED:
  firefox* firefox-globalmenu*
The following NEW packages will be installed:
  epiphany-browser epiphany-browser-data gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gstreamer-0.10 gir1.2-json-1.0 gnome-js-common
  gnome-user-guide libavahi-gobject0 libclutter-1.0-0 libclutter-1.0-common
  libcogl-common libcogl-pango0 libcogl9 libjavascriptcoregtk-3.0-0
  libjson-glib-1.0-0 libseed-gtk3-0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libyelp0 yelp yelp-xsl
0 upgraded, 23 newly installed, 2 to remove and 2 not upgraded.
Need to get 17.5 MB of archives.
After this operation, 34.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Thanks.

---

### Post by PhantomTurtle on 2012-08-11
The answer to your question as to why epiphany is being installed can be found here - [http://askubuntu.com/questions/11934/why-does-removing-firefox-install-another-browser]("http://askubuntu.com/questions/11934/why-does-removing-firefox-install-another-browser").

> If uninstalling firefox installs epiphany, then that's because some other package depends on "a web browser", which packages do by depending on the virtual package www-browser. If the google-chrome package doesn't have a Provides: www-browser line, and you have no other browser installed, APT thinks it needs to install a package that does provide a www-browser and then Epiphany is the first choice on a GNOME system.

I downloaded one of the Google Chrome .deb files and I can confirm that they don't provide www-browser. If you want to get this fixed you need to file a bug report with Google and tell them to fix their .deb packages.

It seems that you have no choice. I would just keep Firefox installed. It won't make a big difference and as long as you have Chrome as the default, you probably won't even see Firefox again. So you have to have at least one and I think that it is better to keep Firefox than remove it and have it replaced by epiphany.

---

### Post by awfullook on 2012-08-11
Aha! Thank you for your concise and precise answer. I will just leave firefox and mark this thread solved.

Regardo.

Rory.

---

### Post by MG&amp;TL on 2012-08-11
> **awfullook said:**
> Aha! Thank you for your concise and precise answer. I will just leave firefox and mark this thread solved.

Regardo.

Rory.


I'd just like to point out that this isn't Ubuntu's fault, chrome should provide a line in their package config that says 'I'm a browser, you don't need to install another one', but it doesn't. :(

---

### Post by vasa1 on 2012-09-21
> **MG&TL said:**
> I'd just like to point out that this isn't Ubuntu's fault, chrome should provide a line in their package config that says 'I'm a browser, you don't need to install another one', but it doesn't. :(
I think matters are slightly more complicated than what Google Chrome provides or doesn't.
Since OP has marked this thread [SOLVED], I'll start a new one in a little while.

Here: [http://ubuntuforums.org/showthread.php?p=12252422#post12252422](http://ubuntuforums.org/showthread.php?p=12252422#post12252422)

---

