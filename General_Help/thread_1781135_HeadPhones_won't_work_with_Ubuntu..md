---
title: "HeadPhones won't work with Ubuntu."
date: 2011-06-13
forum: General Help
---

### Post by wethegreenpeople on 2011-06-13
Hey guys, so I've been waiting a long time to dual boot my Mac OS X with Linux and I finally did it. I'm loving it so far, except for the fact that my headphones won't work. I can plug them in, but the sound will continue to come out of the built in speakers. I've tried messing around with sound preferences but being the n00b that I am, I haven't been able to figure out what I'm doing wrong :P

So if any one could help me out here that'd be greatly appreciated. :D

---

### Post by grahammechanical on 2011-06-13
It is a silly question I know, but in Mac OS X did the sound stop coming out of the built-in speakers when you plugged in the headphones? In my experience this is not an OS function at all. The headphone plug is designed so that when pushed fully in it breaks the circuit to the built-in speakers.

I have the sound output from my computer plugged into the sound input of my TV/monitor. I then take the output from the headphone socket into an amplifier with two external speakers. I like to have the sound coming out of both the external speakers and the built-in speakers. If I push the plug too far into the headphone socket the the sound coming out of the built in speakers cuts off. I have to balance the plug so that I get sound out of the built-in speakers and out of the headphone socket.

It is this experience of mine that suggests to me that the problem lies with the design of the headphone plug or socket.

Regards.

---

### Post by wethegreenpeople on 2011-06-13
Lol yeah. When you plug in the headphones it cuts off the sound from the built in speakers. It does this on EVERY mac I own. I don't understand why that isn't default? It's supposed to do that...

And what you told me doesn't really help lol. You told me how to get the sound to come out of both the built in speakers and the output which I don't want. I want to be able to plug in my headphones and listen to the music from my headphones *alone*

---

### Post by toddha on 2011-06-13
at the top left of ur screen got to the little speaker icon. then hit "sound prefrences" after that select the hardware to the one you want the sound to come out of. if you want it to come out of more than one, hold down left controle and select more than one, or use the selection box.

---

### Post by wethegreenpeople on 2011-06-13
There is only one option. The main speakers. Nothing for headphones.

---

### Post by pqwoerituytrueiwoq on 2011-06-13
just to make sure were you on the right tab/device?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194995&stc=1&d=1307975016[/IMG]

---

### Post by wethegreenpeople on 2011-06-13
Yea, see I don't have the "Connector" option :(

[IMG]http://i.imgur.com/CEp2R.png[/IMG]

---

### Post by wethegreenpeople on 2011-06-13
Wow, threads get moved down really fast on this site huh?

Well this is a bump :P

---

### Post by wethegreenpeople on 2011-06-13
I've been trying to google a fix to this problem all day and haven't been able to find a fix.

D:

---

### Post by wethegreenpeople on 2011-06-14
No help with this guys?

---

### Post by pqwoerituytrueiwoq on 2011-06-14
out of courtesy have you tried using the lts 10.04 it is worth a try i guess
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by Yellow Pasque on 2011-06-14
> **grahammechanical said:**
> In my experience this is not an OS function at all. The headphone plug is designed so that when pushed fully in it breaks the circuit to the built-in speakers.

Plugging in the headphones doesn't physically break any connections. It's called 'jack sensing' and the driver needs to handle it correctly. It's not uncommon for it to not work on Linux. Fortunately, it can often be fixed by specifying the model in /etc/modprobe.d/alsa-base.conf

@OP: what kind of Mac do you have? Even better, run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by wethegreenpeople on 2011-06-15
> **pqwoerituytrueiwoq said:**
> out of courtesy have you tried using the lts 10.04 it is worth a try i guess
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

I did that :P I went from 11.04 to 10.10. Still doesn't work.

> **Temüjin said:**
> 
@OP: what kind of Mac do you have? Even better, run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

It's a Mac OSX. And I can't run that script, if I try to, it says send the report back to alsa? And if I say "y" it crashes if I say "n" it crashes...

---

### Post by Yellow Pasque on 2011-06-15
OSX is the operating system. I meant like iMac or MacBook Pro, for example. Sorry about the alsa-info script failing (it's always worked fine in the past). Anyway, I just wanted to know what codec you had, so try this instead:
```
cat /proc/asound/card0/codec#0 | grep Codec
```

---

### Post by wethegreenpeople on 2011-06-15
Haha my bad I forgot we were talking about hardware here xD yea it's an iMac. Shows you how n00by I can be at times. :P

Running that in terminal I get:
> Codec: Realtek ALC889A

---

### Post by Yellow Pasque on 2011-06-15
There are two possible models for that codec:
```
ALC882/883/885/888/889
=========================
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
```

Try this and restart:
```
echo "options snd-hda-intel model=imac24" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
If that doesn't work after restart, edit the alsa-base.conf file, change 'imac24' to 'imac91', save and restart:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
If that doesn't work, I'm out of ideas..

---

### Post by wethegreenpeople on 2011-06-15
Okay, when I set it to imac91 it changes, it gives me a "Connector" option in sound preferences but, when I pick the Analog Out option it mutes both the built in speakers as well as the headphones. So I don't get sound from either...

---

### Post by wethegreenpeople on 2011-06-16
Any help peepz? I need to get back to watching por-

I mean... youtube videos.... >,>

---

### Post by wethegreenpeople on 2011-06-17
Alright, well... I'm going to bump this one more time and until some one can help me fix this problem Imma be using OS X.

---

### Post by wethegreenpeople on 2011-06-20
Bump.

---

