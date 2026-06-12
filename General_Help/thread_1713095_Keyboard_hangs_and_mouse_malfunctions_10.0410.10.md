---
title: "Keyboard hangs and mouse malfunctions 10.04/10.10"
date: 2011-03-23
forum: General Help
---

### Post by grigglestone on 2011-03-23
First I want to note that there is already defect [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720)

As I explained in that defect, disabling irqbalance has no effect.

Since I had not posted to the forum I thought I'd at least try here since no one seems to be picking the issue up in the bug tracking system and looking at the differences between whats been reported. Also for me this started with 10.4 (9.10 was fine) and I am now on 10.10 and the issue is still happening.

I have a Dell E6500 with Nvidia.

I can consistently reproduce the issue and have a workaround that works most of the time.

These are the steps to repo:

[LIST=1]
[*]Login
[*]Create a console
[*]Type between 3 to 8 characters
[/LIST]
At this point the keyboard is locked (no further input is accepted from any key) and when I select a top level menu in any window, the drop down never appears.

To work around the problem (most times):

[LIST=1]
[*]At the login prompt type a bunch of garbage and erase it
[*]Repeat 1.
[*]Enter my actual password
[/LIST]
After this things seem to be ok. I can't remember how I came across this workaround and I'm not sure whats its actually influencing .. but it seems to work. Occasionally the keyboard/mouse still locks up after 4 to 8 hrs.

There must be some timing issue, but I'm not that familiar with the boot sequence to know of anything else to try.

I'm willing to try some diagnostic code, but no offers yet.

Anyone have any thoughts as to what might be going on or can correlate the full set of behaviors (login, keyboard, mouse, workaround) to at least narrow down what modules might be involved?

---

### Post by grigglestone on 2011-09-19
fyi .. found the issue is to do with a keyboard PS2 connector with the Microsoft Wireless Keyboard (1.0A)

using a PS2 to USB adapter works around the issue

(see [http://ubuntuforums.org/showthread.php?t=1546149&page=2](http://ubuntuforums.org/showthread.php?t=1546149&page=2))

---

