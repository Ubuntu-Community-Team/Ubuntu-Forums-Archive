---
title: "Chrome reports java plugin outdated?"
date: 2012-07-11
forum: General Help
---

### Post by screaminj3sus on 2012-07-11
I've had this problem with both openjre versions from the ubuntu repos (openjre6 and openjre7), so I assumed they must be outdated, completely removed them and installed the latest oracle java 7, same issue. chrome says the plugin is blocked because its outdated.


Everytime I try and run a java applet in chrome it says the plugin is blocked because its outdated, chrome:plugins says it needs a critical security update. As I mentioned I am already running the latest version of the official oracle java 7. Is there anyway to fix this? Its really annoying having it ask me every time if I want to run it anyway. Checking "always allow" for the plugin does nothing, it still asks me every single time.

in ubuntu java -version reports: java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)

screenshot of chrome:plugins attatched: [http://i.imgur.com/BXL6v.png](http://i.imgur.com/BXL6v.png)

---

### Post by vasa1 on 2012-07-11
Can you try with a new profile, just in case something is corrupted in the present one?
[http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059](http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059)

ps: **chrome : plugins** (no spaces) shows as **chromelugins** if you don't "disable smilies in text" while posting.

---

### Post by screaminj3sus on 2012-07-14
It was a fresh install of chrome, but I tried a new profile anyway, same issue.

---

### Post by spamless on 2012-08-18
> **screaminj3sus said:**
> It was a fresh install of chrome, but I tried a new profile anyway, same issue.

I have the same issue in Precise.  Just purged google-chrome-stable and reinstalled it.  Didn't help.

---

### Post by polki@mac.com on 2012-08-22
I have the same problem and would like to know if anyone finds a solution.

---

### Post by thegeko on 2012-09-08
same problem on Debian Squeeze, just installed latest java from oracle..seems like problem with chrome

---

### Post by GentleInferno on 2012-09-08
I had the same problem, really annoying.
Short term quick fix - 
1. click on desktop
2. open dash, type chrome, drag and drop chrome icon on to desktop.
3. right click icon on desktop to get properties
4. add --allow-outdated-plugins at the end in the command line

Use this icon to open chrome. No more annoyance!

Note: I am a complete novice at linux and this is a just a quick fix, not recommended in the long run but it seems for now, this problem is a chrome/java bug.

---

