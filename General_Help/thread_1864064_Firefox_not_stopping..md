---
title: "Firefox not stopping."
date: 2011-10-18
forum: General Help
---

### Post by Synoc on 2011-10-18
Ok on occasion, mostly all the time now, when I close Mozilla Firefox. it doesn't not kill firefox-bin. it's not zombied according to top, but a simple ps -A shows it is still running. What's worse is this happens back when I used Windows with firefox.exe as well. it has gotten to the point where I set up an app launcher with the simple instruction:
```
 killall firefox-bin 
``` 
and set it up on my panel just so I don't have to type it into terminal 12 ro 20 times a day.
The only solution I have to try is uninstalling and reinstalling firefox. but I am not a fan of using a windows method of problem solving on a superior operating system. so any better ideas? I would like to know WHY this is happening so I don't have to deal with it again.

Ubuntu 10.10

---

### Post by Synoc on 2011-10-18
sorry to bump, but... BUMP

---

### Post by lovinglinux on 2011-10-18
Please wait at least 24 hours before bumping.

Close Firefox and start it in safe mode and check if it shuts down properly.

```
firefox -safe-mode
```

If that doesn't help, create a new profile, just to see if you can reproduce the problem.

```
firefox -P
```

---

### Post by Synoc on 2011-10-18
yes it happens in safe mode and a new profile as well

at the end of one of the safe mode startups from terminal I got this  code before it did not shut down, I also got this same code and it DID... and in the new profile I did not get it and it still didn't shut down. nonetheless, here is the code.

```

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4091): Gdk-WARNING **: XID collision, trouble ahead
NOTE: child process received `Goodbye', closing down

```
The note appears after I close the window, but no prompt appears until after I killall firefox-bin.

---

### Post by galvatron408 on 2011-10-18
[http://support.mozilla.com/en-US/questions/666158](http://support.mozilla.com/en-US/questions/666158)

---

### Post by lovinglinux on 2011-10-18
> **Synoc said:**
> yes it happens in safe mode and a new profile as well

at the end of one of the safe mode startups from terminal I got this  code before it did not shut down, I also got this same code and it DID... and in the new profile I did not get it and it still didn't shut down. nonetheless, here is the code.

The note appears after I close the window, but no prompt appears until after I killall firefox-bin.

Does it happen if you only open a blank page?

From my experience, this problem comes and go. It tends to disappear with some updates.

---

### Post by Synoc on 2011-10-19
I'll be honest I've never opened a blank page. and this problem did just start happening a couple weeks ago. and it's not every time. so it makes it hard to reproduce.

Also I looked at that link, mine does not use any extra CPU, nonetheless I looked into it and my settings were already correct.

---

### Post by lovinglinux on 2011-10-20
If it happens with a clean profile, then  it probably will go away with some update. Meanwhile use the killall firefox-bin.

---

