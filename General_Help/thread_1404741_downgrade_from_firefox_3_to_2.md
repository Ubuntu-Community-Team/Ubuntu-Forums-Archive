---
title: "downgrade from firefox 3 to 2"
date: 2010-02-11
forum: General Help
---

### Post by 123456789123456789123456 on 2010-02-11
This may have been something simular allready, I don't know.  I can't find the earlier version on firefox web site.  I have a friend, that is going to school, one of the sites requires firefox 2 to download files from, she has firefox 3, but it reports she needs 2 to download, and will not download using 3.  Does the repository wget -c [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases.2.0/linux-i686/en-GB/firefox-2.0.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases.2.0/linux-i686/en-GB/firefox-2.0.tar.gz), still exist?  Or do I have to find it or the deb from torrents or something?

Still may be a way to upgrade the computer and get a newer version of firefox to work with that web site, or possibly a different web browser.

---

### Post by Richard1979 on 2010-02-11
> **123456789123456789123456 said:**
> This may have been something simular allready, I don't know.  I can't find the earlier version on firefox web site.  I have a friend, that is going to school, one of the sites requires firefox 2 to download files from, she has firefox 3, but it reports she needs 2 to download, and will not download using 3.  Does the repository wget -c [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases.2.0/linux-i686/en-GB/firefox-2.0.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases.2.0/linux-i686/en-GB/firefox-2.0.tar.gz), still exist?  Or do I have to find it or the deb from torrents or something?

Still may be a way to upgrade the computer and get a newer version of firefox to work with that web site, or possibly a different web browser.

[http://downloads.sourceforge.net/portableapps/FirefoxPortableLegacy20_2.0.0.20_English.paf.exe](http://downloads.sourceforge.net/portableapps/FirefoxPortableLegacy20_2.0.0.20_English.paf.exe)

It may run in Wine, this is a Windows version.
I think all the installer does is extract the files so you should be good to run in Linux if you need it.
It's a portable version which means it runs from a USB stick or hard disk with no installation required.

---

### Post by gmargo on 2010-02-11
You'd probably be better off installing the Firefox add-on *User Agent Switcher* [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) and masquerade as Firefox-2.

Here's a User-Agent string from an older version of Firefox-2:
```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.14) Gecko/20080419 Ubuntu/8.04 (hardy) Firefox/2.0.0.14
```Configure that as your User-Agent string, and I bet the silly web site starts working.

---

### Post by lovinglinux on 2010-02-11
> **gmargo said:**
> You'd probably be better off installing the Firefox add-on *User Agent Switcher* [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) and masquerade as Firefox-2.

Here's a User-Agent string from an older version of Firefox-2:
```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.14) Gecko/20080419 Ubuntu/8.04 (hardy) Firefox/2.0.0.14
```Configure that as your User-Agent string, and I bet the silly web site starts working.

+1

Installing Firefox 2 is probably not a good idea, in terms of security. BTW, tell your friend to write to the site webmaster and tell him Mozilla ended support for Firefox 2 on 18 December, 2008.

---

### Post by 123456789123456789123456 on 2010-02-19
I aggree that trying to downgrade to 2.0 would not be recomended.  And even so, the problem accuring with blackboard may be fixed/resolved in a later update to firefox.  this sort of thing has accured before with other versions of firefox, as I remember.  I took the suggestion of downloading and using firefox 2 portable pc program, using wine, and it works perfectly.  Granted I had some freez ups, but I was testing it in a virtual machine at the time, and the main computer was running extreamly slow do to a problem with vista which was native OS on the machine.

---

