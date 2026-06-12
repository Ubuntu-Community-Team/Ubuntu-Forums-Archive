---
title: "amazon checkout problem"
date: 2011-02-24
forum: General Help
---

### Post by virtdave@mcn.org on 2011-02-24
ubuntu 10.10
firefox 3.6.13

When I try to buy stuff in my shopping cart in amazon, I get into a loop of successive screens, always taking me back to the 'shipping address' screen.  This does not happen when I use Windows XP.  I've tried deleting my recent history, deleting amazon's cookies , using different shipping addresses, restarting computer, logging out of amazon then logging back in.  I've chatted on the phone with amazon, they seem baffled and think that since I can buy stuff using windows xp, the problem's not at their end (probably right). Of course I could just use windows when I want to shop there, but I prefer ubuntu.....

---

### Post by seawolf167 on 2011-02-24
I used Firefox with no problems to checkout from Amazon.

The first thing I'd try would be to install and use a different browser to checkout (see below for google chrome via the command line, or just use the software center and search for google chrome). Then if you are able to, at least we know the problem is probably with your Firefox browser (which we can simply delete and reinstall)

```
sudo apt-get install chromium-browser
```

---

### Post by gmargo on 2011-02-24
Have you cleared firefox's cache?  Are you using any Add-ons? Add-ons like AdBlock or NoScript could potentially interfere.

---

### Post by Spyderkid on 2011-02-24
google chrome?

[HERE!!!!!!!]("http://www.google.com/chrome/eula.html?hl=en-GB&platform=linux_ubuntu_i386")

---

### Post by virtdave@mcn.org on 2011-02-24
The clear-the-cache and NoScript ideas were good, but they didn't resolve the problem.  So I installed Chromium (Chrome) and it works fine.  Also, Chromium seems a heck of a lot faster than Firefox, which has become annoyingly slow on my computer.  I'm going to try Chromium for a while, tho I have an emotional attachment to Firefox.  Thanks for tips.

More info:  Chromium is indeed a whole lot faster than Firefox, and I have no further problems with Amazon using Chromium.  Alas, adieu Firefox, unless Mozilla fixes it.

update, March 23, 2011: Just installed Firefox 4, and now am back to using it.  The sluggishness and hassles I was having with previous version now seem fixed

---

