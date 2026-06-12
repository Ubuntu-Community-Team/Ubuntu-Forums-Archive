---
title: "Problem booting with usb drives plugged in"
date: 2011-09-13
forum: General Help
---

### Post by rmcellig on 2011-09-13
When I have both or only one of my external usb drives plugged into my HP laptop, my computer hangs on startup (flashing white underline) before I even get to the grup menu. Unplugging them allows my laptop to startup properly. On my other HP laptop, I don't have this problem. What could be causing this. both computers are running Ubuntu 11.04.

Do you want me to post anything back to this thread?

---

### Post by seawolf167 on 2011-09-13
Turn on your computer, press [F2] to enter BIOS during POST (or whatever your specific key is), go to the "Boot" section and ensure that USB booting has a *lower* priority than hard drive booting (or specifically, your boot drive). It is ok (and even desired) to have cd/dvd booting prioritized above hard drive booting, so don't worry if that it the case.

---

### Post by haqking on 2011-09-13
> **seawolf167 said:**
> Turn on your computer, press [F2] to enter BIOS during POST (or whatever your specific key is), go to the "Boot" section and ensure that USB booting has a *lower* priority than hard drive booting (or specifically, your boot drive). It is ok (and even desired) to have cd/dvd booting prioritized above hard drive booting, so don't worry if that it the case.

+1

You most likely have your BIOS order looking at USB.

You only need this to boot from a USB device, so either move it down in the list or disbale it completely which is more secure from a physical access point of view, as is CD/DVD booting also

---

### Post by rmcellig on 2011-09-13
shame on me for not noticing this! BIOS. I guess I thought that because I had Ubuntu on my laptop and not Windows that the BIOS didn't play in to it. Works great now!!!

---

### Post by haqking on 2011-09-13
> **rmcellig said:**
> shame on me for not noticing this! BIOS. I guess I thought that because I had Ubuntu on my laptop and not Windows that the BIOS didn't play in to it. Works great now!!!


ha we all do it, i have had senior moments since i was 16...LOL

anyways make sure you mark the thread as solved using thread tools to aid others when searching for answers.

Peace

---

### Post by rmcellig on 2011-09-13
I turn 55 tomorrow so it must be that :) I will mark this thread as solved. Thanks for waking me up.

---

