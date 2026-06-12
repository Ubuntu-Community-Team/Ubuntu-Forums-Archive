---
title: "Touchpad not working in Ubuntu 11.10 despite Synaptik touchpad manager"
date: 2011-10-15
forum: General Help
---

### Post by Happy Prancer on 2011-10-15
My touchpad has not been working at all since I upgraded to 11.10 today.  My touchpad is my main pointing device, so not having it is quite debilitating.

I know there are already forum posts discussing this issue, and most people seem to have found a resolution by installing Synaptik Touchpad Manager from the Software center.  I have done this and have run Synaptik to make sure all of the settings are reasonable.  However, I still get no response from my touchpad at all.  Neither the pad nor the buttons are responsive.

Any tips on diagnosing the problem, or solutions to try are greatly appreciated.

Thanks,

Dan

---

### Post by mclode on 2011-10-15
I had the same thing on my Acer netbook, where the touchpad is the only mouse. Pressing Fn-F7 (the touchpad button) re-enabled it and it has carried on working after a couple of reboots. Strangely the touchpad did work immediately after the upgrade but then stopped. Could it be related to the "disable touchpad when typing" option from System Settings > Mouse and Touchpad?

---

### Post by Happy Prancer on 2011-10-15
Wonderful!  Fn-F7 did the trick.  I swear I had already tried it, but maybe that was before installing Synaptik.

Thanks for your help.

---

### Post by K-Jtan on 2011-10-16
I got the same problem with my Dell XPS (M1730), FNn + F7 didn't do anything

---

### Post by Kapflight on 2011-10-16
What worked for me was:
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator

On an asus eee pc 1005HAB

---

### Post by tilder on 2011-11-09
Thanks!

I use a Lenovo Thinkpad R61i.
Fn + F8 did the trick for me.
Didn't expect it ti be such a simple thing.

---

### Post by dharmendra verma on 2011-11-11
Complete Troubleshoot Guide you can find here, i had tried at my level to solve this issue. visit- 
[http://dharmendralinuxdiary.blogspot.com/2011/11/ubuntu-1110-touchpad-problem.html](http://dharmendralinuxdiary.blogspot.com/2011/11/ubuntu-1110-touchpad-problem.html)

Thanks..:popcorn:

---

### Post by stumpf on 2011-11-13
Thank you! My touchpad is working really well now after configuring synaptik.

---

### Post by stumpf on 2011-11-26
Unfortunately, my Lenovo ThinkPad sometimes bugs and the touchpad is no longer functional until I open up Synaptik. Synaptik starts up with my computer, so I can't figure out why this become a problem. I do not know what sets it off, but the touchpad and the buttons won't work until I have Synaptik open. I have tried Fn + F8, but my computer doesn't realize in the first place that the touchpad isn't working - so this makes no difference. Does anyone else have this issue?

---

### Post by TedinOz on 2011-12-16
> **dharmendra verma said:**
> Complete Troubleshoot Guide you can find here, i had tried at my level to solve this issue. visit- 
[http://dharmendralinuxdiary.blogspot.com/2011/11/ubuntu-1110-touchpad-problem.html](http://dharmendralinuxdiary.blogspot.com/2011/11/ubuntu-1110-touchpad-problem.html)

Thanks..:popcorn:

Thanks for the link. This worked for me and I didn't need Synaptiks.

---

