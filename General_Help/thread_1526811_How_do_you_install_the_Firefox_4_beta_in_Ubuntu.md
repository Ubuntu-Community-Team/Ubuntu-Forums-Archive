---
title: "How do you install the Firefox 4 beta in Ubuntu?"
date: 2010-07-08
forum: General Help
---

### Post by kevin82485 on 2010-07-08
How do you install the Firefox 4 beta in Ubuntu?  I'm still trying to understand how to install files that come downloaded in a .tar.bz2 type file.  I unpacked this package, but don't understand what to do with it.

---

### Post by bodhi.zazen on 2010-07-08
It is a binary.

Extract the archive

Open nautilus, go to the extracted directory, and run firefox

---

### Post by kevin82485 on 2010-07-08
Thanks for your reply, but I'm still a little lost. Can you be more specific as to what steps I should follow?

---

### Post by speeves on 2010-07-08
I wrote up a quick how-to here:
[http://speeves.erikin.com/2010/07/firefox-4-beta-1-on-ubuntu-lucid.html](http://speeves.erikin.com/2010/07/firefox-4-beta-1-on-ubuntu-lucid.html)

speeves

---

### Post by cpmman on 2010-07-08
Try Firefoxtester by lovinglinux in Firefox - Tools - Add-ons

---

### Post by kevin82485 on 2010-07-08
> **speeves said:**
> I wrote up a quick how-to here:
[http://speeves.erikin.com/2010/07/firefox-4-beta-1-on-ubuntu-lucid.html](http://speeves.erikin.com/2010/07/firefox-4-beta-1-on-ubuntu-lucid.html)

speeves

The code is not working for me.

---

### Post by philinux on 2010-07-08
> **kevin82485 said:**
> Thanks for your reply, but I'm still a little lost. Can you be more specific as to what steps I should follow?

With nautilis right click the archive file and choose extract here. Open the new folder and look for the firefox executable and double click it.

---

### Post by kevin82485 on 2010-07-08
I give up, I don't see anything that looks like an executable. I have tried opening literally every file that is in the archive and nothing happens.

---

### Post by ajgreeny on 2010-07-08
There should be one file simply called **firefox** which is a shell script, and another called** firefox.bin** which is the binary executable.

---

### Post by bodhi.zazen on 2010-07-08
> **kevin82485 said:**
> The code is not working for me.

> 

[LIST=1]
[*] Download Firefox from [the Firefox download page]("http://www.getfirefox.com/") to your  home directory.
[*] Open a **Terminal** and go to your home directory: cd ~
[*] Extract the contents of the downloaded file:tar xjf firefox-*.tar.bz2
[*] Close Firefox if it's open.
[*] To start Firefox, run the firefox  script in the firefox folder.~/firefox/firefox
[/LIST]
  Firefox should now start. You can then create an icon on your desktop  to run this command.


[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

---

### Post by kevin82485 on 2010-07-08
So I restarted my computer and tried doing this all again, and viola it works.  I don't know what the issue was before, but whenever I tried opening the file from the archive, it would just open FF 3.6.

---

### Post by lovinglinux on 2010-07-09
> **kevin82485 said:**
> So I restarted my computer and tried doing this all again, and viola it works.  I don't know what the issue was before, but whenever I tried opening the file from the archive, it would just open FF 3.6.

If Firefox is already opened, then you can't open another version this way. You need a special command.

I would recommend my extension, [Foxtester](https://addons.mozilla.org/en-US/firefox/addon/141505/). It allows you to easily install, uninstall and launch multiple Firefox versions. 

Watch a demo [here](http://foxtester-extension.blogspot.com/2010/05/foxtester-102-released.html). It's really easy to use it.

---

### Post by webtechquery on 2010-07-12
Hi there.

To install Beta Firefox 4 in your Ubuntu, please check out the following link, which will explain you how you can easily download and install Beta Firefox 4 in your Ubuntu:

[http://www.webtechquery.com/index.php/2010/07/beta-firefox-4-ubuntu-beta-firefox-4-linux/](http://www.webtechquery.com/index.php/2010/07/beta-firefox-4-ubuntu-beta-firefox-4-linux/)

Thanks.

---

### Post by speeves on 2010-07-28
I have updated my instructions for firefox 4 beta 2:
[http://speeves.erikin.com/2010/07/firefox-4-beta-2-on-ubuntu-lucid-1004.html]("http://speeves.erikin.com/2010/07/firefox-4-beta-2-on-ubuntu-lucid-1004.html")

---

### Post by webtechquery on 2010-07-28
Firefox 4 Beta 2 could also be easily downloaded and installed for Ubuntu / Linux. For details, check out the following link:

[http://www.webtechquery.com/index.php/2010/07/firefox-4-beta-2-ubuntu-firefox-4-beta-2-linux/](http://www.webtechquery.com/index.php/2010/07/firefox-4-beta-2-ubuntu-firefox-4-beta-2-linux/)

Thanks

---

### Post by cdated on 2010-07-30
Thanks @bodhi.zazen, somehow I tend forget to close running instances.  I was starting to get annoyed with version 3.6 constantly popping up.

---

### Post by speeves on 2010-08-11
Here is an update for beta 3:
[http://speeves.erikin.com/2010/08/firefox-4-beta-3-on-ubuntu-lucid-1004.html]("http://speeves.erikin.com/2010/08/firefox-4-beta-3-on-ubuntu-lucid-1004.html")

---

### Post by TNT1 on 2010-08-11
> **cpmman said:**
> Try Firefoxtester by lovinglinux in Firefox - Tools - Add-ons

_+1
Then you too can become a lovinglinux fanboi:D

---

### Post by sephtin on 2010-09-20
meh, if you want the nightly... just do it the easy way:

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa && sudo apt-get update
sudo apt-get install firefox-4.0

```

as per:  [http://linuxhub.net/2010/07/install-firefox-4-beta-2-in-ubuntu-using-ppa/](http://linuxhub.net/2010/07/install-firefox-4-beta-2-in-ubuntu-using-ppa/)

why does everyone insist on messing up package management by downloading and installing everything by hand anymore...  sheesh.  ;)

---

### Post by speeves on 2010-09-20
Hi Sephtin,

We are offering this method, as there are times when we need our stable installation of an app, while wanting to test drive beta versions. I am actually noticing that I am starting to running more apps outside of the repo tree, as I am wanting newer versions, (ie rhythmbox or firefox), or don't want to follow the upgrade path of the distribution, (ie eclipse).

The awesome thing about GNU/Linux, is that I _can_ do this :)

Cheers,
speeves

---

### Post by bodhi.zazen on 2010-09-20
> **sephtin said:**
> meh, if you want the nightly... just do it the easy way:

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa && sudo apt-get update
sudo apt-get install firefox-4.0

```as per:  [http://linuxhub.net/2010/07/install-firefox-4-beta-2-in-ubuntu-using-ppa/](http://linuxhub.net/2010/07/install-firefox-4-beta-2-in-ubuntu-using-ppa/)

why does everyone insist on messing up package management by downloading and installing everything by hand anymore...  sheesh.  ;)

Depends on the application. Firefox is trivial, IMO, to install outside the repos / ppa and I prefer to get the code from mozilla :p

A better question, why should you care how others install firefox ? If the ppa works for you, by all means use it.

---

### Post by FahadMKS on 2010-09-20
You may also make use of the link [http://linuxhub.net/2010/07/install-firefox-4-beta-2-in-ubuntu-using-ppa/](http://linuxhub.net/2010/07/install-firefox-4-beta-2-in-ubuntu-using-ppa/) so as to install the Firefox 4.

Try it and let me know if it works.

---

