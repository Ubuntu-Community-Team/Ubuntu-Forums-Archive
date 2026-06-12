---
title: "my machine freezes while working"
date: 2012-07-24
forum: General Help
---

### Post by bestdnd on 2012-07-24
my machine freezes a lot (no keyboard, mouse, ping from outside etc., screen stops updating but keep the last image).
it happens mainly while in a wine game (diablo, sometimes in zone transaction and background saves), but also in amule and rarely when idle.

last entry in /var/log/syslog before it froze last time is about 15 min. before.

someone suggested checking for overheating.
i installed Psensor, and it showed about 89c (core0 and core1) while freezing, but on other cases of hard work, i got up to 98c while still working.

i'm using ubuntu 12.04.

what else can i check?

---

### Post by americanman28 on 2012-07-24
the sensor thats very unlikly

---

### Post by CaptinGoogle on 2012-07-24
It could be almost anything. It could be a graphical setting or perhaps even a conflict of some sort depending upon whether you upgraded or did a fresh install. There's really not enough information to tell.

If it's freezing while you're gaming and using wine then it could be some conflict with Diablo and wine.

You could leave the cover of your case off while gaming if you think that it's overheating.

---

### Post by BrumlePostmann on 2012-07-24
Hmmm, running the computer with the cover off could rise the temperature. 

I don't think it's overheating due to the fact that temperature reading (psensor) is'nt very high. Maybe it's an idea to check how much temperature the processor can handle.

My computer did not freeze, but responded very slowly, video streams went jerky and it were almost impossible to move the mouse from one monitor to the other. Logged out and used Unity 2D instead. Problem occurred usually after a day or so, rebooting made it run ok for another day. Alas I'd have to see tomorrow if it go into the tarpit again.

---

### Post by bestdnd on 2012-07-25
it's probably not overheating, because it can reach higher temperature (as i said, i got up to 98c without freezing).
note that the temperature reading might be off, because some mother boards do not calibrate their reading, and sone cpus can handle higher or lower max temperature.

about the conflict with Diablo, it also happens with other programs or even (rarely) when idle.

i'll try to use 2d desktop, but the freezing is not predictable, and it might take it a few days to freeze again.
in addition, i will try the REISUB thing
[http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717]("http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717")

---

### Post by Statia on 2012-07-25
Could be faulty RAM. You could run memtest86. I think the Ubuntu installer has the option to boot to memtest86.

---

### Post by barefoot138 on 2012-08-09
I also have the same problem, except the mouse is still working, NOTHING is working besides the mouse!!! Seriously how does that even make sense? Anyways I think Ubuntu isn't using my machine's full capabilities and would appreciate a fix!

---

### Post by johnathansmith on 2012-08-09
This could be serious problems with your HDD. Make backup (if you already din't), run S.M.A.R.T and look on the results. Also if you using Transmition torrent client, a downloading files into /home when /home is being crypted - it will lead to fails + freezing (at least this happen to me).

---

