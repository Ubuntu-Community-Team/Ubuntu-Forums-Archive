---
title: "firefox dosent load images properly"
date: 2012-01-17
forum: General Help
---

### Post by KRISHNASHK on 2012-01-17
i am using ubuntu 10.10 the firefox experience is way different from windows. 
Images dosent load properly even after i refresh many times.
if there is a download popup , firefox says connection reset or page not found.
and my internet connection is pretty decent.

---

### Post by BC59 on 2012-01-17
Try using the Chromium. If it's working correctly, it's a Firefox problem. If not, we have to search for a system problem.
You can install Chromium from the Ubuntu Software Center.

---

### Post by kc1di on 2012-01-17
Which version of FireFox are you using?  I have no problems like that here with FireFox , But I most often am using Chromium you may want to try another browser to see it the problem persists across different browsers or is FireFox centric.
Just a thought.

---

### Post by Jake Sweeney on 2012-01-17
My Firefox used to do the same thing on Ubuntu 10.10. After  I installed Chromium it seemed to work fine

---

### Post by KRISHNASHK on 2012-01-18
thanks for the suggestion guys i will try it

---

### Post by raja.genupula on 2012-01-18
Hi if problem wont solved , then reinstall your Firefox once .Because sometimes even small thing missed we cant figure out it . so if problem not solved then try again by reinstalling it .

all the best.

---

### Post by KRISHNASHK on 2012-01-18
> **raja.genupula said:**
> Hi if problem wont solved , then reinstall your Firefox once .Because sometimes even small thing missed we cant figure out it . so if problem not solved then try again by reinstalling it .

all the best.
i downloaded the latest version of ubuntu but how to i add to the bar on the top of the window and how to do i uninstall the existing firefox..

---

### Post by syerges on 2012-01-18
I had the same problem when I started with Ubuntu and Firefox. You need to click on edit - preferences and make some changes in there I believe. Mine works fine now, and I don't recall doing anything drastic.

---

### Post by BC59 on 2012-01-18
> **KRISHNASHK said:**
> i downloaded the latest version of ubuntu but how to i add to the bar on the top of the window and how to do i uninstall the existing firefox..

If you like to have the latest Firefox (beta) version do this. Open a terminal CTRL+ALT+T and paste these commands:

```
sudo add-apt-repository ppa:mozillateam/firefox-next
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by raja.genupula on 2012-01-18
Hi go with this for firefox 9 and stable

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update 
sudo apt-get install firefox
```

All the best.

---

