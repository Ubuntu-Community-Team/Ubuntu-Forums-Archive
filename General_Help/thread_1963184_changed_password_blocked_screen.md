---
title: "changed password blocked screen"
date: 2012-04-22
forum: General Help
---

### Post by alfh on 2012-04-22
Running xubuntu 11.10 on a Dell Power Workstation 380 with pentium 4 and 1 GB memory

I enabled xscreensaver and set it to lock screen after 1 minute of inactivity. Worked excellently, though I never understood why it doesn't use the same login box as on startup of the system.

Then I changed my user password.

Now xscreensaver doesn't recognize my password. When the screen locks I have to do the hard reboot (power button until machine turns off) to log back in.

Thankful for any input on this one.

---

### Post by strafe_sawdoffe on 2012-04-22
Just curious, is your old password recognized after the screen locks?

Also, I'm wondering if maybe there's a bug with the system recognizing certain characters when resuming from suspend. For example, I've seen issues where numbers aren't recognized when the screen resumes from suspend, even though the indicator LED on the keyboard says numlock is on, etc. Are there capitals or special characters in the new password? Could you temporarily change your password to something very simple like "abcd" or "1234" and try to reproduce the problem?

These are all just ideas and no definite answers, but hopefully it will at least help you stumble onto a solution.

---

### Post by alfh on 2012-04-22
> **strafe_sawdoffe said:**
> Just curious, is your old password recognized after the screen locks?

Nope, old password not recognized either.

> **strafe_sawdoffe said:**
> Also, I'm wondering if maybe there's a bug with the system recognizing certain characters when resuming from suspend. For example, I've seen issues where numbers aren't recognized when the screen resumes from suspend, even though the indicator LED on the keyboard says numlock is on, etc. Are there capitals or special characters in the new password? Could you temporarily change your password to something very simple like "abcd" or "1234" and try to reproduce the problem?

These are all just ideas and no definite answers, but hopefully it will at least help you stumble onto a solution.

Well, wadya know, changing the password to something without numbers and special characters "fixed" the problem! :o

Will check now if resetting my favourite password would work again...

Edit: It doesn't. Does xscreensaver recognize that I have Norwegian keyboard? If it thinks I'm on an English keyboard (system default is English), maybe special characters have different placings? Stripping the special characters from the password, keeping numbers, works.

---

### Post by strafe_sawdoffe on 2012-04-22
Check out this bug report, looks like the exact same problem:

[https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/828682](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/828682)

---

### Post by alfh on 2012-04-22
Looks like the one, yes - and that bug seems to be the same as this one: [https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/671923]("https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/671923")

It's declared as fixed in the package xscreensaver - 5.15-2ubuntu1

In short the x screensaver has trouble recognizing the keyboard layout, and folks who like to use special characters in their passwords (like me...) should change to simpler passwords and wait for the fix to reach the repos.


Thanks for your input, strafe!

---

