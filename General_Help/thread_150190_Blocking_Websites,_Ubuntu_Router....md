---
title: "Blocking Websites, Ubuntu Router..."
date: 2006-03-25
forum: General Help
---

### Post by benofsky on 2006-03-25
I have setup an old ubuntu machine, which I use as a router it has two NICS it also is a web/mail/ftp server. 3 other computers connect to the internet through it, I would like to be able to block websites from the family computer going through the router how would I achieve this?
Ben

---

### Post by John.Michael.Kane on 2006-03-25
[http://ubuntuforums.org/showthread.php?t=50014&highlight=firewall+script](http://ubuntuforums.org/showthread.php?t=50014&highlight=firewall+script)
you can also try this way [http://hostsfile.mine.nu/](http://hostsfile.mine.nu/)

---

### Post by jakemikey on 2006-03-25
You want Dansguardian.  I set up a small, dedicated Ubuntu box to do just what you're trying to do.  I used Dansguardian and it works flawlessly.  By far the "smartest" (least false positives) and most configurable filtering software out there.  I installed Squid from the repos and built the latest version of DG from source.  You'll also need to learn about (if you don't already know) the basics of iptables rules.

I learned a lot by setting it up and I'm glad I've got it.

---

