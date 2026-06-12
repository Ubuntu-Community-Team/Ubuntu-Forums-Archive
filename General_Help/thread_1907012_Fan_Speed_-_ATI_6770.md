---
title: "Fan Speed - ATI 6770"
date: 2012-01-10
forum: General Help
---

### Post by Carpentr on 2012-01-10
Hey all,

I've been running this script everytime I startup to set my computer's GPU to run at 30% fan speed.

```

DISPLAY=:0.0; aticonfig --pplib-cmd "set fanspeed 0 30"
```

I've tried doing this as well, as it should set the fanspeed to 30% the next boot as well, but it doesn't:
```
aticonfig --odcc

```

Is there some ATI Catalyst command that I don't know of, or is there a way to automatically make the first script work upon start-up? I'm trying to avoid having to manually run the script every time I boot up.

---

### Post by QIII on 2012-01-10
Setting it that way will lock it at 30%.  Is there a particular reason you don't want the speed to increase as the card gets hot?

---

### Post by Carpentr on 2012-01-10
> **QIII said:**
> Setting it that way will lock it at 30%.  Is there a particular reason you don't want the speed to increase as the card gets hot?

My card automatically defaults to a very high fan speed, even when the temperatures are low. All I really do is surf the web and play non demanding games. The fan is so loud that it's annoying.

If there was a way to set it at 30% and let it increase as needed then I wouldn't mind, but as it stands it always runs loudly, whether it needs it or not.

---

### Post by BC59 on 2012-01-10
Usually the problem with fan speed is fixed installing the ATI proprietary drivers.
Why don't you try installing Jupiter? You could tweak the performance and see if there is a difference in the fan use.

---

### Post by Carpentr on 2012-01-10
> **BC59 said:**
> Usually the problem with fan speed is fixed installing the ATI proprietary drivers.
Why don't you try installing Jupiter? You could tweak the performance and see if there is a difference in the fan use.

I have the proprietary drivers installed at the moment. It even did it on Windows so I'm a little stumped. What's Jupiter?

Thanks to everyone for the help so far.

---

### Post by QIII on 2012-01-10
I can't, in good conscience, tell you how to do something that has a very high potential to ruin a costly component -- even given XFX's warrantee.

You can find just about anything you care to in a help file here

```
aticonfig --help
```

I really don't recommend thwarting something meant to protect your investment.

Have you checked the temp when the fan is running high?

I'll look around a bit and see if this is a common complaint.  If not, it may be a reason for an RMA.  If, as you say, this is occuring in Windows then it is not a Linux issue.

---

### Post by QIII on 2012-01-10
Hmmm.  Strange.  Never mind.  Must've hit send twice.

---

### Post by Carpentr on 2012-01-10
I just checked my GPU's temperature and at 30% it's idling at 45 C and when playing Family Farm on maximum detail with 8x Anti Aliasing it runs between 48 - 50 C. I'll checking the temperature with the fan running normally, too.

Running at it's default speed (I'm guessing about 45%) it runs at 44 C. I'm wondering why it needs to idle so loud when there is barely a difference in temps.

---

### Post by BC59 on 2012-01-10
About Jupiter check here:
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Carpentr on 2012-01-10
> **BC59 said:**
> About Jupiter check here:
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Thanks a lot. I'll check out the link.

---

