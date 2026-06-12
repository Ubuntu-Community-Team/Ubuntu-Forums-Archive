---
title: "Latest Oneric 10.10 (with latest updates) crashes on startup"
date: 2011-10-24
forum: General Help
---

### Post by hanzen on 2011-10-24
Hi,

after installing all the resent updates I restarted my laptop.

After showing the standard startup-screen for some seconds the startup-process stops and shows the terminal with the last startups (foo... - [OK]) Ubuntu did.
It stops kinda randomly at starting MySQL.

When I switch to another Terminal-Window (Strg+Alt+F1) and enter "startx" Unity3D starts. Apache and MySQL are working fine, so the problem doesn't seem to be MySQL.

I installed all recent updates but it didn't fix the problem. It still crashes on startup.

Can anyone help or tell me how I start Unity2D via 'startx'?
What kind of information/logs should I provide and how?

Thx, Hannes

---

### Post by hanzen on 2011-10-24
I guess I provided too less info.

After a restart i got:

The last start-up messages I get are these:
```

* stopping kernel messages
* starting VirtualBox kernel modules
* starting Bluetooth
* PulseAudio configured for per-user sessions
       saned disabled; edit /etc/default/saned
            * stopping anac(h)ronistic cron
* starting anac(h)ronistic cron
* stopping anac(h)ronistic cron

```


I found some threads which suggested to remove anac(h)ronistic.
I did that.


Then I got:

```

* stopping kernel messages
* Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment out)
* speech-dispatcher disabled; edit /etc/default/speech-dispatcher
...

```


I edited the jetty startup, just to give it a try (I obiously don't not what I'm doing) and got:

```

* stopping kernel messages
grep: character class syntax is [[:space:]], not [:space:]
...

```


I tried to get a boot log but it always say
```

cat /var/log/boot
(Nothing has been logged yet.)

```


Seems like this problem is not as obvious as I was hoping. So it might be easier just to re-install Oneric.

Could it be better to move my post to the install & update section?

---

### Post by Jaybyrrd on 2011-10-24
Just curious as I think it would help to clarify for someone more experienced. Did you upgrade your distribution or do a clean install?

---

### Post by hanzen on 2011-10-24
Ah, thx, good point.

I did a dist-upgrade. After that everything was fine. But since I installed the latest updates I have this problem.

---

### Post by Jaybyrrd on 2011-10-24
Ok I want to let you know that at least for me and my experience with doing a dist-upgrade that there are often problems like this that arise because through use changes are made within Ubuntu, and when you do an upgrade, there is no way for designers to account for every possible change so there will be errors and bugs as a result. I do not know how to solve your issue, hopefully someone else does, but I recommend doing a clean install anyways just because you can't go wrong starting out exactly as the developers intended you to. (I had issues with my dist-upgrade and a clean install has fixed everything so this is my new found position on all things dist-upgrading) Maybe someone else has a better answer. I hope so. :)

---

### Post by hanzen on 2011-10-24
Hey Jay,

thx for sharing your experience. I guess you're right.
Then I might go for a fresh install on the weekend.

---

