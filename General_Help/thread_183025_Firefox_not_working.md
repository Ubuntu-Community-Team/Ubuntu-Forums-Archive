---
title: "Firefox not working"
date: 2006-05-27
forum: General Help
---

### Post by kokas on 2006-05-27
Hi there

1- I'm new to Ubuntu and to Linux...just started 5 days ago :) I'm loving it

2- I installed Ubuntu 5.10 and wanted to Upgrade Firefox to 1.5

3- I used the guide at [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28new%29%7C%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28new%29%7C%28firefox%29) after doing a search here in the forum

4- I didn't understand nothing off what I was doing...it was simple copy and paste do the command line :](*,)  and when I tried to start Firefox nothing happens...the cursor shows the thinking symbol for a few seconds but then nothing happens

So I have no browser and I'm typing this from XP :-k 

Any help is good.....

---

### Post by sYs^ on 2006-05-27
I think you should install Dapper Drake instead of Breezy Badger because that comes with FireFox 1.5 by default and that will be the latest stable release in a  ~ week.

---

### Post by kokas on 2006-05-27
If I install the Beta version will it be possible to update when the final version comes out or do I have to reinstall it again ?

Tks

---

### Post by sYs^ on 2006-05-27
You wont have to reinstall it, upgrading will just do the trick, btw the current release(RC1) is almost stable and it has a graphical installer and stuffs like that, so it's really easy to set it up.

---

### Post by kokas on 2006-05-27
Ok I'm downloading it.... :)

---

### Post by sYs^ on 2006-05-27
Good luck and have fun :p

---

### Post by [S|G] on 2006-05-27
I installed the latest firefox on my system using the following method (please note that Dapper repos already have firefox 1.5.0.3 and therefore manually installing might not be the best option; however when they update firefox again this method will probably still work):

1 - Download the latest firefox release from [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)
2 - Do the following (from the directory you downloaded firefox):
```

sudo mv firefox-version.tar.gz /opt
sudo tar -xvf /opt/firefox-version.tar.gz
sudo rm -Rf /opt/firefox/plugins
sudo ln -s /usr/lib/mozilla-firefox/plugins /opt/firefox/plugins
sudo mv /usr/bin/firefox /usr/bin/firefox_backup
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

There is no need to uninstall your current firefox; I didn't. Also, it will use all your currently installed plugins. If you ever want to revert to ubuntu's firefox (in case it updates to a newer version, for example) just remove /usr/bin/firefox and restore the backup (/usr/bin/firefox_backup)

---

