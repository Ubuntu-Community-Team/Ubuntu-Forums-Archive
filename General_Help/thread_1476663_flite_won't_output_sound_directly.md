---
title: "flite won't output sound directly"
date: 2010-05-08
forum: General Help
---

### Post by Manaan on 2010-05-08
Hello, I am posting this thread in the General Help section because I didn't want to put it in Absolute Beginner Talk; even though I am a beginner, I don't think this question is that simple to solve.

Anyway, here's what's wrong: flite (festival lite) won't produce sound directly. When I run
```
flite -t test
```
no sound is produced. But when I run
```
flite -t test -o test.wav;cvlc test.wav
```
it works perfectly. This wouldn't be a problem if I just wanted to use flite by itself, but I want to use kismet with it.

I tried searching for a flite configuration file with
```
sudo du / -a | grep -i flite.conf
```
but the flite.conf file I found doesn't have any useful settings in it.

So, how do I fix this?

---

### Post by Scarlet_Chantel on 2010-05-08
me too :(

---

### Post by Manaan on 2010-05-12
Got an update for you people. I just installed FluxBox and kismet's text to speech through flite works perfectly. But here's the weird part: flite -t "test" still doesn't work and kismet still doesn't play any sound in Gnome.

---

### Post by Manaan on 2010-05-16
Bump. Now new info this time except some piano applications in the Ubuntu Repository don't output sound either. I'm thinking this isn't just a flite problem, but I don't want to change the thread title in case I'm wrong.

---

### Post by Manaan on 2010-05-18
Okay, this is going to be my last bump before I abandon this thread. Sorry nonexistent people.

---

### Post by mecrider on 2010-07-30
I haven't found a solution to getting flite working in lucid, but I did discover there is a similar program called spd-say that is included in a default install and works great. It actually has more options (voices etc.) than the default flite package has. I have switched to it for turn-by-turn directions from navit.

---

