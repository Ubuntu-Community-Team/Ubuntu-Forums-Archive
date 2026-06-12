---
title: "Firefox Java Plugin Alternative"
date: 2010-10-10
forum: General Help
---

### Post by melikamp on 2010-10-10
Hi! I am using the latest Lucid Lynx 10.04 on Intel x32, icedtea6-plugin, and the Mozilla's binary of Firefox 3.6.10. The java plugin appears to work, mostly, but craps out on this page:

[http://www.ghcc.msfc.nasa.gov/GOES/goeseastconus.html](http://www.ghcc.msfc.nasa.gov/GOES/goeseastconus.html)

To test, run the animation. What I see is just a corner of the applet, and buttons don't seem to work. This page works fine for me with the official x64 plugin in Slackware, but I just cannot make it work in Ubuntu. Any ideas? Are there any other FLOSS plugins I can try? A different browser, may be?

---

### Post by JackNocturne on 2010-10-10
hello,

I tried the page you linked and it worked for me.

I use firefox **3.6.x** and the plugin i use is I**ced Tea NPR Web Browser Plugin** (using IcedTea6 1.9)

---

### Post by gandaran on 2010-10-10
> **melikamp said:**
> Hi! I am using the latest Lucid Lynx 10.04 on Intel x32, icedtea6-plugin, and the Mozilla's binary of Firefox 3.6.10. The java plugin appears to work, mostly, but craps out on this page:

[http://www.ghcc.msfc.nasa.gov/GOES/goeseastconus.html](http://www.ghcc.msfc.nasa.gov/GOES/goeseastconus.html)

To test, run the animation. What I see is just a corner of the applet, and buttons don't seem to work. This page works fine for me with the official x64 plugin in Slackware, but I just cannot make it work in Ubuntu. Any ideas? Are there any other FLOSS plugins I can try? A different browser, may be?
you can install sun-java by enabling the archive.canonical partner repository in software sources and updating the package list next.
install command 
```
sudo apt-get install sun-java6-plugin
```
remove the all the openjdk java or just the icedtea plugin if you have any application that depends on openjdk.

---

### Post by melikamp on 2010-10-10
> **gandaran said:**
> you can install sun-java by enabling the archive.canonical partner repository in software sources and updating the package list next.
install command 
```
sudo apt-get install sun-java6-plugin
```
remove the all the openjdk java or just the icedtea plugin if you have any application that depends on openjdk.

Thanks! I purged icedtea and installed sun-java as you suggested, and it works now.

---

### Post by soldier1st on 2010-10-15
that page works fine and i am using Openjdk, would it be a good idea to install sun java instead of using openjdk?i have a few java apps and they seem to work fine with openjdk but would installing sun java and removing openjdk make things better or worse?

---

