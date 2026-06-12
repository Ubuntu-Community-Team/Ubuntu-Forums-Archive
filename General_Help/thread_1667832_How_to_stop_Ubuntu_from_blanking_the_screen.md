---
title: "How to stop Ubuntu from blanking the screen"
date: 2011-01-15
forum: General Help
---

### Post by nrundy on 2011-01-15
I have both Computer and Display set to NEVER SLEEP in power management. yet after about five minutes of inactivity, Ubuntu always blanks out the screen (i.e., just a black monitor screen but the monitor power light is still on).

How do I stop this? I want to continue to see what is on my desktop--I do not want the screen to blank out ever.

---

### Post by SoFl W on 2011-01-15
What is System-> Preferences-> Screen Saver set to?

---

### Post by stinkeye on 2011-01-15
Besides turning the screensaver off you need to add
```
xset -dpms
```
to startup applications to stop the monitor blanking after about 10 mins of inactivity.

---

### Post by nrundy on 2011-01-25
It was the screensaver. thanks guys.

Sorry for the multiple posts!  My internet connection was on the fritz and my posts never appeared after I made them. So I thought they never posted. The multiples were not intentional.

---

