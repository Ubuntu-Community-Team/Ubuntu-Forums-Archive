---
title: "Nautilus crashes and subsequent idiotic un/reinstall help"
date: 2010-01-26
forum: General Help
---

### Post by not1 on 2010-01-26
Hey guys I have ruined my ubuntu laptop a little bit from the result of me doing things that are way beyond any computer "savvy-ness" I have.

You may be cringing to help someone like me but - yeah - help would really be appreciated.

So Nautilus wouldn't run once upon a time for no particular reason. I hadn't installed anything since this issue came around (besides a Chrome plugin), nor had I changed any settings or messed about. Running Nautilus from the terminal resulted in an error message I cannot remember, however it said something about a segmentation fault.

This problem would not stop - I couldn't open any folders - and so I thought uninstalling and reinstalling Nautilus would result in an easy fix.

[SOLVED] So yeah I restarted after deleting and reinstalling through the terminal, but when I logged in it went to a terminal screen with no other functions (a mode you might be aware of) [/SOLVED]

Can anyone set me on the road to fix my idiocy? Nautilus still wont run.

---

### Post by J V on 2010-01-26
reinstall, you lied so we can't help you...

> I hadn't installed anything since this issue came around (besides a Chrome plugin)And, with that, chrome, and all the libraries needed for it... in fact, thats a lot of stuff installed with "Nothing except a chrome plugin"

We don't know what you installed, how you did it, or how you f*ckd up your system, you will have to reinstall... but if you didnt have anything installed that shoulden't be a problem should it?

---

### Post by not1 on 2010-01-26
> **J V said:**
> reinstall, you lied so we can't help you...

And, with that, chrome, and all the libraries needed for it... in fact, thats a lot of stuff installed with "Nothing except a chrome plugin"

We don't know what you installed, how you did it, or how you f*ckd up your system, you will have to reinstall... but if you didnt have anything installed that shoulden't be a problem should it?

No I installed Chrome as soon as Google released it (last year?) for the linux platform, and Nautilus worked just fine. I got a plugin a couple of days ago.

The problem at hand here is that I CANT START Ubuntu. It goes to a white screen with a terminal on it. My previous problem with Nautilus is not the problem at hand here. It is what I did to try and fix that problem that needs fixing.

I **did not** install anything or any libraries or packages. Do you honestly think I'd lie? There is nothing malicious or risque that I wouldn't share over the anonymity of the net. In addition I all ready look like an *** and if I did anything else id tell you kind sir.

Are you sure that there is NO OTHER WAY i could get problems on a computer that did not originate with installing something?

---

### Post by not1 on 2010-01-26
Is it possible that when i uninstalled Nautilus it deleted further vital system files that were needed and that these did not reappear when i reinstalled?

again i am not computer savvy

---

### Post by nothingspecial on 2010-01-26
Nautilus is one of those apps that remove other stuff you need when you remove it.

Get a wired internet connection.

```
sudo ifconfig eth0 up
sudo dhclient
sudo apt-get install ubuntu-desktop
exit
```

---

### Post by not1 on 2010-01-26
Thanks buddy, that worked a treat.

However - the original problem is still around. Nautilus isn't running and wont run.

Error when launching from terminal:

(nautilus:2192): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault

---

