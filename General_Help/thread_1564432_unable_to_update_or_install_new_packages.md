---
title: "unable to update or install new packages"
date: 2010-08-30
forum: General Help
---

### Post by whtvr on 2010-08-30
Hi,

I seem to have a problem with updating my system (Ubuntu 10.04 x64 on Thinkpad x200s) and installing new packages. Every time I try to run Synaptic Manager, apt-get from the terminal or try update the system I either get the following message:

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```or

```

dpkg: status database area is locked by another process

```The latter message appears even if there's no other instance of apt running anywhere (i.e. just after reboot).


When I try to run 'sudo dpkg --configure -a' I either get the message about dpkg database being locked (as above) or it starts doing something and then gets stuck on:

```
Setting up firefox (3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2~lucid) ...
```I tried to clear the cache by deleting everything from /var/cache/apt and /var/cache/apt/archives but that didn't help. I also tried to remove the mozilla ppa (and all other 3rd party repositories) but after I run apt-get update I get one of the above messages so I'm kind of stuck.

Let me know if I omitted any relevant information/details. Any advice much appreciated.

---

### Post by realzippy on 2010-08-30
*"dpkg: status database area is locked by another process"*

...that could only be apt-get,aptitude,synaptic, aso.

```
sudo fuser -vki /var/lib/dpkg/lock
```

shows this process.

Any process running of those?There can only be 1 instance,but you might know this.

---

### Post by 13east on 2010-08-30
it seems that a previous update might have been interrupted for firefox... have you tried removing firefox completely and than installing it over again, or even trying the open source non-branded version of firefox (package name: awebbrowser)?

---

### Post by whtvr on 2010-08-30
thanks for the replies guys!

ok, so when I issue 'sudo fuser -vki /var/lib/dpkg/lock' i get this:

```
                     USER        PID ACCESS COMMAND
/var/lib/dpkg/lock:  root       3550 f.... dpkg
Kill process 3550 ? (y/N) 

```and when I kill it and try 'sudo dpkg --configure -a' again i'm back to square one - "Setting up firefox [...]"

I tried removing firefox but I can't do that since neither synaptic nor apt-get works for me...

---

### Post by whtvr on 2010-08-31
ok, so I looked around and for some people with a similar problem 'sudo apt-get -f install' seemed to work... not for me though, as i get the following

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```'sudo dpkg --configure -a' obviously doesn't work (see my previous posts)...

does anybody have any more ideas how to fix this? thanks in advance

---

### Post by realzippy on 2010-08-31
So 


```
sudo apt-get update
```

could not run either?

---

### Post by whtvr on 2010-08-31
'sudo apt-get update' gives me good old

```
E: Archive directory /var/cache/apt/archives/partial is missing.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by realzippy on 2010-08-31
And if you create it?

```
sudo mkdir /var/cache/apt/archives/partial

```

---

### Post by whtvr on 2010-08-31
if i create the folder manually and issue 'sudo apt-get update' i get

```
Hit http://ftp.heanet.ie lucid Release.gpg
Ign http://ftp.heanet.ie/pub/ubuntu/ lucid/main Translation-en_IE
Hit http://ftp.heanet.ie lucid-updates Release.gpg
Ign http://ftp.heanet.ie/pub/ubuntu/ lucid-updates/main Translation-en_IE
Hit http://ftp.heanet.ie lucid-security Release.gpg
Ign http://ftp.heanet.ie/pub/ubuntu/ lucid-security/main Translation-en_IE
Hit http://ftp.heanet.ie lucid Release
Hit http://ftp.heanet.ie lucid-updates Release 
Hit http://ftp.heanet.ie lucid-security Release
Hit http://ftp.heanet.ie lucid/main Packages   
Hit http://ftp.heanet.ie lucid-updates/main Packages
Hit http://ftp.heanet.ie lucid-security/main Packages
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```and few seconds later a window pops up saying "Not all updates can be installed. Run a partial upgrade, to install as many updates as possible", if i try to run partial update I either get the message about dpkg lock (which I now know how to get around) or it tries to run the update but fails again and gets stuck on that firefox package... is there any other place beside /var/cache/apt where that firefox package could be? i presume it's broken and that's what causing the whole issue....

---

### Post by realzippy on 2010-08-31
this order ?:

```
sudo mkdir /var/cache/apt/archives/partial
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

---

### Post by whtvr on 2010-08-31
'sudo dpkg --configure -a' just give me

```

Setting up firefox (3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2~lucid) ...

```and gets stuck on it, 'sudo apt-get -f install' tells me to run 'sudo dpkg --configure -a'...

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[1]+  Killed                  sudo dpkg --configure -a

```and finally 'sudo apt-get update' produces

```

Hit http://ftp.heanet.ie lucid Release.gpg
Ign http://ftp.heanet.ie/pub/ubuntu/ lucid/main Translation-en_IE
Hit http://ftp.heanet.ie lucid-updates Release.gpg
Ign http://ftp.heanet.ie/pub/ubuntu/ lucid-updates/main Translation-en_IE
Hit http://ftp.heanet.ie lucid-security Release.gpg
Ign http://ftp.heanet.ie/pub/ubuntu/ lucid-security/main Translation-en_IE
Hit http://ftp.heanet.ie lucid Release
Hit http://ftp.heanet.ie lucid-updates Release 
Hit http://ftp.heanet.ie lucid-security Release
Hit http://ftp.heanet.ie lucid/main Packages   
Hit http://ftp.heanet.ie lucid-updates/main Packages
Hit http://ftp.heanet.ie lucid-security/main Packages
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

seems like a blind circle...

thanks for your help realzippy

---

### Post by realzippy on 2010-08-31
What about purging firefox?

```
sudo apt-get --purge remove firefox*
```

---

### Post by whtvr on 2010-08-31
same story... "manually run 'sudo dpkg --configure -a' to correct the problem."

---

### Post by realzippy on 2010-08-31
..last ideas before I am out of those:

1.disabling search for new hardwaredrivers and update-notifier in *Startup Applications*,reboot..

..then there should be no dpkg process running,right?So:
*sudo fuser -vki /var/lib/dpkg/lock*
should show nothing.What means that *synaptic* should open...
then reinstalling the firefox stuff..
2.if same doom loop occurs I would start recovery mode,drop to root shell and see what
happens there when updating apt-get & co...good luck.

Edit:
you could have a look at the */var/lib/dpkg/status* file,search for *Package: firefox*
maybe there is something about it's status;

---

### Post by whtvr on 2010-09-02
Hiya,

So I tried to run 'sudo dpkg --configure -a' in the recovery mode but again got stuck on Firefox... 

About the */var/lib/dpkg/status *file - anything in particular I should be looking at?

Thanks everybody for your input, I really appreciate that. I think I'm just going to ignore the problem for another month or so and go for 10.10 when it comes out. Unless anybody has any more ideas how to deal with this....

---

### Post by realzippy on 2010-09-02
[I]About the /var/lib/dpkg/status file - anything in particular I should be looking at?
[/I]
search the file for the term:

*Package: firefox*

then check it's status   e.g.  "installed"......

If you delete (make backup!!)or "comment out" all firefox stuff there,apt should not know about it
(only an idea,I do not exactly know!!!),maybe it is worth a test.

**Edit:**
Tested it here,means I deleted:

[I]Package: firefox
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 36644
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
Replaces: firefox-2, firefox-2-dom-inspector, firefox-2-libthai, firefox-3.0, firefox-3.5, firefox-3.6, firefox-3.6-gnome-support
Provides: firefox-2, firefox-2-dom-inspector, firefox-2-libthai, firefox-3.0, firefox-3.5, firefox-3.6, www-browser
Depends: fontconfig, psmisc, lsb-release, debianutils (>= 1.16), libasound2 (>> 1.0.22), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.18.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.6), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.1.1), libx11-6 (>= 0), libxext6, libxrender1, libxt6, zlib1g (>= 1:1.1.4), firefox-branding | abrowser-branding
Recommends: ubufox
Suggests: firefox-gnome-support (= 3.6.8+build1+nobinonly-0ubuntu0.10.04.1), kmozillahelper (>= 0.6), latex-xft-fonts, libthai0
Conflicts: firefox-2 (<< 3), firefox-2-dom-inspector (<< 3), firefox-2-libthai (<< 3), firefox-3.0 (<< 3.6~hg20100117r33523), firefox-3.5 (<< 3.6~hg20100117r33523), firefox-3.6 (<< 3.6~hg20100117r33523), firefox-3.6-gnome-support (<< 3.6~hg20100117r33523)
Conffiles:
 /etc/apparmor.d/usr.bin.firefox 33968ed5f58af6dacef565039e8ab7ec
 /etc/firefox/profile/bookmarks.html 0a2756fccbc1f9b90fa1200e7120db8d
 /etc/firefox/profile/localstore.rdf ea03cc19c2a3f622fa557cd8ea9da6eb
 /etc/firefox/profile/prefs.js 99940ecd258d83b3355ab06fca0ffddb
 /etc/firefox/profile/mimeTypes.rdf 6047f42624d9930caa8d651fa94d28f1
 /etc/firefox/profile/chrome/userChrome-example.css c63733eef9d337c86e6609bcc478a668
 /etc/firefox/profile/chrome/userContent-example.css d3765c7d2de5626529195007f4b7144a
 /etc/firefox/pref/firefox.js d1bcb630df08ddce608a6aa8f4976d35
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}[/I]

 from the file;apt "thinks" it is not installed...

---

