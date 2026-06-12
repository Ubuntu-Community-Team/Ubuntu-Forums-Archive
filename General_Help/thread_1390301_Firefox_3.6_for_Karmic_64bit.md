---
title: "Firefox 3.6 for Karmic 64bit?"
date: 2010-01-25
forum: General Help
---

### Post by AmrH on 2010-01-25
Is there a way to install Firefox 3.6 for Ubuntu Karmic 64bit?

---

### Post by llawwehttam on 2010-01-25
Up to a point but only if you use the ppa. Otherwise I recommend ubuntuzilla. [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)

---

### Post by AmrH on 2010-01-25
I've tried Ubuntuzilla; however, it says that it's only for the 32bit version.

---

### Post by drs305 on 2010-01-25
This ppa has the 64-bit version:
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

---

### Post by AmrH on 2010-01-25
> **drs305 said:**
> This ppa has the 64-bit version:
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
Would you please tell me how to add this to the sources.list file?

---

### Post by philinux on 2010-01-25
> **AmrH said:**
> Would you please tell me how to add this to the sources.list file?

One thing to remember with that ppa is that you will get daily updates, like every day.

```
sudo add-apt-repository ppa:anyppa
```

so that would be

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily
```

---

### Post by bodhi.zazen on 2010-01-25
> **AmrH said:**
> Would you please tell me how to add this to the sources.list file?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by AmrH on 2010-01-25
Thank you!

---

### Post by philinux on 2010-01-25
> **AmrH said:**
> When I type the line below, it says that it's invalid.
```
sudo add-apt-repository http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
```

See post #6

---

### Post by Vaphell on 2010-01-25
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

you can find instructions there

---

### Post by mordecai83 on 2010-01-25
At  [webupd8]("http://www.webupd8.org/2010/01/firefox-36-stable-ubuntu-repository-ppa.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+webupd8+%28Web+Upd8+-+What%27s+New+On+The+WWW%29") i found this ppa:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

then

```
sudo apt-get update && sudo apt-get install firefox-3.6
```

---

### Post by michael37 on 2010-01-25
Yes, definitely use firefox-stable, not daily builds.

Thanks @mordecai83 and asac for maintaining firefox-stable.

---

### Post by clarkec321 on 2010-01-26
> **mordecai83 said:**
> At  [webupd8]("http://www.webupd8.org/2010/01/firefox-36-stable-ubuntu-repository-ppa.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+webupd8+%28Web+Upd8+-+What%27s+New+On+The+WWW%29") i found this ppa:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

then

```
sudo apt-get update && sudo apt-get install firefox-3.6
```

I probably shouldn't have done this as I don't really know what I'm doing, but my impatience for 3.6 just got the better of me.

Everything seemed to work fine, but when I start FF it's still 3.5.7, I presume to get 3.6 running I need to run it from the terminal, and then somehow remove 3.5.7 and make the shortcut in the applications menu manually.

Is there a way I can undo the above and just wait for 3.6 to be available in the Update Manager?

---

### Post by ElSlunko on 2010-01-26
ppa:mozillateam/firefox-stable

^^ That's what I use. Works fine

---

### Post by AmrH on 2010-01-29
> **ElSlunko said:**
> ppa:mozillateam/firefox-stable

^^ That's what I use. Works fine
And here's the tutorial ;)
[http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html)

---

### Post by carpman on 2010-02-27
Hello, ok tried the tut on link and all appears to install ok and can see both firefox and firefox-3.5 in usr/bin but no matter how i start it the about firefox menu reports 3.5.8 ?

---

### Post by ulvesang on 2010-02-27
> **carpman said:**
> Hello, ok tried the tut on link and all appears to install ok and can see both firefox and firefox-3.5 in usr/bin but no matter how i start it the about firefox menu reports 3.5.8 ?

I've been running into the same problem: I've tried fully uninstalling all packages related to (any) Firefox, removing the "http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu" repository info, then re-entering it, updating, and then re-downloading firefox3.6. However, on reinstalling, I still get the "wrong" Firefox build (Mozilla/5.0 (X11; U; Linux i686 (x86_64); de; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5).

---

### Post by michael37 on 2010-03-01
Easiest strategy: remove firefox-stable however you added it, then go to System -> Administration -> Software Sources -> Other Software.
Click on +Add and paste **ppa:mozillateam/firefox-stable**.  It will ask you reload, do that.

This should do the trick.

---

