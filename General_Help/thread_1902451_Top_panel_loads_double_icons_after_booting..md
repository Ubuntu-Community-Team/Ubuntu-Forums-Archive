---
title: "Top panel loads double icons after booting."
date: 2011-12-30
forum: General Help
---

### Post by oxf on 2011-12-30
Does anyone have  a solution to this little problem?

When booting my laptop (Compaq Presario M2000 series) some of the aplet icons in the top panel eg wireless/battery/speaker etc will load and be displayed twice. It's usually only happens to one, most often the battery icon or the speaker. It also does not happen every time and a reboot will usually solve the issue.

Not devastating in terms of functionality but annoying none the less.

Katja

---

### Post by westie457 on 2011-12-30
> **oxf said:**
> Does anyone have  a solution to this little problem?

When booting my laptop (Compaq Presario M2000 series) some of the aplet icons in the top panel eg wireless/battery/speaker etc will load and be displayed twice. It's usually only happens to one, most often the battery icon or the speaker. It also does not happen every time and a reboot will usually solve the issue.

Not devastating in terms of functionality but annoying none the less.

Katja

To save rebooting every time that happens run this in a terminal if you are still running 10.10 ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by oxf on 2011-12-30
> **westie457 said:**
> To save rebooting every time that happens run this in a terminal if you are still running 10.10 ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

OK thanks, I'll try that.

But is there a way of figuring out why this happening in the first place?

---

### Post by oxf on 2011-12-31
> **westie457 said:**
> To save rebooting every time that happens run this in a terminal if you are still running 10.10 ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```


Well that certainly fixes it and saves rebooting so thanks!

But does anyone have any thoughts on why this happens in the first place or how to investigate it?

Katya

---

### Post by oxf on 2012-01-01
Just a not to anyone else using the above command to reset the Top Panel.
This **will** delete any of your personal preferences that you've moved up there!

I just wish I could solve the original problem. However, it seems like this is quite an uncommon one, Lucky me! :(

---

### Post by oxf on 2012-01-14
This happens on more than one PC here. I find it hard to believe I'm the** only** one experiencing it!

---

### Post by oxf on 2012-03-24
Well this is STILL happening!
It's not devastating in terms of functionallity but looks weird.
I wish there was a way of fixing it as it doesn't look great..

:confused::confused::confused:

Katya

---

### Post by oxf on 2012-03-24
I'm going to mark this thread as solved and start a new one which is more explicit and descriptive of the problem. If a moderator reads this feal free to delete the this thread since I can't see a way of doing it.

---

