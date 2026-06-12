---
title: "file not found but i am looking at it"
date: 2009-12-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-12-04
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found

says that but /opt/firefox/firefox-bin is right there
how do i update the index ubuntu uses

---

### Post by cariboo on 2009-12-04
Because Firefox is not installed in your standard path, you need to use the full path to the file to start it. IF you trying to start it from the terminal and you are in the correct directory try:

```
./firefox-bin
```

---

### Post by pqwoerituytrueiwoq on 2009-12-04
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
i used that to try to get 3.5 installed and be able to  use the 64bit version of flash
i have spelled it out 
/opt/firefox/firefox
and just 
firefox



me@linux-laptop:~$ /usr/bin/firefox
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found
me@linux-laptop:~$ /opt/firefox/firefox
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found
me@linux-laptop:~$ firefox
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found

---

### Post by MaxIBoy on 2009-12-04
Capitalization issue maybe?

---

### Post by pqwoerituytrueiwoq on 2009-12-04
that is not it
i can find it with nautilus but not with the find or locate command


```
me@linux-laptop:~$ ls /opt/firefox/
application.ini             libfreebl3.so    libxul.so
blocklist.xml               libmozjs.so      modules
browserconfig.properties    libnspr4.so      mozilla-xremote-client
chrome                      libnss3.so       old-homepage-default.properties
components                  libnssckbi.so    platform.ini
crashreporter               libnssdbm3.chk   plugins
crashreporter.ini           libnssdbm3.so    plugins.backup
crashreporter-override.ini  libnssutil3.so   README.txt
defaults                    libplc4.so       removed-files
dictionaries                libplds4.so      res
extensions                  libsmime3.so     run-mozilla.sh
firefox                     libsoftokn3.chk  searchplugins
firefox-bin                 libsoftokn3.so   Throbber-small.gif
greprefs                    libsqlite3.so    update.locale
icons                       libssl3.so       updater
libfreebl3.chk              libxpcom.so      updater.ini
me@linux-laptop:~$ /opt/firefox/firefox
/opt/firefox/run-mozilla.sh: 399: /opt/firefox/firefox-bin: not found
```

---

