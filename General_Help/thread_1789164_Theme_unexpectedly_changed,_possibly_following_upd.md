---
title: "Theme unexpectedly changed, possibly following update"
date: 2011-06-23
forum: General Help
---

### Post by macho on 2011-06-23
I'm running Natty, and yesterday I lost the default theme that came when it was installed. It happened after a re-login, possibly following an "Update Manager" upgrade of packages.

As you can see in the attached screenshot, the taskbar is now grey instead of black, the background in my gnome-terminal is white instead of black (it uses the system theme for colours), my Thunderbird icon set has changed, etc.

Any thoughts on how I can restore the default theme (what it's called, where that setting is under unity) and, ideally, what might have caused this?

Thanks!

---

### Post by David D. on 2011-06-23
I had this happen to me about a week ago and there have been posts of it happening to some others.  A reboot fixed the theme problem for me, and I have not had a recurrence (so far anyway).

---

### Post by MSPdwalt on 2011-06-23
I had a similar problem on 10.04  It happens to me occasionally, I rigged up a script to fix it.


```
#!/bin/bash

# re-apply gnome settings

gnome-settings-daemon

# restart apps so they take the "new" settigns (you might have to add stuff here depending on what you use)

killall nautilus
killall gnome-panel
killall empathy

exit
```

---

### Post by josephmills on 2011-06-23
is this a dual boot if so what the place that it is in sdb1 ? find that out and do a```
 fsck -y /dev/whatever the partition is 
``` this will try and find any holes in the harddrive and then try to fix them

---

### Post by luca5am on 2011-06-23
Since I have been using ubuntu (about 8 months), it has happened to me regularly (but not often). A reboot  fixes it, as mentioned above but it would be nice to understand why it happens. MSPdwalt, thanks for the script, I'll try it next time it happens, it's quicker than a reboot. josephmills, I don't use dual boot.

---

### Post by MSPdwalt on 2011-06-23
I had a thought....you're using unity so your settings daemon or rather the command you run to re-apply your settings may be different.

I found a thread on it I just can't seem to find it at the moment.  If I remember right it had something to do with the gnome-settings-daemon taking too long to run occasionally or something like that...known bug...fix coming...yada...yada...just like support for alps multi-touch on 10.04 lol

---

### Post by luca5am on 2011-06-23
I'll adapt the script if necessary, it seems easy enough to find the proper commands.

It seems that quite a lot of people have reported this bug ie [https://bugs.launchpad.net/ubuntu/+source/ubuntu-gdm-themes/+bug/345558](https://bugs.launchpad.net/ubuntu/+source/ubuntu-gdm-themes/+bug/345558). The last post of this one says that it hasn't happened to the person with faster hard disks. Now that I think about it, it only happens with my small and slow laptop, it's never happened on my desktop computer. So it does look like something takes too long to run as you suggested. I doesn't sound like it would be a hard bug to fix though (like "wait longer", or 'retry after a while').

Thanks for the info anyway.

---

### Post by macho on 2011-06-24
Yes, a simple logout/login fixed it. Sorry to trouble everyone.

---

### Post by wildmanne39 on 2011-06-24
> **macho said:**
> I'm running Natty, and yesterday I lost the default theme that came when it was installed. It happened after a re-login, possibly following an "Update Manager" upgrade of packages.

As you can see in the attached screenshot, the taskbar is now grey instead of black, the background in my gnome-terminal is white instead of black (it uses the system theme for colours), my Thunderbird icon set has changed, etc.

Any thoughts on how I can restore the default theme (what it's called, where that setting is under unity) and, ideally, what might have caused this?

Thanks!Hi, here is the fix for your problem.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by luca5am on 2011-06-24
Great!! Thank you wildmanne39.

---

### Post by wildmanne39 on 2011-06-24
> **luca5am said:**
> Great!! Thank you wildmanne39.Hi, your welcome.

---

