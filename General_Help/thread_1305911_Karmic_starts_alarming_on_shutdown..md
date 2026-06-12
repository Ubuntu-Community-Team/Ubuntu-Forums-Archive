---
title: "Karmic starts alarming on shutdown."
date: 2009-10-30
forum: General Help
---

### Post by Barafu Albino Cheetah on 2009-10-30
I have made a fresh install of Karmic RC Kubuntu, and upgraded it. 

When I switch off computer using kde menu, sometimes all goes fine, and I see a blue progressbar. But sometimes, I see only black screen, and kubuntu starts to alarm with a built-in buzzer. It produces a constant unstopping sound. However, the shutdown process stops in time. 

kernel log shows about "dsp access error" but I don't know if it is relevant. What is dsp by the way?
X log and system log show nothing curious. 

How can I get what goes wrong?

---

### Post by Barafu Albino Cheetah on 2009-10-30
Any ideas?

---

### Post by P4man on 2009-10-30
dsp is digital signal processor. I would guess that refers to a soundcard.

You can prevent the beeping by blacklisting the pcspkr module in /etc/modprobe.d/blacklist.conf although that seems to be in there by default

Not sure what the root cause is, but if it shuts down nicely otherwise, I wouldnt worry too much.

---

### Post by wd5gnr on 2009-10-30
The dsp is your oss sound card. I had Jaunty sound working after much fussing and Karmic totally broke that. So I'd look at your sound. Are you running pulse audio? Are you running anything that uses sound when you log off.

Me, when I try to log off nothing happens. I think I may know why, but have to experiment. Overall the upgrade to Karmic did little positive for me and cost me a day trying to retweak everything.

> **Barafu Albino Cheetah said:**
> I have made a fresh install of Karmic RC Kubuntu, and upgraded it. 

When I switch off computer using kde menu, sometimes all goes fine, and I see a blue progressbar. But sometimes, I see only black screen, and kubuntu starts to alarm with a built-in buzzer. It produces a constant unstopping sound. However, the shutdown process stops in time. 

kernel log shows about "dsp access error" but I don't know if it is relevant. What is dsp by the way?
X log and system log show nothing curious. 

How can I get what goes wrong?

---

