---
title: "Chrome - Crashes On Opening"
date: 2012-07-06
forum: General Help
---

### Post by libspero on 2012-07-06
I'm not sure if this is strictly a Chrome issue or a Ubuntu issue so I apologise if I'm asking in the wrong place.

I'm running 12.04  [and loving it!]
Just did a routine update yesterday and shortly afterwards I noticed that Chrome no longer works.  This could be entirely circumstantial.

Basically,  when I click on the chrome icon on the side bar it loads up,  but instantly gives the message "Aw Snap,  something went wrong with your page"  (a flash issue?!?).

I tried to go into options etc but nothing works, no pages load and new tabs just present the same message.

I thought I'd uninstall it and re install it again,  but I couldn't see an option for doing that in the software centre.

What would you guys do next?

---

### Post by codingman on 2012-07-06
To uninstall chrome:

```
sudo apt-get remove google-chrome
```

To install it again go to: [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

And press the download button and take it from there.

---

### Post by libspero on 2012-07-06
Thanks codingman..   but I got the following message:

> libspero@Libspero:~$ sudo apt-get remove google-chrome
[sudo] password for libspero: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'google-chrome' can't be removed
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 prboom libcroco3:i386 libgettextpo0:i386
  libsdl-net1.2 timidity-daemon timidity
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by vierklee on 2012-07-06
I have the same problem

---

### Post by idoitprone on 2012-07-06
sudo dpkg -r google-chrome

---

### Post by haresear on 2012-07-06
This is probably caused by PepperFlash bundled with the latest version of Chrome. Check out:

[http://ubuntuforums.org/showthread.php?t=2011882]("http://ubuntuforums.org/showthread.php?t=2011882")
[http://ubuntuforums.org/showthread.php?t=2013858]("http://ubuntuforums.org/showthread.php?t=2013858")
[http://ubuntuforums.org/showthread.php?t=2018460]("http://ubuntuforums.org/showthread.php?t=2018460")

---

### Post by libspero on 2012-07-06
Thanks for the replies and links.

Looks like it might need rolling back to a previous version of Chrome some how then.   Glad it's not just me seeing this.

I don't have time to try it right now so I'll set this thread to resolved for now and hope that's the answer.

Cheers all   :)

---

