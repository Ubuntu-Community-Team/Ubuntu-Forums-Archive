---
title: "Reboot drops sound settings ( back to default - muted )."
date: 2009-12-03
forum: General Help
---

### Post by endBc on 2009-12-03
Have anybody experienced such behavior ? Reboot reverts my settings back to the default - Master and PCM muted.
Why it does so and *who* is responsible for saving/loading these settings ?

---

### Post by kostaben on 2009-12-03
same here.

---

### Post by falconindy on 2009-12-03
Set your volume to whatever you want the defaults to be and then..
```
sudo alsactl store 0
```

---

### Post by endBc on 2009-12-03
```
endbc@ubuntu:~$ sudo alsactl store 0
[sudo] password for endbc: 
Home directory /home/endbc not ours.

```

```
endbc@ubuntu:~$ alsactl store 0
alsactl: save_state:1530: Cannot open /var/lib/alsa/asound.state for writing: Permission denied
```

What I'm missing here ?

---

### Post by falconindy on 2009-12-03
Not sure, was a bit of a guess laced with hope that Pulse wasn't getting in the way.

*Starts up Karmic VM*

Odd. I get the same error message as a user, but nothing back (a good thing) when I run it with sudo. At least this is hope that Pulse isn't being... well, Pulse.

A little more poking around reveals that it's a permissions problem. Duh. I found a post on these forums eluding to the idea that ownership in your home directory might be off. To correct that, do:

```
sudo chown -R $USER:$USER $HOME
```
If that doesn't work, I found [this](https://answers.launchpad.net/ubuntu/+question/68564) which gives the workaround of commenting out the line in alsa-utils that mutes your volume on exit. Open up /etc/init.d/alsa-utils with sudo in your favorite text editor and scroll down to line 378, which should be:
```
mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS 1
```
Toss a # in front of this line to comment it out. Be forewarned that this can and will be reverted if there is ever an update to ALSA.

hth.

---

### Post by endBc on 2009-12-03
> **falconindy said:**
> Open up /etc/init.d/alsa-utils with sudo in your favorite text editor and scroll down to line 378, which should be:
```
mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS 1
```Toss a # in front of this line to comment it out. Be forewarned that this can and will be reverted if there is ever an update to ALSA.

Thank you - problem solved by adding # in front of [COLOR=Green]mute_and_zero_levels[/COLOR] :)

---

