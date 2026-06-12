---
title: "Screen Brightness"
date: 2010-09-20
forum: General Help
---

### Post by Startacus on 2010-09-20
Hello, I have an HP Mini 5102 running Windows 7 Professional and Ubuntu Netbook Remix. I am having issues with my display brightness in Ubuntu. It appears to be capped. It is telling me that it's brightness is all of the way up but it is significantly dimmer than it is in Windows, this is both on battery and on AC. 

I was wondering if there is some sort of brightness cap or something and if there is a way I can fix it.

Thanks.

---

### Post by afrowildo on 2010-09-20
Try

```
smartdimmer -s <brightness level between 15 and 100 here>
```

---

### Post by yerayenrique on 2010-09-23
I got another solution.

$ sudo apt-get install xbacklight

Then, to change it:

$ xbacklight -set X (where X, is the value you want, from 0 to 100).

---

### Post by Startacus on 2010-09-23
I've tried both of those. I get an error on the smartdimmer and xbacklight doesn't make it any brighter. I don't know, maybe it's just me but it seems like the screen gets a lot brighter in Windows 7 than it does in Ubuntu.

---

### Post by yerayenrique on 2010-09-24
> **Startacus said:**
> I've tried both of those. I get an error on the smartdimmer and xbacklight doesn't make it any brighter. I don't know, maybe it's just me but it seems like the screen gets a lot brighter in Windows 7 than it does in Ubuntu.

This maybe me a stupid question but have you carefully checked the settings under System/Power Manager? Can't come up with anything more especific atm.

---

### Post by afrowildo on 2010-09-24
What was the smartdimmer command that you used (exact wording please) and what was the error you received?

---

### Post by Startacus on 2010-09-24
> **afrowildo said:**
> What was the smartdimmer command that you used (exact wording please) and what was the error you received?

```

smartdimmer -s 100
init.nvclock() failed!

```



All of my options in the settings and the power manager are fine. I don't know, maybe it's just me. It's at least enough of a difference where I'm noticing it. It seems that when it's on the AC adapter it's fine. I'll have to try and do some closer comparison when I get a chance.

---

### Post by Startacus on 2010-09-30
After a little bit of further research. I've figured out that the screen brightness is fine if I restart the computer while it's plugged in. However, if I start the machine when it's running on battery then the screen will be significantly dimmer at max, whether I plug it in afterward or not.

Is this a common bug or what?

---

### Post by luvshines on 2010-09-30
Make sure that 'Reduce backlight brightness' is not checked in System->preferences->power management->on battery power

---

### Post by afrowildo on 2010-09-30
Here's a thread started by someone with the same problem related to smartdimmer. The OP hasn't specified whether or not it was successful, but it's worth a try nonetheless.

[http://ubuntuforums.org/showthread.php?t=100902](http://ubuntuforums.org/showthread.php?t=100902)

FWIW, I'm currently running the Maverick Development Release and I'm not having this problem, while I did have it in Lucid. You may find that upgrading to Maverick on 10th October (or sooner if you're feeling adventurous) makes the problem go away.

---

### Post by Startacus on 2010-09-30
> **afrowildo said:**
> Here's a thread started by someone with the same problem related to smartdimmer. The OP hasn't specified whether or not it was successful, but it's worth a try nonetheless.

[http://ubuntuforums.org/showthread.php?t=100902](http://ubuntuforums.org/showthread.php?t=100902)

FWIW, I'm currently running the Maverick Development Release and I'm not having this problem, while I did have it in Lucid. You may find that upgrading to Maverick on 10th October (or sooner if you're feeling adventurous) makes the problem go away.

When I try to follow that guys directions it says that there is nothing to do for install. Would I have have to install the version from apt-get first?

Also, were you having the same issue with smartdimmer or with the screen brightness?


And luvshines, I double checked that, it's not checked.

---

### Post by afrowildo on 2010-09-30
I was having the problem with screen brightness, utntil I gave smartdimmer a go right now and got the exact same error message as you. I'm looking look into this and get back to you later today.

---

### Post by borderblu on 2010-09-30
I'm having the same problem, going through the steps suggested, downloading smartdimmer, making sure the brightness swithch in power management was off - still get the nvlock error msg. I know what set it off, my battery went  critical and my laptop turned off, and ever since, i've had had the dim screen.

---

### Post by bananafishbones on 2010-09-30
I'm getting the same thing on a new install of 10 on a Inspiron 1501. The screen is noticeably dimmer than XP just a few hours ago before wiping it and installing U.

When I try the brightness buttons on the keyboard it goes dim then brighter, back down to the same dimmness then back to the same level of brightness. I actually have a brigher screen with the Dell set to half-brightness. It's like the controls are not correct.

I tried the two suggestions here as well. No go. The error message for dimmer as well.

WTH?

---

### Post by borderblu on 2010-09-30
I just upgraded to Lynx 10.04 real-time kernel, same problem, I was able to reproduce it by putting the laptop into suspend-mode. I went to the power settings and adjusted brightness, just toggled it down a bit and back up and the brightness was back to normal.

---

### Post by Startacus on 2010-10-27
> **borderblu said:**
> I just upgraded to Lynx 10.04 real-time kernel, same problem, I was able to reproduce it by putting the laptop into suspend-mode. I went to the power settings and adjusted brightness, just toggled it down a bit and back up and the brightness was back to normal.

So you just go to the menu, turn the brightness down and bit and then crank it back up?

I upgraded to the latest version of Ubuntu but I'm still having issues.

---

