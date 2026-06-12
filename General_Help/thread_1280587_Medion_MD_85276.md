---
title: "Medion MD 85276"
date: 2009-10-02
forum: General Help
---

### Post by Arwenac on 2009-10-02
Hi everyone,

This is my first post so I hope I'm getting this right.

I have a drawing tablet and it worked fine in windows, but a few months ago I decided to try out Ubuntu and I'm hooked. The problem is that ubuntu recognizes the tablet and when I move my stylus over the tablet my mouse moves but it is impossible to click. When I tap the tablet it doesn't and  I don't have any bottons on my stylus. I tried a lot of thing with the .fdi files(which I made.) But I'm clueless. 
Sometimes when de stylus hovers over the tablet the mouse moves and the next time it only moves when you have the stylus on the tablet. I realy fon't get it anymore...
Does anyone have any ideas?
Thanks for the help

---

### Post by Favux on 2009-10-02
Hi Arwenac,

Welcome to Ubuntu Forums!

Which version of Ubuntu are you using?

It sounds like your tablet is being detected as a mouse.  You can check this out and get useful info. by entering in a terminal:
```
xinput --list
```

First you need to know what the underlying tablet is.  Then you can determine if you need an aiptek driver, wizardpen driver, etc.  Practic describes this in post #11 here:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)  And a little more on this:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

