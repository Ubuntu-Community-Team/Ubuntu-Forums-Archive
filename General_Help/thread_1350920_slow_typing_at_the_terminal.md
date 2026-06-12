---
title: "slow typing at the terminal"
date: 2009-12-09
forum: General Help
---

### Post by Steve834 on 2009-12-09
I'm trying to track slow typing speed at the terminal. It has been driving me crazy.  The terminal window cannot keep up with my typing (and I don't type that fast). No apps except the terminal are running.

I have Ubuntu 9.1 running on VMWare on Windows on a Dell.

It seems to happen all the time, except when you want to reproduce the problem. I've found a way to reproduce by holding down a key to fill up a line, then holding down the backspace key to erase all the characters.  The backspace is very jurky.  The more times you repeat the worse it gets.

I tried opening two terminal windows and running "top" in one and doing my experiment in the other. Top show nothing much going on when typing or backspacing. After releasing the backspace key however, top shows pusleaudio taking a lot of cpu cyles 12%, 30%, etc.  Is pusleaudio the problem? 

Google shows [Bug 462427] Input - Keyboad and Mouse slow with pulseaudio/alsa.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/462427](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/462427)

The bug talks about replacing pusleaudio but gives no instructions on how to do this.

I don't even use the audio very much.

Does anyone have any advice for me to solve this problem?

---

### Post by irock35 on 2011-01-31
same here :(

---

