---
title: "turn on my laptop at a specific time? kind of like an alarm clock..possible?"
date: 2011-09-01
forum: General Help
---

### Post by Mauroblack on 2011-09-01
So I have ubuntu 11.04 on my Asus netbook,

I am just wondering, is there an app that will turn on my computer at a specific time?

Kind of like...to wake up and have my computer on and ready to use. Like in sci-fi movies.

There has to be a way using BIOS time or whatever...ideas?

---

### Post by aura7 on 2011-09-01
The opposite is definitely possible using shutdown command in linux terminal but I am not sure of what you are asking being possible with any operating system.

---

### Post by blind2314 on 2011-09-01
> **Mauroblack said:**
> So I have ubuntu 11.04 on my Asus netbook,

I am just wondering, is there an app that will turn on my computer at a specific time?

Kind of like...to wake up and have my computer on and ready to use. Like in sci-fi movies.

There has to be a way using BIOS time or whatever...ideas?


Definitely possible. 

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)

---

### Post by sanderd17 on 2011-09-01
If it can be done, it has to be a BIOS feature. So that would be different for each computer (but I have never seen a BIOS with that feature).

Maybe it's possible to wake up at a certain time from hibernation.

---

### Post by Johnb0y on 2011-09-01
check in your BIOs, there should be something in there for you to use. if not then possible google for software to act the same...

---

### Post by elliotn on 2011-09-01
wow I would like that too. like setting the PC to turn at specific time. wow

---

### Post by Mauroblack on 2011-09-01
> **Johnb0y said:**
> check in your BIOs, there should be something in there for you to use. if not then possible google for software to act the same...

Yea some laptops have it...mine doesnt.

---

### Post by elliotn on 2011-09-01
> **Mauroblack said:**
> Yea some laptops have it...mine doesnt.

I wonder if my mobo has it

---

### Post by drmrgd on 2011-09-01
Not sure if this is close to what you're looking for, but you could try something like nvram-wakeup:

[http://manpages.ubuntu.com/manpages/hardy/man8/nvram-wakeup.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/nvram-wakeup.8.html")

The only difference is that you have to be in soft shutdown state (sleep or hibernation I think) in order for this to work. A while back I was thinking to try the same thing to have my computer wake up, run a cron backup job, and then go back to sleep while I was asleep.  I got busy and never finished it, though.  

Oh yeah, just remembered another tool I was thinking of trying, rtcwake, which works in the inverse way:

[http://linux.die.net/man/8/rtcwake]("http://manpages.ubuntu.com/manpages/hardy/man8/nvram-wakeup.8.html")

---

### Post by sunfromhere on 2011-09-01
Hmm, would it be possible to pair this idea with f.e. a music player?

Once upon a time (2001, WinXP) i used TaskScheduler in which I added Winamp to wake up computer at 6am and start playing my selected playlist.

Naturally, a) the computer wasn't shut down, only in sleep; b) I didn't get up on time because I enjoy sleeping with music :) Nevertheless, would something like this be possible? Wake up from hybernation at set time + start the playlist?

---

### Post by CrusaderAD on 2011-09-01
> **sanderd17 said:**
> If it can be done, it has to be a BIOS feature. So that would be different for each computer (but I have never seen a BIOS with that feature).

Maybe it's possible to wake up at a certain time from hibernation.

BIOs is where it's at! I do this all the time.

---

### Post by jim_deadlock on 2011-09-01
+1

I use a 10 year old Dell to run automatic weekly backups this way. Auto powerup is a normal BIOS feature, you should find it in there somewhere.

---

### Post by Johnb0y on 2011-09-02
> **CerealCypher said:**
> BIOs is where it's at! I do this all the time.

defo! this is how i "use to" have it set up! maybe need a BIOS update...?

---

