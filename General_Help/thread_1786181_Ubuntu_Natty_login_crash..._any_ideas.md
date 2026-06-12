---
title: "Ubuntu Natty login crash... any ideas?"
date: 2011-06-19
forum: General Help
---

### Post by ozzy441 on 2011-06-19
Ok, so basically, I've installed nice new fresh 11.04. This is when the problems started. Downloaded, burt and verified the amd64 (as I have an AMD 64bit system) iso for install. Booted up, ran install fine (connected to wireless, it seems Ubuntu now ships with broadcom wireless drivers of some description) so updates were downloaded. Setup fine. Reboot, login aaaaand... crash. Well, freeze. Actually, a bit of both. In all environments except safe mode, at some point after login (randomly, but doesn't normally take too long) the screen 'sticks'. Everything stays on the screen exactly where it was, including the pointer, but no interation is possible. I then have to forcibly shut down (press power button) and re-boot.
Does anybody have any ideas? I've seen a few similar problems, but they originate around graphics drivers (I'm just using standard, because I can't log in long enough in a network-enabled environment to download the proper ones) and wireless (but if that was the case, surley the liveCD session would have crashed when wireless was enabled, as I haven't added any additional drivers. Actually, I haven't added any additional software, once again because I can't get into an environment which allows networking for long enough to do so). Besides, these problems seem to show different symptoms from mine.
>>EDIT
Forgot to mention, installing 10.10 from liveCD (32bit) works fine-and this also appears to include drivers for broadcom, as live session also allows connection to my wifi. However, when I update from 10.10 to 11.04 (which is still in 32bit, for obvious reasons), my problems start all over again.

---

### Post by dino99 on 2011-06-19
64 bits is mainly for headache & nightmare lovers :(

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

before dropping your hardware over the window, try to repair package(s) booting in recovery mode (hold "shift" key down at end of bios process to see grub menu)

---

### Post by ozzy441 on 2011-06-19
> **dino99 said:**
> 64 bits is mainly for headache & nightmare lovers :(
As I said, I get the same problem with the 32bit version of 11.04

---

### Post by ozzy441 on 2011-06-22
Bump. Anybody?

---

