---
title: "How to revert to firefox 3.1 in Ubuntu 9.10 karmic koala"
date: 2009-10-29
forum: General Help
---

### Post by chuckh1958 on 2009-10-29
I just updated to 9.10 and have hit a show stopper. My organization uses a web based ticketing system with is not compatible with Firefox 3.5. I use it extensively as part of my job. Apparently there is a java permissions bug with FF 3.5 and the tool will not work with it. How can I get FF 3.0 or 3.1 installed in Ubuntu 9.10?

FF 3.1 and IE8 both work find with the tool but not FF 3.5. Galeon and Epiphany seem to have the same problem as FF 3.5.

---

### Post by Redundant Username on 2009-10-29
I'm not sure how to downgrade, but as a temporary fix you could download an older version of firefox from the Mozilla website. Make sure it's the tar.gz so you can just uncompress and firefox.bin.

---

### Post by buchan on 2009-10-29
Same issue here with an older incompatible plugin...

Go here:
[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)
Download the proper version.
I extracted the folder to the users directory and changed the shortcuts to point the the older version.

---

### Post by chuckh1958 on 2009-10-29
Do I need to change the LD_LIBRARY_PATH to pick up the uncompressed lib versions? Or will the newer one's alread in the path work?

---

### Post by sports fan Matt on 2009-10-29
If the only issue is an unproper addon, wouldn't this be easier?

Nightly Tester Tools 2.0.2: 

his extension adds a few extras useful to those that regularly test nightly builds of Firefox, Thunderbird, Sunbird and Toolkit Seamonkey (Suiterunner).

The following is a brief list of the extension's features, for the full set of features please visit the extension home page.

* Extension compatibility fixing
* Titlebar customisation
* Build ID retrieval
* Screenshots
* Breakpad information
* Restoring tabs from previous session
* Leak log analysis 

[https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

---

### Post by buchan on 2009-10-29
I didn't make any other changes and everything worked so it "should" be the same for you.

---

### Post by Merk42 on 2009-10-29
FYI there is no such thing as Firefox 3.1
it was 3.1 in the early alphas, but changed to 3.5 since it was so different.

Do browsers like Opera or Chrome/Chromium work?

---

### Post by chuckh1958 on 2009-10-29
> **Merk42 said:**
> 

Do browsers like Opera or Chrome/Chromium work?

Don't know. Neither is in the karmic repo. I've tried every browser in the karmic repo - ephiphany, galeon (which I rather like), SeaMonkey, and FireFox (3.5). Only SeaMonkey works but I don't care for the that browser. I much prefer FF.

Gonna try removing FF 3.5 and manually installing 3.0.15. 

Given that there are still problems with 3.5, I wish the packagers would offer 3.0 as an alternative in karmic. This java permissions bug is not the only problem with FF 3.5. I've been to other pages on the web that don't render correctly in 3.5 but are fine in 3.0.

---

### Post by Merk42 on 2009-10-29
> **chuckh1958 said:**
> Don't know. Neither is in the karmic repo. I've tried every browser in the karmic repo - ephiphany, galeon (which I rather like), SeaMonkey, and FireFox (3.5). Only SeaMonkey works but I don't care for the that browser. I much prefer FF.

Gonna try removing FF 3.5 and manually installing 3.0.15. 

Given that there are still problems with 3.5, I wish the packagers would offer 3.0 as an alternative in karmic. This java permissions bug is not the only problem with FF 3.5. I've been to other pages on the web that don't render correctly in 3.5 but are fine in 3.0.

[Opera](http://www.opera.com) is closes source, so that's why it's not in the repos, the .deb works to install.

I forget where to get the installation for Chrome/Chromium is

What other pages don't work? have you submitted bugs?

---

### Post by ikisham on 2009-10-29
Just saying (you may know better than me), but since you upgraded and not done a clean install maybe removing java (and configs) and reinstalling could help?

---

### Post by chuckh1958 on 2009-10-29
It's not a problem with the jre, it's a problem with Firefox. Same thing happens in Win XP with FF 3.5. I can run FF 3.0 using the same jre and everything works fine. 

I just downloaded 3.0.15 from a link posted earlier in this thread, and that fixed it. Here's what I did after downloading.

bunzip2 < firefox-3.0.15.tar.bz2 | tar xvf -
sudo ln -s firefox/firefox /usr/bin/firefox-3.0
sudo rm /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.0 /usr/bin/firefox

---

