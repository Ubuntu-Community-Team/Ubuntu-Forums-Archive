---
title: "How to save the most battery life possbile with uBuntu?"
date: 2011-05-06
forum: General Help
---

### Post by Suitsuke on 2011-05-06
Hey guys! Greetings from Finland!

Just wanting to know all the possible steps needed to drastically reduce the amount of battery power that ubuntu uses. Ubuntu seems to completely eat my battery. I've had massive, massive issues in the past with ubuntu ripping through my brand new laptops battery, completely killing it. However after making a thread about how much batter ubuntu eats a few months ago.. if not years, members here told me that they can get their battery to squeeze out 5 hours if they set all their settings correctly..

Obviously I've been left majorly out of the loop. My laptop barely ever comes off the AC power but when it does I need hours of time. Ubuntu has been proven on many websites to reduce battery usage to double less than that of what windows needs.

So I decided to come to the source of the OS itself and the experienced pro's that run the show.

Please share your secrets and knowledge and tell me how to minimize as much as possible the amount of power that ubuntu will use :)

Thanks again!
Moikka

---

### Post by stoneheart on 2011-05-06
I don't have a direct answer to your question, but have you looked at WattOS?  It's a distro based on Ubuntu that has specific utilities included meant to reduce your energy footprint.

---

### Post by JRV on 2011-05-06
Install powertop, let the machine idle and see how often it wakes up and what programs are waking it.
```
sudo apt-get install powertop
```
to run program:
```
sudo powertop
```

---

### Post by Suitsuke on 2011-05-06
Thanks. It gave me lots of information and I've made all the possible amends that I know how to. I have to get into compiling my own kernels so I can change the rest of the things I need to. Seems good now though. Reduced from 5,000 down to 50 :D!

---

### Post by unagimiyagi on 2011-05-12
> **JRV said:**
> Install powertop, let the machine idle and see how often it wakes up and what programs are waking it.
```
sudo apt-get install powertop
```to run program:
```
sudo powertop
```


Hi,

I've run powertop.  I see the suggestions to W, U, P, etc and whether they are helping my battery life, I'm not sure.  However, the settings aren't sticking.  How do you make the powertop settings stick?

---

