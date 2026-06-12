---
title: "Ubuntu randomly crashing :("
date: 2010-04-03
forum: General Help
---

### Post by aCsbD6N5xj on 2010-04-03
Hi.

I installed ubuntu 9.10 4 days ago via unetbootin and so far everything's fine except for the random crashes. My CPU reaches 100% randomly and ubuntu just freezes and logs me out automatically. At least there's no manual reboot involved and it's quick to log back in. But it's getting more frequent and annoying. But right now i'm not really working on important stuff so i could say it's still 'ok'. Even in crash handling, ubuntu owns windows xp lol

Right now in sys monitor, gnome-system-monitor is using the most CPU, on par with firefox-bin when i'm using it. For memory usage, ffx is the highest not suprisingly. And amsn and its 'wish' process join in when i open amsn.

But even when i do mundane tasks like playing sudoku, or just opening any software, i can see from the sys monitor 'graph' on the top panel that something is using much CPU. By the time i open SM,if i can, the CPU usage decreased. And when it freezes, well i'm logged out. 

At one point, I didn't have LAME for audacity so i clicked on Download, expecting ffx to open the website. On both times i tried that, it froze. Fortunately session manager saved the link. At another point, I just right clicked on my top panel for the sake of it and bam my pc froze again!!! WTF...

A few minutes ago, the last time my pc froze, i noticed a few red/violet lines on the top right of my screen. The kind of lines when, well, a pc freezes. Hope i'm clear enough.

And last, a few things about my current pc:

- Effin Toshiba Satellite sumthin
- Intel core duo w/ 512 MB RAM
- ATI Graphics card
- Basically too weak for both windows vista and windows 7 home premium edition (I ran both tests when I still had Windows)

+ How do I get my pc specs in linux???

Thx

---

### Post by aCsbD6N5xj on 2010-04-03
BUMP... really need help plz :(

---

### Post by C.S.Cameron on 2010-04-03
How did you install it using UNetbootin?
To C drive from windows or to flash drive?

---

### Post by aCsbD6N5xj on 2010-04-03
> **C.S.Cameron said:**
> How did you install it using UNetbootin?
To C drive from windows or to flash drive?

So the ubuntu iso was downloaded via utorrent. Concerning unetbootin, i think it was a single executable file. But i ran it from the C Drive. Then it just put ubuntu on my flash drive. All this was done in windows xp sp3.

Then i booted ubuntu off the flash drive as a 'Live CD' and clicked on the 'install' icon on the desktop. The install process took ~7 mins to finish.

---

### Post by aCsbD6N5xj on 2010-04-04
BUMP... again :(

---

### Post by shebaw on 2010-04-04
Have you downloaded the latest updates? And btw, what are you using to connect to the internet, is it a wifi card or a cable modem? I had issues with my ATi graphics card driver and the wifi driver, it randomly froze when I surfed the net through wifi connections.

---

### Post by aCsbD6N5xj on 2010-04-04
> **shebaw said:**
> Have you downloaded the latest updates? And btw, what are you using to connect to the internet, is it a wifi card or a cable modem? I had issues with my ATi graphics card driver and the wifi driver, it randomly froze when I surfed the net through wifi connections.

Yes i downloaded the ~220mb updates 1 day after the install. Last year, when i moved to my current home, the connection would just be lost by itself after a few months. And then it would just try to reconnect automatically. That considerably slowed down my computer. All of this was in windows XP. I had no idea if it was my network card (or basically my pc) getting too old, the home connection or both.

Now in ubuntu that connection problem still persists but does not slow down my pc at all. But i suspect sometimes when i do lose connection, it makes my CPU go berserk. Coz even in linux, connection loss is still as frequent as in xp. I have an intel ABG 3945 network card, wirelessly connected to a router/firewall. 

But the crashes themselves occur really randomly.

---

### Post by neur0 on 2010-04-04
It sounds like it's video card related.
Do you have those fancy effects enabled ?
Did you install ATI drivers ?
What does the command
```
lshw -C video
```
give you ?

---

### Post by aCsbD6N5xj on 2010-04-04
> **neur0 said:**
> It sounds like it's video card related.
Do you have those fancy effects enabled ?
Did you install ATI drivers ?
What does the command
```
lshw -C video
```give you ?


It gives me info about my graphics card:

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: M56P [Radeon Mobility X1600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff(prefetchable) ioport:2000(size=256) memory:dc000000-dc00ffff memory:dc020000-dc03ffff(prefetchable)

And yes i have compiz enabled. Though when i just fool around with it, it does nothing like freezing or lagging.

---

### Post by aCsbD6N5xj on 2010-04-04
BUMP... I apologize for doing this so much :(

---

### Post by sandyd on 2010-04-04
> **BucketBob said:**
> It gives me info about my graphics card:

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: M56P [Radeon Mobility X1600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff(prefetchable) ioport:2000(size=256) memory:dc000000-dc00ffff memory:dc020000-dc03ffff(prefetchable)

And yes i have compiz enabled. Though when i just fool around with it, it does nothing like freezing or lagging.

try installing the ati open source drivers.

---

### Post by aCsbD6N5xj on 2010-04-04
> **carlee said:**
> try installing the ati open source drivers.

Noob question: where do i get them and how do i install them?

I googled 'ATI open source drivers' and got this link

[HTML]https://help.ubuntu.com/community/RadeonDriver[/HTML]I also entered this code in the terminal, as said in the above link:

```
 lspci -nn | grep VGA 
```I got this output:

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]
```The rest of the link is like greek to me :(

---

### Post by shebaw on 2010-04-05
Does the freezing occur when you are not connected to the wireless network?

---

### Post by aCsbD6N5xj on 2010-04-05
> **shebaw said:**
> Does the freezing occur when you are not connected to the wireless network?

Yes :(

---

### Post by kg4cna on 2010-04-05
Have you tried it with Compiz turned off?

---

### Post by aCsbD6N5xj on 2010-04-05
> **kg4cna said:**
> Have you tried it with Compiz turned off?

No. How do i turn it off w/o uninstalling it?

---

### Post by aCsbD6N5xj on 2010-04-06
Bump

---

### Post by C.S.Cameron on 2010-04-06
Try System/Preferences/Appearance/Visual Effects - None

---

### Post by aCsbD6N5xj on 2010-04-07
> **C.S.Cameron said:**
> Try System/Preferences/Appearance/Visual Effects - None

seems like it was compiz after all. i'm using 'heavy' apps right now w/o any problems. any ideas why the crashes were happening in the first place?

---

### Post by aCsbD6N5xj on 2010-04-07
Actually it still hangs up sometimes for e.g. when transfering files between my local HD and my external HD (encrypted) or installing stuff from Ubuntu Soft. Centre.

But it does not actually crash. It goes back to normal after like ~2 secs.

---

