---
title: "A most likely already discussed topic: /swap space"
date: 2010-09-05
forum: General Help
---

### Post by Lyude on 2010-09-05
This is my question, since Googling this seems to give me tons of yes awnsers and at the same time, tons of no awnsers. I run a amd64 Ubuntu Lucid Lynx desktop with 4 GB of ram. I installed this OS without using /swap, and I believe I noticed that it was a lot faster then my last install of Ubuntu (although that install was broken from the start, and went on to commit suicide). Now I have never once ran out of RAM, neither on Windows (I used to use x64 vista as my main OS, although windows would nag at me if I disabled my virtual paging file for some reason, despite the fact I was not even close to running out of ram) nor on Debian or Ubuntu. I am no Linux expert, however after the past few months on Ubuntu I have learned quite a lot about Linux, and I'd like to say I'm pretty good with it. Since I'm no expert though, I'd like to ask if having a /swap on a system that will most likely never run out of ram will 1-up the overall performance of the system.

---

### Post by Old_Grey_Wolf on 2010-09-05
There is not a yes or no answer. It depends on how you use your computer. Ubuntu has a FAQ about swap that may help you ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)) figure out the answer for your needs.

---

### Post by uRock on 2010-09-05
If you want the ability to hybernate your system, then you will need a swap partition of an equal or greater value than your RAM. If you are using a desktop and never allow your system to sleep, then you will only need swap if you plan to run virtual machines or some other really heavy applications.(Or KDE)

---

### Post by Lyude on 2010-09-05
I think I've hibernated without a problem on here... I'll have to try again to make sure

---

### Post by Lyude on 2010-09-05
Oh wow, the Hibernation option isn't even there O_o, I guess I do need a /swap.

---

### Post by uRock on 2010-09-05
'It knows"

:lolflag:

---

### Post by Lyude on 2010-09-05
I'm about to set up a /swap partition, how do I get Ubuntu to use it when I'm done?

---

### Post by uRock on 2010-09-05
It is all here in the link [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by tgalati4 on 2010-09-05
In the rare event that you run out of RAM, the swap space will cause your machine to slow down.  You can watch your RAM levels with one of several tools:  top, htop, system monitor, etc.

Without swap, when you run out of RAM, you have limited options to take over control if your machine seems hung.  Swap space allows your machine to continue (although slowly) giving you a chance to close applications to free up RAM.

A swap partition is also handy for testing other Live CD distros; you'll sometimes get better performance.

---

### Post by Lyude on 2010-09-05
Sorry xD, I forgot to check that link. Anyway, thanks for the help ^^

---

