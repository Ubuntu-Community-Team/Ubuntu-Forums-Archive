---
title: "Chromium Fails to display any webpages"
date: 2009-07-16
forum: General Help
---

### Post by jarede on 2009-07-16
For some reason chromium (or Google Chrome unstable) fails to display any webpages at all, while every other browser installed on the OS works fine. I've tried uninstalling and reinstalling but nothing seems to work. Googling around has also turned up nothing, so I'm thinking its an issue with my system.

Anyone got any idea what could cause something like this to happen?

---

### Post by moster on 2009-07-16
You did not said how you install it.

Do it like rest of us and it should work if somebody did not cast spell on you ;)

Add repos
[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/~chromium-daily/+archive/ppa")

```
sudo apt-get install msttcorefonts
sudo apt-get update
sudo apt-get install chromium-browser
```

Maybe you just do not have mscore fonts? At my knowledge they are must have for chromium.

---

### Post by jarede on 2009-07-16
Unfortunately I did have msttcorefonts installed as well as the repo for chromium. :(

I haven't used the browser in a while so I don't know when it started not functioning but attached is a screencap of what happens when I try to load any webpage

---

