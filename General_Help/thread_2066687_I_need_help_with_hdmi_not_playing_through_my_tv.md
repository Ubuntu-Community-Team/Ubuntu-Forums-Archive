---
title: "I need help with hdmi not playing through my tv"
date: 2012-10-05
forum: General Help
---

### Post by locky123 on 2012-10-05
Hey i have ubuntu 12.04 and i have my tv connect to my pc via hdmi and before i swtiched over to ubuntu it was working fine the hdmi cable is plugged into my nvida geforce gt430 
p.s my headphone jack works

---

### Post by newb85 on 2012-10-05
Please clarify.  What isn't working through HDMI?  The sound, the video, or both?

---

### Post by locky123 on 2012-10-05
> **newb85 said:**
> Please clarify.  What isn't working through HDMI?  The sound, the video, or both?

Just the sound

---

### Post by albandy on 2012-10-05
Go to a terminal, type alsamixer
then press F6 and select the nvidia card
unmute each hdmi channel with the M key.

---

### Post by locky123 on 2012-10-05
> **albandy said:**
> Go to a terminal, type alsamixer
then press F6 and select the nvidia card
unmute each hdmi channel with the M key.

ok there all set as 0 but still no sound

---

### Post by newb85 on 2012-10-05
You need to select the HDMI output in System Settings, Sound.  If it's not listed, you may need to restart Pulse.

---

### Post by locky123 on 2012-10-05
> **newb85 said:**
> You need to select the HDMI output in System Settings, Sound.  If it's not listed, you may need to restart Pulse.

ok well it's not listed at all i have my driver updated to the latest so idk the problem

---

### Post by pqwoerituytrueiwoq on 2012-10-05
as a person who has used a GT 430 with HDMI and got i working 
[http://ubuntuforums.org/showthread.php?t=1926721]("http://ubuntuforums.org/showthread.php?t=1926721(covers") (covers a 550 ti and gt 430)
 on ubuntu 10.04 (10.10+ don't need extra work like this)

this will give you some speaker test commands
```
aplay -l | grep card | sed 's/://g' | awk '{print "speaker-test -Dplughw:"$2","$7" -c2"}'
```
find the one that works and tell us which

---

### Post by newb85 on 2012-10-05
> **locky123 said:**
> ok well it's not listed at all i have my driver updated to the latest so idk the problem

And did you try restarting pulse, as I mentioned?

```
pulseaudio --kill
```

---

