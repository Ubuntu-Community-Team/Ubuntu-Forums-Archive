---
title: "Unexpected boinging"
date: 2010-07-19
forum: General Help
---

### Post by ibexslam on 2010-07-19
My Jackalope recently started making a "boing!" sound at apparently random intervals several times a day, even when I'm not using the computer. 

I know it's not exactly a huge problem, but it is a bit irritating. 

Any ideas on why it's doing this?

I.

---

### Post by WorMzy on 2010-07-19
Probably, but it's hard to give clear instructions with such little information to go on.

The first thing I'd do would check 'crontab -l' and the /etc/cron.[daily|hourly] directories, see if someone's playing a joke on you by having a script play the sound periodically.

If that yields no obvious culprits, then the sound must be coming from one of your running applications. Check the notification area for anything that would possibly need to alert you when a certain event happened, like a torrent downloaded completing a download for example. If you find something like that, poke around in the options and see if it has an option to play a sound enabled, and disable it if it does.

---

### Post by ibexslam on 2010-07-20
I checked crontab; nothing there.

The cron directories have various things in them, but cron.hourly is empty. I'd expect to see something there, if anywhere, as the boinging occurs hourly, roughly approximately thereabouts timewise. 

It's not possible at all for anyone on the premises to be playing a joke...no one here knows what a cron job is. 

The only applications I've been running lately have been Firefox (just about all the time) and Gimp (from time to time). Of course there are other processes running, including a gweather-applet-2, which must be the Weather Report panel application I've got.

I can't say I recall installing anything new lately; it's odd that I never heard the boinging before, as far as I can remember.

I suppose a web page could boing...does anyone know if BoingBoing boings? (One has to ask.)

I.

---

### Post by WorMzy on 2010-07-20
With a name like that, I'd say it's quite likely. It could be an embedded flash animation producing the sound, or a java applet, or even just an embedded sound file, occasionally called by javascript.

---

### Post by ibexslam on 2010-07-20
I've got the boingboing page open, and today there's no boinging. Not running Gimp today...I'm going to keep an eye, uh, ear on that. Stay tuned for the next installment of "Is My Gimp Boinging?"

I.

---

### Post by ibexslam on 2010-07-21
Odd. I haven't changed anything, but the boinging seems to have stopped. Must be a ghost in the machine.

Anyway, thanks, W.

I.

---

