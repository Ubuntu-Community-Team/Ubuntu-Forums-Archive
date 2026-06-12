---
title: "netbook drive filling up"
date: 2010-01-14
forum: General Help
---

### Post by rogue1987 on 2010-01-14
eeePC 900a, Remix 9.10 installed, 4gb drive, 1gb memory

i'm still fairly new to Ubuntu (and Linux for that matter) and am not sure what to check for this. But here's the scoop:

Installed 9.10 last night (over 9.04), the install size was 1.9 gb. I uninstalled a handful of things I didn't need, not much (no bluetooth on this eee). Right now, nearly 24 hours later, the drive is up to 2,4 gb. I'm quickly losing free space - had the same issue with 9.04 remix, which took me own to only about 300mb free space when I installed 9.10.

The only thing I've put on here is Adobe Air/Tweetdeck. I have an extra 4GB SD card that I keep all my files on. I turned the settings on Firefox way down so it doesn't store too much tmp files.

So what is filling up the drive?

---

### Post by garryknight on 2010-01-14
It could be .deb files clogging up /var/cache/apt. You can remove them with 'apt-get clean' and make sure they never reappear by selecting "Delete downloaded packages after installation" in Synaptic's Settings, Preferences, Files section. There's probably a way of doing the latter from the command line but I haven't found it yet.

---

### Post by running_rabbit07 on 2010-01-14
Try ```
sudo apt-get autoclean
``` & ```
sudo apt-get autoremove
``` to clear up some space.

---

### Post by rogue1987 on 2010-01-14
yeah, i know about that and have do that regularly as needed. i'll make sure i click the button.

thanks for the reply

---

### Post by rogue1987 on 2010-01-14
ran all 3 commands and cleared out 200mb roughly. i'll keep watching over the next few days and see what happens.

thanks again guys

---

### Post by running_rabbit07 on 2010-01-14
I don't know what all is installed on UNR, but with my desktop, the system partition is filled past 5 gigs.

---

