---
title: "Very slow web browsing"
date: 2010-05-04
forum: General Help
---

### Post by x-shaney-x on 2010-05-04
This something I have only experienced since the final install.
I'm using a fresh firefox profile with NO extensions currently.  The only change I have made is to disable ipv6 to see if it helped with the following problem. 

Browsing web pages is stupidly slow and much slower than I am used to.
Downloading in firefox is normal and running at speeds I would expect.
For example, I have downloaded several distro .iso's over the past two days and they have been consistently downloading at 1MB/s +

This is only affecting browsing web pages and it's affecting all of them, even the basic google search page takes at least twice as long as normal.

---

### Post by Simfan147 on 2010-05-04
Have you tried a different browser?

---

### Post by TheNerdAL on 2010-05-04
> **Simfan147 said:**
> Have you tried a different browser?


Yeah, try Google Chrome, it works on Linux. 

[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by valhemmer on 2010-05-04
are you using a wireless card?

---

### Post by x-shaney-x on 2010-05-04
Not using wireless, ethernet cable and pretty fast fibre optic connection.
I have tried chrome/chromium and also empathy and they are both loading pages like lightning as normal.

I should stress this isn't an internet problem in general, it is ONLY affecting firefox and ONLY when browsing web pages and ONLY on this lucid install.  It was acting normally through the betas.

The only other distro I have used regularly in recent days is PCLinuxOS (gnome) and firefox is behaving exactly the same on there.

Strange.

---

### Post by NearlyALaugh on 2010-05-04
Try disabling IPv6 (a newer Internet protocol) in Firefox:

Type "about:config" in the location bar, use the filter to find "network.dns.disableIPv6", and double click on it to set it to "true". Try browsing and perhaps restart Firefox.

If that doesn't work, set the value back to "false" and try something else.


**Edit:** Shows how well I read your initial post—you already tried this. Sorry!

---

### Post by john newbuntu on 2010-05-05
If you do not have too many things to backup, try closing firefox and renaming the .mozilla/firefox in your home directory to something else.  Then restart firefox and see if it is any faster.
If that does not work, here is an article by lovinglinux on optimizing firefox:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

