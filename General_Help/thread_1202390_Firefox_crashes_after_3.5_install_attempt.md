---
title: "Firefox crashes after 3.5 install attempt"
date: 2009-07-02
forum: General Help
---

### Post by andreselsuave on 2009-07-02
Hi there:

I tried to install firefox 3.5 final from the mozilla foundation website. I just unpacked the tar.bz2 and tried running firefox from there. It worked good, but now I wanted to do a system-wide install (which I haven't found yet) so I deleted the file. 

Now when I try to open firefox 3.0.11, it is up for 2-3 seconds then crashes with the following terminal output:

```
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success
```

Anyone can help, please?

thanks a lot

---

### Post by moster on 2009-07-02
Before you figure it out what is that error here is simple instructions how to get latest version of firefox and future updates :)
[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html")

---

### Post by andreselsuave on 2009-07-02
thanks moster, but I already tried that and it installs you the release candidate of firefox 3.5 (aka Shiretoko) not the final version.

---

### Post by moster on 2009-07-03
> **andreselsuave said:**
> thanks moster, but I already tried that and it installs you the release candidate of firefox 3.5 (aka Shiretoko) not the final version.

Maybe you are not aware what is going on. SHiretoko IS final 3.5 firefox. :) Everybody is suprised, not just you. Its something about licences for using name "firefox". It is really nonsense.

---

### Post by andreselsuave on 2009-07-04
It Is not!! 

When I install firefox-3.5 I go to Help -> About it says Firefox 3-5 RC4 Shiretoko

When I download the tar.bz2 from firefox website Help-> about says Firefox 3.5 Final

---

### Post by blueridgedog on 2009-07-04
Have you tried renaming your ~/.mozilla directory and testing with a clean profile?

---

### Post by Genius314 on 2009-07-04
Maybe there's a conflicting plugin? Try running:
```
firefox -safe-mode
```
Then you can disable all the plugins from there...
Just be warned that if you have a lot of plugins, you'll have to re-enable them one-by-one.

Hope that helps.

---

### Post by Sukotto on 2009-07-04
1. Add the following line to** /etc/apt/sources.list**
*deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main*

2. Identification key for this repository (Applications -->Accessories --> Terminal)

*sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE*

3. Refresh your system cache:

*sudo apt-get update*

4. Setup this package, latex-xft-fonts and also firefox-3.5-gnome-support

[I]sudo apt-get install firefox-3.5 firefox-3.5-gnome-support latex-xft-fonts

Should work then
[/I]

---

### Post by blueridgedog on 2009-07-05
What is the lure of 3.5?  Is there something significant that has changed?

---

### Post by scouser73 on 2009-07-05
Visit here to install Firefox 3.5 **NOT** Shiretoko

[http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")

I installed it this morning using this method.

[[IMG]http://img40.imageshack.us/img40/1978/51943437.th.png[/IMG]](http://img40.imageshack.us/i/51943437.png/)

---

