---
title: "Could not read from resource &gt; Could not launch application (INPUT|OUTPUT ERROR)"
date: 2011-08-24
forum: General Help
---

### Post by Natalio on 2011-08-24
Hello everyone,

My girlfriend's laptop is currently running Ubuntu 11.04, and today it started giving some weird error on Clementine doing mp3 playback. Then I tried to play mp3s on the Movie Player and did the same thing. The error I'm getting is:

Clementine error:

Could not read from resource. Librarybackend: unable to open database file. Unable to fetch row.

And after that, whenever I try to do ANYTHING (and I mean anything, open any app or something) I get:

Could not launch application: Failed to execute child process "Firefox" **[or any other, for that matter]** (Input|Output error).

And then if I go to any music folder, they're empty.

Any help is great help and very appreciated. I should also note that the laptop has had some problems with the hard drive, but last night it was playing music just fine, then when we woke up, this problem started happening.

Thanks in advance :P

Matías

---

### Post by Ghost|BTFH on 2011-08-24
Take some steps to verify where the issue is coming from.

Slap some MP3s onto a flash drive.  Attempt to play them.

IF they play, THEN hardware issue - laptop hard drive is dying.

IF they don't play, THEN software issue - check for bugs.

Cheers,
Ghost|BTFH

---

### Post by Natalio on 2011-08-24
> **Ghost|BTFH said:**
> Take some steps to verify where the issue is coming from.

Slap some MP3s onto a flash drive.  Attempt to play them.

IF they play, THEN hardware issue - laptop hard drive is dying.

IF they don't play, THEN software issue - check for bugs.

Cheers,
Ghost|BTFH

Haven't thought of that. Thanks, I'll try now!

---

### Post by Natalio on 2011-08-24
Ok, so here's what happened:

I started playing the mp3s from a cheap mp3 player I have. Everything seemed to be working just fine until the same thing happened again, Chrome and Firefox crashed, but music playback continued. I tried to get to my Downloads folder, but it was a no-go.

When I tried to shut down, obviously I couldn't. Eventually, when I could, I got the following message in a black screen:

[3545.639326] end_request; I/O error, dev sda sector 35853664

I had to manually shut down pressing the power button.

Any thoughts? Thanks!

---

### Post by Ghost|BTFH on 2011-08-24
Hard drive is dying.

---

