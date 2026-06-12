---
title: "Can't log in to kubuntu 9.10"
date: 2010-01-16
forum: General Help
---

### Post by anonymous01 on 2010-01-16
Everytime I type my username and password and then press enter in the log in screen, kubuntu will always bring me back to the log in screen.

I google my problem but the result is the same


Any ideas???

---

### Post by anonymous01 on 2010-01-16
bump

---

### Post by supermelon928 on 2010-01-17
bump

---

### Post by Ederico on 2010-02-05
I just did an update, and voilà once again updating means getting more problems than ever before. Can anyone help? This topic was started two weeks ago, I'm having the same problem. No replies yet!

---

### Post by karasumori on 2010-03-04
I am suddenly having the same problem.  My computer was working fine last night, but when I turned it on this morning, I was unable to get pass the login screen.  When I type my password, the screen blacks out, then goes to the "loading" screen (the one with the box in the middle and the KDE icons appearing until the desktop is loaded), then returns to the login screen before anything happens.  When I type an incorrect password, however, the system recognizes that and does not let me past the login screen.  Any suggestions?  I can log in via the console, but there are somethings I need that are impossible without the windowing system being up.

---

### Post by Ederico on 2010-04-30
Fantastic, no replies to this yet. Me and karasumori have the same problem.

I had let it go before I could use another system and couldn't bother much about it.

Now though, things are just great. Here's the situation. I have karasumori's problem on two different system, and now I have another problem on my main system (my laptop).

At the moment of writing I'm using Windows, on both systems. That's because Linux screwed up on both. That's not something I like to say because I made the switch to Linux years ago and have been using Ubuntu/Kubuntu ever since. Now, after the latest attempted upgrade to Kubuntu 10.04 I'm stuck with Windows. Ok, I tried upgrading and I cannot even got to the login screen. I select Kubuntu from GRUB and I'm send to a command line screen, I give my username there and password and nothing. I type startx and something seems to work! So I was like, yay! No, it didn't work. Kubuntu starts loading normally but neither my mouse nor my keyboard work. At first I did get to my desktop, but now I can't even manage that. Some error with HPLIP is coming on screen. I tried recovery mode, reparing packages and everything. It starts downloading some 600MB worth of data, then I get an error message saying that it is impossible to write to file (I'm translating freely here, my system is in Italian), and something about unix-utils or something like that. So after around an hour downloading, I'm still stuck.

Frankly, I'm starting to regret this whole Linux/Ubuntu/Kubuntu move. Each update and upgrade is turning into a nightmare. I made the move because of greater stability, security and else. Well, what use it if I cannot even use a system? It is not like I wouldn't like to make an effort, I like the whole free and legal OSS thing rather than Microsoft's horrendous prices and monopoly. Yet, now I notice that this community isn't as responsive as it used to be.

In a few words, unless I solve the problem myself (and I am no tech guru), I guess an expense for Microsoft Windows 7 will have to be made, regretfully.

---

### Post by gregwa on 2010-04-30
It's not just Kubuntu 9.10, it's also Ubuntu 9.10.  Did the update, rebooted a bit later and I can't log into my system either.

---

### Post by cariboo on 2010-04-30
@Ederico

Have you tried:

```
apt-get -f install
```

The above command assumes you are using recovery mode.

On the system running Kubuntu what grahics card does the system have? Your problems sound like an Xorg problem, or graphics drivers. You may need to create an /etc/X11/xorg.conf

As far as the size of the updates go, I updated from Karmic to Beta 1, there were just over 1200 Mb of packages that needed to be downloaded. The size of the updates, depends on the state of your system, if you have installed a lot of extra packages, they need updating too.

---

### Post by wieman01 on 2010-05-01
I am writing from my wife's computer... I upgraded and have similar problems. No splash, KDE won't refuse to show the desktop, etc. 

cariboo907, I try to do what you have outlined.

---

### Post by wieman01 on 2010-05-01
I can only shake my head... sigh. Kubuntu forgot to install a package:

> sudo apt-get install kdebase-workspace
That done, create a new user through command line if you still have problems and log on to your system. It should resolve your problems.

---

### Post by Ederico on 2010-05-01
> **cariboo907 said:**
> @Ederico

Have you tried:

```
apt-get -f install
```

The above command assumes you are using recovery mode.

On the system running Kubuntu what grahics card does the system have? Your problems sound like an Xorg problem, or graphics drivers. You may need to create an /etc/X11/xorg.conf

As far as the size of the updates go, I updated from Karmic to Beta 1, there were just over 1200 Mb of packages that needed to be downloaded. The size of the updates, depends on the state of your system, if you have installed a lot of extra packages, they need updating too.

I tried the command in recovery mode. How do I know what graphic card do I have and how do I create that file? I can't access that right now though, as my laptop is connected to my external drive which I'm partitioning to attempt an install of Kubuntu 10.4. I was stupid on this one, my external drive is 1TB big and in like 12 hours the partitioning is only at 58%, and I'm not even doing drastic changes as I only affected one partition of from the whole drive. I hope I don't lose date from my external drive now, that is scary.

Now I can only use my desktop pc. I didn't try an upgrade from an unworkable 9.10 to 10.4, I opted for a fresh install (no important data on this one). I did the partition work and installed it. Everything should have been fine but now I'm stuck with the same problem on this one. If I remember correctly though, on my laptop it said there were some files to install or update, but I couldn't because I got the message a referred to above (impossible to write or something like that). On my desktop pc however, it seems like there is nothing to upgrade, install, remover et cetera.

I'm confused. :(

---

### Post by wieman01 on 2010-05-02
I decided to go for a fresh install... hopefully the last for the next 3 years.

You know, I also got very frustrated with the upgrade... Nothing worked as it should have. No splash, no desktop, freezing desktop environment once I got it working, etc. This was by far the most terrible upgrade I have ever had. I had bad ones, but this one was worse by any stretch of imagination.

I don't know why Ubuntu's quality assurance is so unreliable. I lost confidence in the whole upgrade process and will not go through it again anytime soon.

End of rant. :-)

---

### Post by Ederico on 2010-05-02
I went for a fresh install myself on my laptop (working fine) and my external drive (GRUB error 17 problem, need to fix that).

This one is better than the one before, but the time wasted will not be recovered unfortunately.

---

