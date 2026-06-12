---
title: "no internet connection"
date: 2010-12-15
forum: General Help
---

### Post by manji_kun on 2010-12-15
So i finally got my desktop tore down, i brought it to my internet source to run updates, considering i was almost a year out of date, i knew i had a while before i was done.

after i ran all my updates, my machine prompted me to reboot, so i did, after i was back into the Operating System, i wasn't connecting to the internet, i had the connection saved, and now i can't find the "view wireless networks"

will someone help me with this?

---

### Post by Habitual on 2010-12-15
sudo apt-get install -y wifi-radar

---

### Post by manji_kun on 2010-12-15
> ""unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"
"apt-get update"
> 
"could not open lock file /var/lib/apt/lists/lock - open (13: Permission Denied)right now i have no connection, or at least, im not connected to it.

---

### Post by cracker89 on 2010-12-15
I'm no expert, but what does iwlist scan give you? As in can you access networking, or is it just an issue with the radar?

---

### Post by manji_kun on 2010-12-15
it says

> wlan0 No scan results

---

### Post by cracker89 on 2010-12-15
> **manji_kun said:**
> it says

hmm.. thats a way to list the wireless connections that your card can detect. Are you in range of any? Because if that is so, this is more than just a problem with the radar app..

---

### Post by manji_kun on 2010-12-15
im deffinitely in range, im on a laptop right next to my desk top, and it's picking up the signal at "excellent" strength

---

### Post by flyingbear on 2010-12-15
Why don't you try to downgrade the drivers for your wireless device?

---

### Post by manji_kun on 2010-12-15
how do i do that? they make upgrading simple enough, lol

---

### Post by cracker89 on 2010-12-15
wait a bit... i dont think i've understood ur problem completely. What is really wrong here? Post your update, ur internet has stopped working, due to wireless networking being disabled and you cannot see the icon on the bar on the top ^^^ over there? is that it?

---

### Post by manji_kun on 2010-12-15
yeah, thats pretty much it, theres no wireless connection at all, im not sure whats going on with it, maybe the updates deleted something?

---

