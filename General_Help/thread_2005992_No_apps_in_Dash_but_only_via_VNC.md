---
title: "No apps in Dash but only via VNC"
date: 2012-06-18
forum: General Help
---

### Post by AlexBooton on 2012-06-18
Suddenly Dash stopped displaying any applications.  It still shows everything else: files, video, etc.

And yes, the "Home" filter is set.

This only happens when I view the desktop from a remote client. A tightvnc server is running on the 12.04 box.  From the 12.04 box itself, Dash works fine.

And this happened recently.  It had been fine till yesterday.

I've tried everything I could find via google.  I removed ~/.local/share/zeitgeist and rebooted.  Zeitgeist came back but still I can't access any applications.

Any ideas?

Thanks,

AB

---

### Post by xp15 on 2012-06-18
I don't sure if that will solve it, but you can reset unity (or maybe you have already tried it).

in terminal (Ctrl+Alt+T):
```

unity --reset

```

it may take a while. it normal if the windows are changing. wait till it finish.
I guess reboot didn't help too.

---

### Post by AlexBooton on 2012-06-18
> **xp15 said:**
> I don't sure if that will solve it, but you can reset unity (or maybe you have already tried it).

in terminal (Ctrl+Alt+T):
```

unity --reset

```

it may take a while. it normal if the windows are changing. wait till it finish.
I guess reboot didn't help too.

Hi xp15,  Thanks for the idea.  I tried it but it didn't help.

It's difficult to do from a VNC session because without the Dash you can't bring up a terminal (at least I don't know how).

But I did it directly from the desktop and it didn't help.  

In fact, it returned a slew of error and I had to reboot to get it working again.

Any other thoughts?

Remember, this is only a problem in a VNC session.

Thanks,

AB

---

