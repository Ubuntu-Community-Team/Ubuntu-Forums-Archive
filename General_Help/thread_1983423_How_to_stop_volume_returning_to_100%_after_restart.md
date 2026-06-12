---
title: "How to stop volume returning to 100% after restart"
date: 2012-05-20
forum: General Help
---

### Post by Macfunky on 2012-05-20
Every time i restart ubuntu (12.04) i find that the sound menu has jumped back to 100% volume. Is there a way to keep it at the same level as when i logged out as it scares the crap out of me every time i play music cause i keep forgetting about it :P

---

### Post by georgezenios on 2012-05-26
same bug here really stupid bug blasts out at maximum volume because its not the first thing you remember when you reboot. kids get woken up if late at night, scares the crap out of the neighbours. just stupid sort it out ubuntu.

---

### Post by Macfunky on 2012-05-29
> **georgezenios said:**
> same bug here really stupid bug blasts out at maximum volume because its not the first thing you remember when you reboot. kids get woken up if late at night, scares the crap out of the neighbours. just stupid sort it out ubuntu.

It's very frustrating. I have found that it happens across different desktop enviroments, xfce, gnome shell and unity. Is this specific to Ubuntu?

---

### Post by steeldriver on 2012-05-30
If this is related to alsa, there may be things you can do with 'alsactl store' and 'alsactl restore' (at least it seems to have fixed the opposite problem for me - max volume becoming subliminal on reboot)

Basically you use 'alsactl store' when you've got everything set up to the levels you want, then arrange to run 'alsactl restore' on startup - either:

1. system wide (i.e. all users) you can use 

```
sudo alsactl store
```one time, which creates a default state file /var/lib/alsa/asound.state, and then put

```
sleep 10 && alsactl restore
``` somewhere before the final 'exit 0' statement in /etc/rc.local (I read somewhere that the 'sleep  10' is there to make sure pulseaudio has finished messing with things)

2. per user

I haven't tried this but it should be possible to run an equivalent command in ${HOME}/.config/autostart - in that case you will probably need to give it a state file location somewhere in your home dir and pass that to both the 'store' and 'restore' commands - there is likely a 'correct' place for that but I don't know what it is

Hope this gets you started

---

### Post by HallunX on 2012-05-30
Hi guys i am new Linux user and I found this problem too, Im using Ubuntu 12.04. Is this is fixable I mean how to get rid of it till update come ?


Sorry  for my English.

---

### Post by BoogeyOfTheMan on 2012-07-20
I get:

alsactl: get_control:259: Cannot read control '2,0,0,Mic Capture Volume,0': Invalid argument

When I try to run it

My problem is that whenever I boot, my sound is muted and my volume is back to 50%. I just want my volume levels to stay how they were when I rebooted.

---

