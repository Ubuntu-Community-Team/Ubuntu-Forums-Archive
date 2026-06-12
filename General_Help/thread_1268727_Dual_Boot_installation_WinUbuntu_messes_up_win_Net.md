---
title: "Dual Boot installation Win/Ubuntu messes up win Networking"
date: 2009-09-17
forum: General Help
---

### Post by am7555 on 2009-09-17
Hello,

I have installed ubunut 9.04 beside my windows XP System. All is well both systems run nicely except for the Networking capabilities in Windows. I cannot connect to the internet when I boot in Windows. I get an error saying that the Networking cable is disconnected. Obviously the cable is just fine because I can boot Ubuntu and all works fine.

Any ideas and suggestion are appreciated. Note that Before Ubuntu, Windows was running 100%.

Javier

---

### Post by stinkeye on 2009-09-17
Have you tried tightening the ubunut.

---

### Post by am7555 on 2009-09-17
How do you do that? I'm fairly new to Ubuntu -- a little guidance would be great.

What do you mean tighten it up?

---

### Post by mike555 on 2009-09-17
I notice on my dual boot if I shut down for a couple of minutes and let the router "think" ,then start into the other OS it works better then just restarting.  something about different host names I guess.

---

### Post by am7555 on 2009-09-17
I'll give it a try. It seems odd though.

---

### Post by stinkeye on 2009-09-17
> **am7555 said:**
> How do you do that? I'm fairly new to Ubuntu -- a little guidance would be great.

What do you mean tighten it up?
Sorry about that,just my little joke.
You missed it.
> **am7555 said:**
> Hello,

I have installed [COLOR="DarkRed"]*ubunut*[/COLOR] 9.04 beside my windows XP System. All is well both systems run nicely except for the Networking capabilities in Windows. I cannot connect to the internet when I boot in Windows. I get an error saying that the Networking cable is disconnected. Obviously the cable is just fine because I can boot Ubuntu and all works fine.

Any ideas and suggestion are appreciated. Note that Before Ubuntu, Windows was running 100%.

Javier
AS far as I know Ubuntu shouldn`t affect your windows install. It just places grub in your mbr on your windows partition so you have a dual boot menu. May well be some router quirk as the previous poster suggested.

---

### Post by am7555 on 2009-09-17
Joke? :)
ESL you know, sometimes jokes fly over my head...not that I lack a sense of humor. 

Cheers.

---

### Post by danwood76 on 2009-09-17
Make sure you power down before booting XP (not restarting) its possible that the linux drivers leave something in the cards RAM which the XP drivers dislike.

---

### Post by sedawk on 2009-09-17
Like the previous poster said, check if that only happens if
you go from Ubuntu to windows (warm-boot), or if it
also happens if you turn off the machine and
then turn it on again to boot windows (cold-boot).
(and in case the cold-boot doesn't work: try to fully
 turn of the PC, disconnecting it from power with a
 "real" switch or by unplugging the power cord for a few
 seconds).

Sometimes this happens (sound not working, mouse not working)
and the problem exists since dual booting windows and linux
was invented ...

---

### Post by am7555 on 2009-09-17
Wow, thanks for the insight. I'm new to all this and even though the learning curve is fairly high, I'm enjoying it.

I'll test all these ideas and report tomorrow.

Cheers to all,

Javier

---

