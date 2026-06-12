---
title: "No Java in Google Chrome"
date: 2009-12-08
forum: General Help
---

### Post by DedMoroz on 2009-12-08
I cant seem to get any java apps working in Google Chrome. Does Java even work in Chrome?

---

### Post by Zorael on 2009-12-08
Well, it works for me - or at least [http://javatester.org](http://javatester.org) does.
```
$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 4.0.267.0~svn20091208r34029-0ubuntu1~ucd1~karmic
  Candidate: 4.0.267.0~svn20091208r34029-0ubuntu1~ucd1~karmic
  Version table:
 *** 4.0.267.0~svn20091208r34029-0ubuntu1~ucd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by Rebootkid on 2009-12-08
Not working for me at all with the Google download.

ii  google-chrome- 4.0.249.30-r33 The web browser from Google

A search for chromium-browser doesn't return anything

---

### Post by Rebootkid on 2009-12-09
sudo apt-get install sun-java6-plugin

got me working

---

### Post by DedMoroz on 2009-12-09
I went the long route of uninstalling adobe flash, uninstalling java and uninstalling google chrome, then rebooting and did the process in reverse basically. I installed google chrome, then installed flash and java.

I still get no sound in youtube or other flash content...which I noticed is using "flash 9" which I find strange since the only flash I have is flash 10 something or other. The newest version. Is Chrome somehow over riding what I have installed with their own version?

Java now appears to work according to Zoreals link here: [http://javatester.org](http://javatester.org)

But, on more intricate java apps like Pogo.com games... nothing happens.

---

### Post by timandjulz on 2009-12-19
Thanks Rebootkid.  Installing the plugin support worked for me.

Tim

---

### Post by abhiroopb on 2009-12-29
> **DedMoroz said:**
> I went the long route of uninstalling adobe flash, uninstalling java and uninstalling google chrome, then rebooting and did the process in reverse basically. I installed google chrome, then installed flash and java.

I still get no sound in youtube or other flash content...which I noticed is using "flash 9" which I find strange since the only flash I have is flash 10 something or other. The newest version. Is Chrome somehow over riding what I have installed with their own version?

Java now appears to work according to Zoreals link here: [http://javatester.org](http://javatester.org)

But, on more intricate java apps like Pogo.com games... nothing happens.

Absolutely the same situation.

Youtube works fine and most other websites work fine. However, none of the games on pogo.com work at all. I have to load up firefox just to play these games.

Another strange thing is that content on EW.com is not displayed in Google Chrome. You can see everything except the text of the article (example: [http://news-briefs.ew.com/2009/12/29/jersey-shore-town-distances-self-from-show/](http://news-briefs.ew.com/2009/12/29/jersey-shore-town-distances-self-from-show/)). Open the same article in Chrome and then open it in Firefox and you will see the difference.

---

