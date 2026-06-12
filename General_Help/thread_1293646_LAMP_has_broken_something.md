---
title: "LAMP has broken something?"
date: 2009-10-17
forum: General Help
---

### Post by HomoGleek on 2009-10-17
Hi

I tried installing LAMP last night, but my net-book battery died while I went too make a drink, now when I start ubuntu, after the load screen I get the terminal, no login screen etc, and I had too use a Mint LiveCD too do anything, any help would be appreciated

---

### Post by HomoGleek on 2009-10-18
I don't like too bump but just incase someone has an idea that hasn't seen this yet :)

---

### Post by Peter09 on 2009-10-18
in a terminal do the following command

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by HomoGleek on 2009-10-18
> **Peter09 said:**
> in a terminal do the following command

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get update
```

```
sudo apt-get upgrade
```
Hi, thanks but no luck, I cant get online in terminal

This is the error that appears if its any help

```

kinit: no resume image, doing normal boot

```

---

### Post by Peter09 on 2009-10-18
Thats not an error, its just indicating that the machine is not coming back from hibernation or resume.

The first command does not need you to be online, it  just reconfigures your package manager. Can you not get to a terminal, try recovery mode.

---

### Post by HomoGleek on 2009-10-18
Ive tried recovery mode, no luck with that either, hmm maybe a install of Mint until Karmic release.

Is there anyway I can move my installs of Opera etc from Ubuntu over too Mint using backups?

---

### Post by Peter09 on 2009-10-18
What is happening in recovery mode? Have you tried - Repair Broken Packages - from the menu in recovery mode.

---

### Post by HomoGleek on 2009-10-18
> **Peter09 said:**
> What is happening in recovery mode? Have you tried - Repair Broken Packages - from the menu in recovery mode.
It tries too access something.ubuntu.com.

At the bottom it says 0 upgrade, 0 new installs etc etc

---

### Post by Peter09 on 2009-10-18
Try typing startx at the terminal prompt. Also the reconfigure your screen option in recovery mode - sorry of hand to not know whet the menu option is called.

---

### Post by HomoGleek on 2009-10-18
Thanks, startx works. Not the ideal soloution though, is there anyway I can fix this too happen all the time?

I seem too have some errors now, I have no sound anymore, something about GStreamer being missing.

I cant mount the windows partition anymore either.

(Im using Jaunty)

---

### Post by Peter09 on 2009-10-18
You have some packages missing - see if going through update manager and doing an update will rebuild those missing packages.

---

### Post by HomoGleek on 2009-10-18
Done that, 256MB of updates, would take me around 18 hours on mobile GPRS :/

---

### Post by Peter09 on 2009-10-18
Think your going to need to get somewhere to download them.

---

### Post by HomoGleek on 2009-10-18
Ahh, fresh install is more appealing atm, what should I be backing up?

---

