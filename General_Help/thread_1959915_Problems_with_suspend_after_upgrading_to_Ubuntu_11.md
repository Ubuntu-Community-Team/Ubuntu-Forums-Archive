---
title: "Problems with suspend after upgrading to Ubuntu 11.10"
date: 2012-04-16
forum: General Help
---

### Post by kotek on 2012-04-16
Hello company,
I've just upgraded my Asus netbook (EEE PC) to Ubuntu 11.10, and I've found that I can't suspend it any more. It worked perfectly with the previous version, even with no swap partition. I've already created a swap to see if it helped, but the problem seems to be far from there. /var/log/pm-suspend.log says:
Unhandled kernel version: 3.0 ('uname -r' = '3.0.0-17-generic')
I've tried several update-initramfs -u with no success...
Any ideas?

---

### Post by Toz on 2012-04-16
Do you have laptop-mode-tools installed? If so, you could be suffering from this bug: [http://askubuntu.com/questions/74338/unhandled-kernel-version-error-when-trying-to-install-laptop-mode-tools]("http://askubuntu.com/questions/74338/unhandled-kernel-version-error-when-trying-to-install-laptop-mode-tools"). A workaround is suggested in that thread.

---

### Post by kotek on 2012-04-16
Thanks, good suggestion, I actually have laptop-mode-tools, but although I've applied the workaround it still doesn't suspend... Now it's even worse, because there's no error message at all:

/var/log/pm-suspend.log

```
enabled, active

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>>
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


```

Do you think the problem is still laptop-mode-tools?

---

### Post by Eirreann on 2012-04-16
So what is happening when you suspend?  Does your computer show a white screen with black stripes/flakes on it?

---

### Post by kotek on 2012-04-16
The screen starts to fade out for a couple of seconds, but then it suddenly comes back to life with this little box that asks for the password to unlock the session...
Sometimes, it really seems to be going to suspend, the screen gets darks for some 8 seconds, but finally same thing.

---

### Post by Toz on 2012-04-16
It might not be worse. You may have eliminated the original problem, but just uncovered the next one.

Can you post the complete contents of the /var/log/pm-suspend.log file (you posted only the last little bit)?

And exactly what model of Asus EEE do you have?

---

### Post by kotek on 2012-04-17
This is all I have in my pm-suspend.log, not just the last bit...
About the computer, it's an Asus EEE PC 901.

---

### Post by Toz on 2012-04-17
A couple of suggestions to try:

1. Try the fix listed at this page: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug").

2. Look in your bios under CPU settings and if you have an option to disable C9, then select it and try the suspend function.

3. If neither of those two work, then in a terminal window, type in these commands:
```
export PM_DEBUG=true
sudo pm-suspend
```
...and you should get a much more detailed /var/log/pm-suspend.log file. First post back the results of:
```
ls -l /var/log/pm-suspend.log
```
...and then attach the file to your reply.

---

### Post by kotek on 2012-04-19
No way, man, I've done all this. The first post you mentioned was actually the first thing I tried after my google search, before writing here...
About the rest, nothing. And my /var/log/pm-suspend.log is as poor as always:

ls -l /var/log/pm-suspend.log
```
-rw-r--r-- 1 root root 809 2012-04-19 16:47 /var/log/pm-suspend.log

```

/var/log/pm-suspend.log
```
enabled, active

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
```

---

### Post by kotek on 2012-04-21
All right, it's not really a solution but I managed to suspend, even without swap partition, using s2ram as explained here:

[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

So I'll mark the issue as solved. Thanks anyway Toz and Eirreann!

---

