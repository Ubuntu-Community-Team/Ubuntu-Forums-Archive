---
title: "Firefox download error -228"
date: 2009-09-23
forum: General Help
---

### Post by mac9416 on 2009-09-23
Hello

I am trying to install Adblock Plus in Firefox 3.7 (or 3.0 or 3.5 for that matter). When I confirm I want to install Adblock Plus, it returns...

> Minefield could not install the file at 

[https://addons.mozilla.org/downloads/file/61695/adblock_plus-1.1.1-fx+sm+tb.xpi](https://addons.mozilla.org/downloads/file/61695/adblock_plus-1.1.1-fx+sm+tb.xpi)

because: Download error
-228

My cache is enabled and I have disabled IPv6 in Firefox. I have also tried downloading the file from Mozilla's FTP site and installing it locally. The installation either hangs or returns the same error- 228.

I have managed to get it to install by running
```
sudo firefox-3.7 <filename>.xpi
```
I know that running FF as root is a bad idea, but it actually worked. Until I restarted. It then requested that I restart to apply changes. Then it requested that I restart to... Yes, it went into a never-ending loop. So I reinstalled FF and am back where I started.

Thanks in advance
-mac

---

### Post by mike555 on 2009-09-23
try here .....   [https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

---

### Post by mac9416 on 2009-09-23
Hey, mike555, thanks for the response. 

I went there and clicked Add to Firefox > Install Now. I then got the same error.

---

### Post by rashamra on 2009-11-13
I'm having the same problems as well. Been scouring the web for solutions but to no avail.

---

### Post by mac9416 on 2009-11-13
Hey, rashamra,

I should have replied sooner, but after tinkering around for an hour with no results, I simply rebooted and things have worked fine since. Very strange.

Good luck to you!

---

### Post by rashamra on 2009-11-15
Still no luck :(

For those of you with the same problem you might wanna try this out:
[http://ubuntuforums.org/showthread.php?t=1311774](http://ubuntuforums.org/showthread.php?t=1311774)

Good luck

---

