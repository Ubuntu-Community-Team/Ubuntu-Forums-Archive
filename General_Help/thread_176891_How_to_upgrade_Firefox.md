---
title: "How to upgrade Firefox?"
date: 2006-05-15
forum: General Help
---

### Post by yusufm on 2006-05-15
I just installed ubuntu and ran the system upgrade, which upgraded my
firefox version from 1.0.7 to 1.0.8. How do I upgrade it to the latest
firefox version?? I tried to run the check for upgrades in firefox
itself, but it doesn't say that there are any available updates...

I also tried to uninstall firefox, so I could just download it again, but when I tried to uninstall, it said a bunch of things depended on it and it seemed like a very bad idea to go ahead with the uninstall...

Thanks.

---

### Post by morbid_bean on 2006-05-15
[QUOTE=yusufm]I just installed ubuntu and ran the system upgrade, which upgraded my
firefox version from 1.0.7 to 1.0.8. How do I upgrade it to the latest
firefox version?? I tried to run the check for upgrades in firefox
itself, but it doesn't say that there are any available updates...

I also tried to uninstall firefox, so I could just download it again, but when I tried to uninstall, it said a bunch of things depended on it and it seemed like a very bad idea to go ahead with the uninstall...

Thanks.[/QUOTE]


When i upgraded mine i used this........... [http://www.psychocats.net/ubuntu/firefox.php](http://www.psychocats.net/ubuntu/firefox.php)   worked great.

---

### Post by aysiu on 2006-05-15
Do not uninstall Firefox.

Use this script to update it, though:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by fer5437 on 2006-05-15
You can try search in the forum. Try this link it have show how to install firefox 1.5.0.2
[http://ubuntuforums.org/showthread.php?t=165655&highlight=mozilla]("http://ubuntuforums.org/showthread.php?t=165655&highlight=mozilla")

---

### Post by yusufm on 2006-05-15
[QUOTE=aysiu]Do not uninstall Firefox.

Use this script to update it, though:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)[/QUOTE]
Thanks. Good reply.

---

### Post by easyease on 2006-05-15
you could always go here and download the new firefox....
 [http://klik.atekon.de/](http://klik.atekon.de/)
No need to uninstall the old version, ive got both 1.5 and the standard ubuntu issue firefox on my system......no conflicts at all.

---

### Post by aysiu on 2006-05-15
[QUOTE=easyease]you could always go here and download the new firefox....
 [http://klik.atekon.de/](http://klik.atekon.de/)[/QUOTE] Klik is a pretty cool tool. Keep in mind that it is by itself a separate program that needs installing: > To quickly prepare your system for klik, install the klik client: wget klik.atekon.de/client/install -O -|sh  and follow instructions on screen. (K)Ubuntu users, please also run sudo apt-get install binutils libstdc++5 rpm.

---

### Post by radinator on 2006-05-15
I just did this (with the script) and am getting a host of errors.  What's missing?

Thanks,
Ray

```
rswartz@hellmouth:~/Desktop$ firefox

(firefox-bin:10583): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:10583): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:10583): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/opt/firefox/run-mozilla.sh: line 131: 10583 Aborted                 "$prog" ${1+"$@"}
rswartz@hellmouth:~/Desktop$
```

---

### Post by aysiu on 2006-05-15
Are you trying to install an x86 Firefox on a 64-bit Ubuntu installation?

---

### Post by radinator on 2006-05-15
*slap the forehead*

My personal Homer Simpson moment.  You called it exactly.  Thanks!

---

### Post by aysiu on 2006-05-15
You may want to take a look at SwiftFox.

---

### Post by Zeno50 on 2006-05-16
Anyway to do this with the new Bon Echo Firefox?  (it's the latest alpha)

---

### Post by aysiu on 2006-05-16
[QUOTE=Zeno50]Anyway to do this with the new Bon Echo Firefox?  (it's the latest alpha)[/QUOTE] I don't think the latest Bon Echo has an AMD64 build:

[http://developer.mozilla.org/devnews/index.php/2006/05/12/bon-echo-alpha-2-milestone/](http://developer.mozilla.org/devnews/index.php/2006/05/12/bon-echo-alpha-2-milestone/)

---

### Post by Zeno50 on 2006-05-16
Sorry, I wasn't the author of the parent.  I don't have an AMD64 and was just curious if there was an easy way to try the Bon Echo.

---

### Post by aysiu on 2006-05-16
[QUOTE=Zeno50]Sorry, I wasn't the author of the parent.  I don't have an AMD64 and was just curious if there was an easy way to try the Bon Echo.[/QUOTE] Sure. I haven't tested this, but this should work. Just download the attached text file to your desktop and then paste these commands into the terminal: ```
cd ~/Desktop
mv installbonechoalpha2.sh.txt installbonechoalpha2.sh
chmod +x installbonechoalpha2.sh
./installbonechoalpha2.sh
```

---

### Post by Zeno50 on 2006-05-16
Works great!  Thank you!

---

### Post by visvak on 2006-07-01
not working. its perenially stuck at 

```
Downloading Firefox from the Mozilla site

--09:05:30--  http://130.239.18.165/pub/mozilla.org/firefox/releases/bonecho/alp ha2/linux-i686/en-US/bonecho-alpha2.tar.gz
           => `bonecho-alpha2.tar.gz'
Connecting to 130.239.18.165:80... failed: Connection timed out.
Retrying.

--09:08:40--  http://130.239.18.165/pub/mozilla.org/firefox/releases/bonecho/alpha2/linux-i686/en-US/bonecho-alpha2.tar.gz
  (try: 2) => `bonecho-alpha2.tar.gz'
Connecting to 130.239.18.165:80...

```

any alternate source for download ?

---

### Post by aysiu on 2006-07-02
[QUOTE=visvak]not working. its perenially stuck at 

```
Downloading Firefox from the Mozilla site

--09:05:30--  http://130.239.18.165/pub/mozilla.org/firefox/releases/bonecho/alp ha2/linux-i686/en-US/bonecho-alpha2.tar.gz
           => `bonecho-alpha2.tar.gz'
Connecting to 130.239.18.165:80... failed: Connection timed out.
Retrying.

--09:08:40--  http://130.239.18.165/pub/mozilla.org/firefox/releases/bonecho/alpha2/linux-i686/en-US/bonecho-alpha2.tar.gz
  (try: 2) => `bonecho-alpha2.tar.gz'
Connecting to 130.239.18.165:80...

```

any alternate source for download ?[/QUOTE] Well, since I wrote that over a month ago, you might want to try this source:
[http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/bonecho/alpha2/linux-i686/en-US/bonecho-alpha2.tar.gz](http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/bonecho/alpha2/linux-i686/en-US/bonecho-alpha2.tar.gz)

---

### Post by visvak on 2006-07-02
hey this is only alpha 2 is it ? is there anyway to get alpha 3 ? the latest release ?

---

### Post by aysiu on 2006-07-02
[QUOTE=visvak]hey this is only alpha 2 is it ? is there anyway to get alpha 3 ? the latest release ?[/QUOTE]
I don't see anything about Alpha 3:
[http://developer.mozilla.org/devnews/index.php/2006/05/12/bon-echo-alpha-2-milestone/](http://developer.mozilla.org/devnews/index.php/2006/05/12/bon-echo-alpha-2-milestone/)

---

### Post by visvak on 2006-07-02
umm i forgot from were i got it but here's a screenshot -  

[IMG]http://img75.imageshack.us/img75/2880/screenshot0lv.png[/IMG]

enlarge it and see. its 2.0 a3

also take a look at - 

[http://www.mozillazine.org/talkback.html?article=8671](http://www.mozillazine.org/talkback.html?article=8671)
[http://arstechnica.com/news.ars/post/20060531-6953.html](http://arstechnica.com/news.ars/post/20060531-6953.html)

EDIT - here's the source  - [http://developer.mozilla.org/devnews/index.php/2006/05/26/bon-echo-alpha-3-milestone-released/](http://developer.mozilla.org/devnews/index.php/2006/05/26/bon-echo-alpha-3-milestone-released/)

---

### Post by aysiu on 2006-07-02
Okay. The script won't work exactly, then, but here's Alpha 3:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha3/linux-i686/en-US/bonecho-alpha3.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha3/linux-i686/en-US/bonecho-alpha3.tar.gz)

---

### Post by visvak on 2006-07-02
[QUOTE=aysiu]Okay. The script won't work exactly, then, but here's Alpha 3:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha3/linux-i686/en-US/bonecho-alpha3.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha3/linux-i686/en-US/bonecho-alpha3.tar.gz)[/QUOTE]

ya the script dosent work anymore. any chance of an updated one ? BonEcho has an awesome "Undo CLose Tab" feature and a better downloader. and my version of nightly tester tools whichi use make old extensions work dosent work with a2.

EDIT - ok got it installed. instruction from mozilla's site - 

```
Extract the tarball and run ./firefox:

tar -xzvf bonecho-alpha3.tar.gz
cd firefox
./firefox 
```

ok now it starts when i type cd firefox and ./firefox into the terminal. so what will the link to the file be. if i wanted to creat a menu shortcut ?

---

### Post by aysiu on 2006-07-02
This is what the new script would look like: ```
#!/bin/bash
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Firefox are installed
"
sudo apt-get -y install firefox libstdc++5
echo "
Backing up old Firefox preferences
"
cp -R ~/.mozilla ~/.mozilla_backup
echo "
Changing to home directory
"
cd
echo "
Downloading Firefox from the Mozilla site
"
wget -c ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/bonecho/alpha3/linux-i686/en-US/bonecho-alpha3.tar.gz
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -x -z -v -f bonecho-alpha3.tar.gz
echo "
Removing the unzipped .tar.gz
"
rm bonecho-alpha3.tar.gz
echo "
Linking plugins
"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
echo "
Linking launcher to new Firefox
"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
echo "
The new Firefox is installed."
```

---

### Post by visvak on 2006-07-02
thanks mate works perfectly. i am now running firefox 2.0 alpha 3 without a prob. u wrote those scripts yourself ?

---

### Post by aysiu on 2006-07-02
[QUOTE=visvak]thanks mate works perfectly. i am now running firefox 2.0 alpha 3 without a prob. u wrote those scripts yourself ?[/QUOTE]
Well, yes, sort of. They're just modifications of these instructions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by visvak on 2006-07-14
hey aysiu, firefox 2.0 beta 3 is out. any chance of an updated script ?

EDIT : If i just changed the source of the download and the name of the ta.gz file, will the old script work ? i've done that but am scared to run it for fear of screwin up my current firefox install.

EDIT 2: HELP !!! I ran the script. it updated all right. but now i have some wierd language which i think is spanish. anyways, can anyone tell me how to get back english ?

---

### Post by SuperMike on 2006-07-15
Now that I'm on Swiftfox and my web browsing moves at lightning fast speed, how can I get the same speed improvements in Thunderbird?

---

