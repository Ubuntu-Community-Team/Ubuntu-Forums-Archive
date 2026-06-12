---
title: "Chromium"
date: 2010-05-21
forum: General Help
---

### Post by osomphane on 2010-05-21
Can anyone tell me if the Chromum package in the Ubuntu Software Center repository is safe and sable for use? Do people prefer it over Google Chrome, since it does not require Wine to run?

---

### Post by cain071546 on 2010-05-21
It is safe and fine to use but i would download the official version for Linux from Google i find it works better most of the time

---

### Post by SlidingHorn on 2010-05-21
> **osomphane said:**
> Can anyone tell me if the Chromum package in the Ubuntu Software Center repository is safe and sable for use?

I have run both Chrome and Chromium on Ubuntu, and I was much more satisfied with Chromium.  I had an issue with Chrome which didn't play any audio from flash (hulu, etc.).  Since installing Chromium, everything has run perfectly.

> Do people prefer it over Google Chrome, since it does not require Wine to run?

Actually, Chrome itself now has a Linux version which can be installed from the repos:

For Chrome:

```
sudo apt-get install google-chrome
```

For Chromium:

```
sudo apt-get install chromium-browser
```

Try both out and see which works best for you

---

### Post by cain071546 on 2010-05-21
i had issues with the older version of (Chrome) but the newest beta from Google seems to be just fine 
and have both installed i still prefer Chrome over Chromium

---

### Post by friTTe81 on 2010-05-21
Im using Chromium now, had some trounble with Chrome.
Not sure if it had to do with my Wubi install of Ubuntu or somethging else.
But after my fresh install i installed Chromium, it works with everything so far =)

---

### Post by Sef on 2010-05-21
> For Chrome:

 	Code:
 	sudo apt-get install google-chrome 
For Chromium:

 	Code:
 	sudo apt-get install chromium-browser


Applications > Ubuntu Software Center > Search: Chrome > click install on the browser(s) that you want.

---

### Post by bodhi.zazen on 2010-05-21
I have started looking at using chromium as a replacement for firefox (as I think it is more secure and has matured).

If you are running lucid it is in the repos. If you are not, use the stable ppa and not the daily build (assuming you want stability).

---

### Post by osomphane on 2010-05-22
I cannot find chrome in the repos, only a deb from google.
Apt-get google-chrome doesnt find a package.
Chromium is in the software center though.

---

### Post by uRock on 2010-05-22
I prefer Chromium, being it is in the repos you have no worries of adding an unsafe PPA.

If it weren't for my college requiring Firefox or IE to do online courses, I would've dropped Firefox already.

---

### Post by bodhi.zazen on 2010-05-22
It is in the lucid repos

[http://packages.ubuntu.com/lucid/chromium-browser](http://packages.ubuntu.com/lucid/chromium-browser)

```
sudo apt-get install chromium-browser
```

---

### Post by sixthwheel on 2010-05-22
I just switched to Iron, which is a chromium browser with no tracking data.

---

### Post by uRock on 2010-05-22
> **sixthwheel said:**
> I just switched to Iron, which is a chromium browser with no tracking data.

I never knew Chromium tracked data.

---

### Post by Aditya Bhavaraju on 2010-05-22
> **osomphane said:**
> Can anyone tell me if the Chromum package in the Ubuntu Software Center repository is safe and sable for use? Do people prefer it over Google Chrome, since it does not require Wine to run?

Chromium is safe and stable but I would suggest you download chromium directly from google at [http://www.google.com/chrome?hl=en&platform=linux&brand=CHFK](http://www.google.com/chrome?hl=en&platform=linux&brand=CHFK)
yours sincerely
Aditya

---

### Post by uRock on 2010-05-22
> **Aditya Bhavaraju said:**
> Chromium is safe and stable but I would suggest you download chromium directly from google at [http://www.google.com/chrome?hl=en&platform=linux&brand=CHFK](http://www.google.com/chrome?hl=en&platform=linux&brand=CHFK)
yours sincerely
Aditya

That takes you to Chrome, not Chromium.

---

### Post by auh2o on 2010-05-22
Why ANYone would use Chrome instead of Chromium is beyond me, unless you actually WANT to give the most evil company in the world (next to Monsanto) the ability to track you.

---

### Post by sixthwheel on 2010-05-22
> **uRock said:**
> I never knew Chromium tracked data.

That's what they claim anyways..Who knows anymore who's tracking what?

---

### Post by wilee-nilee on 2010-05-22
You might consider this.
[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)
for information this is the actual download link.
[http://www.srware.net/forum/viewtopic.php?f=18&t=1031](http://www.srware.net/forum/viewtopic.php?f=18&t=1031)

---

### Post by bodhi.zazen on 2010-05-22
Srware Iron is probably what I will switch to, last time I looked it was a bit unstable yet on Linux and the distribution of the source code / deb / rpm packages left a little to be desired.

Do they have an Ubuntu repository set up yet ? ppa ?

---

### Post by malspa on 2010-05-22
Here's someone who suggests that it's better to just use Chromium instead of Iron:

[http://thoughtyblog.wordpress.com/2009/12/16/why-no-one-should-not-use-the-iron-chromium-fork/](http://thoughtyblog.wordpress.com/2009/12/16/why-no-one-should-not-use-the-iron-chromium-fork/)

---

