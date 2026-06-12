---
title: "Firefox Update?"
date: 2010-09-24
forum: General Help
---

### Post by iSithis on 2010-09-24
Hello, I was wondering, how do I update my firefox to the latest Beta 7 Release?

I have downloaded the file, but I am pretty new to Ubuntu, therefore do not know which file I need to run in order to update.

---

### Post by andymorton on 2010-09-24
You should be able to update the beta from within the browser. Help>Check for updates. 

andy

---

### Post by iSithis on 2010-09-24
There doesn't appear to be a Check For Updates button within the help menu on Firefox.

---

### Post by WorMzy on 2010-09-24
A quick google search gives me this: [http://twitteling.com/2010/07/how-to-install-the-firefox-browser-beta-4-on-ubuntu/](http://twitteling.com/2010/07/how-to-install-the-firefox-browser-beta-4-on-ubuntu/)

> To install Firefox 4 on Ubuntu Linux, please open Terminal and do the following:
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-4.0
```

Any use to you?

You can also download the beta from the [firefox nightly pages]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/"), just extract the tar and double click the firefox file.

---

### Post by iSithis on 2010-09-24
Worked like a charm, thanks mate :)

---

### Post by lovinglinux on 2010-09-25
Keep in mind that ppa will also update your default Firefox version with unstable versions, along with other Mozilla applications. Also keep in mind that the ppa will make Firefox 4 clone your user profile, so any changes like saving a bookmark in FF 4 won't show in FF 3.6.

See other methods of installation at [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

Firefox 4 discussions:

[http://ubuntuforums.org/showthread.php?t=1544124](http://ubuntuforums.org/showthread.php?t=1544124)
[http://ubuntuforums.org/showthread.php?t=1574094](http://ubuntuforums.org/showthread.php?t=1574094)

---

