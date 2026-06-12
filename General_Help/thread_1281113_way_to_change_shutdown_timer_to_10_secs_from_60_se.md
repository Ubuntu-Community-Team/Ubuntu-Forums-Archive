---
title: "way to change shutdown timer to 10 secs from 60 secs??"
date: 2009-10-02
forum: General Help
---

### Post by gordong11 on 2009-10-02
Is there a way to change the amount of time in 9.04 shutdown and restart timers? They are set at 60 seconds and I would like to change them to 10 seconds.

I do know how to disable the timer in the preferences menu so this is not a life-changing problem but would be nice. Thanks

---

### Post by SkyNet2029 on 2009-10-02
you could always run fromo terminal like this

# shutdown -t

where t is time in seconds

---

### Post by dcstar on 2009-10-02
> **gordong11 said:**
> Is there a way to change the amount of time in 9.04 shutdown and restart timers? They are set at 60 seconds and I would like to change them to 10 seconds.

I do know how to disable the timer in the preferences menu so this is not a life-changing problem but would be nice. Thanks

I would say it is hard coded in the FUSA applet.

You can put in a bug report or add to this one:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/398687](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/398687)

---

### Post by HereInOz on 2009-10-02
You can turn it off completely by right clicking on the shutdown button in the top right hand corner, then click Preferences, then untick Show confirm dialogs for logout, restart and shutdown.

Best solution I have found.

---

### Post by HereInOz on 2009-10-02
Sorry, didn't read the last line of your original post.  Doh!!

---

### Post by abhilashm86 on 2009-10-03
use this command,
```

sudo shutdown -P (time required)

```

---

