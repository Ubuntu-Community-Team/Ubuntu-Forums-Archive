---
title: "No Cheese webcam booth"
date: 2011-09-03
forum: General Help
---

### Post by Bruv on 2011-09-03
I have tried to install Cheese through Ubuntu Software centre and from Synaptic package manager but it doesn't show under Applications/Sound & Video.
the Software centre failed twice, saying to check internet connection, although it was working.
I have Searched for Cheese and found some files in Files system.


What has happened to the program ?

---

### Post by Bruv on 2011-09-04
May help others with similar problems.

Despite 'installing' the program it wasn't 'installed' 
I think there was a problem with the Software Centre, as I uninstalled it, then re-installed it and re-installed Cheese again and it works.

---

### Post by IWantFroyo on 2011-09-04
A tip for problems like these:

First, try installing it using aptitude:
```
sudo aptitude install cheese
```You will be able to see any error messages.

Then, try running it from terminal:
```
cheese
```These should diagnose why it isn't working. Problems like these are usually caused because the correct repository isn't enabled.

Edit: Just wanted to point out that I know you fixed the error. This is just a tip in general for problems like this.

---

### Post by Bruv on 2011-09-04
Every bit of information helps, if not me someone else.
Thank you

---

