---
title: "System clock stuck in UTC"
date: 2006-02-23
forum: General Help
---

### Post by FlakJacket on 2006-02-23
Somehow (maybe during install) i set my system clock to set to UTC. I don't live in London so now all of my time logs and clocks other than the kicker clock are 5 hours ahead.  I can't find anywhere to change what my system clock is set to.

Thanks for any help,

Flak

---

### Post by skaboss on 2006-02-23
hello,

You can try this :
```

sudo ntpdate europe.pool.ntp.org

```
Replace europe.pool.ntp.org with another server (you can find a list [here]("http://ntp.isc.org/bin/view/Servers/NTPPoolServers")), depending on where you live.

---

### Post by FlakJacket on 2006-02-23
I discovered that my time zone is NewYork (UTC) but i can't get (EST) to stick. Anyway to manually change timezone?

Flak

---

### Post by FlakJacket on 2006-02-24
Anybody have an idea?

Flak

---

### Post by tmahmood on 2006-02-24
```
tzsetup
```

this might help.. :)

---

### Post by FlakJacket on 2006-02-24
Thanks that finally did it.  This has really frustrated me.  Thanks alot!

Flak

---

### Post by msak007 on 2006-02-26
This one frustrated me for a long time as well until someone suggested "tzsetup". I was stuck in UTC, and found it ridiculous that there was no option in the clock configuration to just choose a "generic" time zone (EST, CST, etc.), and it had to be bound to a city / location. Or at least the option to set the GMT offset manually. If that option is there, then I missed it.

---

### Post by FlakJacket on 2006-02-26
Yeah it would tell me in the GUI config it would tell me NewYork(EST)
 but it would change back after I closed it and reopened it.  The time never changed.

Flak

---

### Post by Chemicalvamp on 2006-02-26
i agree figuring out how to get my clock to stay at the correct time was a pain.

---

### Post by Red Knuckles on 2006-04-09
I tried all of the above and nothing worked. In Date & Time - System Settings the box for 'current time zone' ALWAYS goes back to UTC no matter what I select in the 'to change the time zone, select your area from the list below' box.    Any ideas?

---

### Post by incubus on 2006-04-09
What about editing:
/etc/default/rcS

and switching UTC's flag?

incubus

---

### Post by Apostata on 2006-11-20
I don't understand why, but apparently 'tzsetup' isn't available on my system (Edgy Kubuntu). This is a really annoying situation: I can set my local timezone fine, but all of my email/correspondence is being time-marked +5 hours ahead. What package is 'tzsetup' part of?

Cheers.

---

### Post by santo on 2006-11-28
In Edgy it is called tzselect instead of tzsetup.

As Incubus suggested, you might want to take a look at /etc/default/rcS also.
Change
```

UTC=yes

```
to
```

UTC=no

```

---

### Post by Red Knuckles on 2006-12-01
> **santo said:**
> In Edgy it is called tzselect instead of tzsetup.

As Incubus suggested, you might want to take a look at /etc/default/rcS also.
Change
```

UTC=yes

```
to
```

UTC=no

```

I did this and ran 'sudo tzselect' [in Edgy] and all seems ok. Thanks.:)

---

### Post by kairu0 on 2006-12-17
I was looking everywhere for this.

This is a bug that I would definitely like to see fixed in Feisty. Assuming that everyone's clock is set UTC seems kind of ridiculous to me.

---

### Post by louieb on 2006-12-18
> **santo said:**
> In Edgy it is called tzselect instead of tzsetup.
Same thing in Dapper: tzselect instead of tzsetup

---

### Post by Trapper on 2007-02-08
Something is really screwed up. I am set up to run EST. No UTC. My clock is 5 hours off.

I checked /etc/default/rcS  It has UTC=no

I ran tzselect. At the end it came up with this:

Local time is now:      Thu Feb  8 19:17:57 EST 2007.
Universal Time is now:  Fri Feb  9 00:17:57 UTC 2007.

How wrong ----- 19:17:57 is actually what the UTC is right now!!! The local time is 14:17:57
It's still a looooong time to Friday!!!

I have FC6 and Win2K on the same box. When I boot into them they both correct the system time to what it should be As soon as I switch back to Ubuntu I end up with UTC time. Uh .... all my settings are correct and the same as in FC6.

Whatever, at the current rate, I am going to have to select a timezone that's actually incorrect for me to end up with the correct local time. That shouldn't have to be happening. I finally select Tahiti out in the Pacfic Ocean. I actually live in Florida, USA on the Atlantic Ocean ..... but my time is now correct. at least.

It seems that Ubuntu may be having a -5 vs. +5 problem.

---

### Post by Apostata on 2007-02-08
At least I don't feel alone anymore :)

I've honestly followed every sane recommendation to this problem and I still get UTC (ie email dated five hours ahead of EST). Not to flame (K)Ubuntu, but why - given this day and age - should this even be an issue?

Mind you, I suppose I could pretend I was a time traveller, then it wouldn't be so bad.

---

### Post by viejogringoso on 2007-03-12
Had the same problem on dapper.
Turned out the symbolic link  /etc/localtime  was missing.
Did the following from console:

sudo  ln  -s  -f  /usr/share/zoneinfo/America/New_York  /etc/localtime

All better now.

Note that the  -f  forces an overwrite in case /etc/localtime does exist.
Also note that the command is case sensitive.

Of course you will have to replace  /America/New_York
by selecting your time zone from those provided in  /usr/share/zoneinfo/.

Adios

---

### Post by Apostata on 2007-03-17
> **viejogringoso said:**
> Had the same problem on dapper.
Turned out the symbolic link  /etc/localtime  was missing.
Did the following from console:

sudo  ln  -s  -f  /usr/share/zoneinfo/America/New_York  /etc/localtime

All better now.

Note that the  -f  forces an overwrite in case /etc/localtime does exist.
Also note that the command is case sensitive.

Of course you will have to replace  /America/New_York
by selecting your time zone from those provided in  /usr/share/zoneinfo/.

Adios

I soooo wanted this to work, but unfortunately it didn't do the trick for me. Tried replacing the symbolic link as you noted, but no difference. Still +5 hours ahead on my system.

---

### Post by buckbugs on 2008-06-12
hmmmm... i check /etc/default/rcS and change to UTS=no but the UTC still appearing instead of my local time. Any other trick or setting to make my local time appearing?

im using hardy anyway.

---

