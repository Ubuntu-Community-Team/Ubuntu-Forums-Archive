---
title: "Ubuntu crashes when downloading torrents"
date: 2011-02-28
forum: General Help
---

### Post by kingatnight on 2011-02-28
Hi, I've recently switched to Ubuntu and everything runs perfectly except whenever i'm downloading a torrent in Ktorrent or Transmission it will download for about 5 minutes and then my system will just completely shut off. Can anyone tell me why this might be happening? It usually happens whenever it get's above a 2mbps download speed. In windows, however, I can get up to 20mbps and my computer won't even lag... let alone crash. :\

Can someone please help? Thanks in advance :P

---

### Post by Hedgehog1 on 2011-02-28
> **kingatnight said:**
> Hi, I've recently switched to Ubuntu and everything runs perfectly except whenever i'm downloading a torrent in Ktorrent or Transmission it will download for about 5 minutes and then my system will just completely shut off. Can anyone tell me why this might be happening? It usually happens whenever it get's above a 2mbps download speed. In windows, however, I can get up to 20mbps and my computer won't even lag... let alone crash. :\

Can someone please help? Thanks in advance :P

I know this wont sound logical, but if you use Deluge rather than transmission, this should stop happening.

While my system didn't crash, it horked ***<technical term: horked>*** my network connections and forced me to re-boot. It was not until I did some serious upgrades to my network that transmission stopped crashing the router.  I did get it all to work with transmission, only later to discover that Deluge is faster anyway.

Please see if Deluge works for you without causing the same issues.

---

### Post by kingatnight on 2011-02-28
> **Hedgehog1 said:**
> I know this wont sound logical, but if you use Deluge rather than transmission, this should stop happening.

While my system didn't crash, it horked ***<technical term: horked>*** my network connections and forced me to re-boot. It was not until I did some serious upgrades to my network that transmission stopped crashing the router.  I did get it all to work with transmission, only later to discover that Deluge is faster anyway.

Please see if Deluge works for you without causing the same issues.
I just tried Deluge and I get the same problem. At about 5%, just as it went over 2mbps, my system shut off.

:|
Does anyone know a solution for this? I've tried using Ktorrent, Transmission and Deluge and I always get the same result so I doubt it has to do with my torrent client.

---

### Post by kingatnight on 2011-03-01
bump.

Does anyone have a solution for this? Please, it's really annoying having to download things five minutes at a time and restarting my computer over and over again

---

### Post by xfearxnxloathing on 2011-03-01
does this ever happen when not downloading torrents?

---

### Post by matt_symes on 2011-03-01
Hi

> my system shut off

Are you saying your computer automatically shuts down or is it hanging or is x crashing ?

What do you mean by that ?

Kind regards

---

### Post by kingatnight on 2011-03-01
> **xfearxnxloathing said:**
> does this ever happen when not downloading torrents?
Nope, it's weird. Ubuntu runs flawlessly unless I'm downloading torrents. When I download files in google chrome at high speeds it works fine and doesn't crash.

[QUOTE=matt_symes]Are you saying your computer automatically shuts down or is it hanging or is x crashing ?

What do you mean by that ?[/QUOTE]
It just turns off instantly. First the Torrent client I'm using will crash then, within a few seconds, my screen goes black and my computer shuts off.

I should probably add that if I cap my download speed's at about 500kbps it won't crash and will download smoothly. But that's very slow compared to what I'm used to (usually 10 -12mbps)..

---

### Post by xfearxnxloathing on 2011-03-02
> **kingatnight said:**
> Nope, it's weird. Ubuntu runs flawlessly unless I'm downloading torrents. When I download files in google chrome at high speeds it works fine and doesn't crash.


It just turns off instantly. First the Torrent client I'm using will crash then, within a few seconds, my screen goes black and my computer shuts off.

I should probably add that if I cap my download speed's at about 500kbps it won't crash and will download smoothly. But that's very slow compared to what I'm used to (usually 10 -12mbps)..
run your system monitor at the same time and keep it next to or on top of your torrent downloader program (btw deluge is the bee's knees!)that way when this happens you can still see the system monitor for an idea of what might have happened.  but while ur downloading keep watch of how much cpu is being used, your cpu may be reaching 100% and over-heating, freezing then shutting down.

---

### Post by matt_symes on 2011-03-02
Hi

Check your log files. They might give an indication of what is happening.

Kind regards

---

### Post by Jouke74 on 2011-03-03
You did not accidentally turn on the Gnome power manager feature to shutdown when your system is idle for 5 minutes did you?

Or your system crashes on the screensaver, in that case try to turn of screensaver (and power monitor off). Or change the times to e.g. 10 minutes and see if this makes the shutdown happen in ten minutes (then at least you know this is the cause).

---

### Post by ktm1 on 2011-07-08
Did you ever figure out what caused this?

I have the same problem, except my machine just randomly hard freezes, doesn't shut down. Deluge and Transmission, machine freezes only when torrenting (used to get GPU lock outs, but that was solved).

I thought it could be a memory problem (cached memory seems to go very high quickly when torrenting), but I ran memtest86 and found no problems.

Using 11.04.

---

### Post by windguy on 2011-08-01
Hi there;

I am also having the same issues using deluge or Transmission. I am currently working with 11.04 on two different computers and having the same issues with both. After about 5-10 min of downloading screen goes black, computer lights are still on and usb wireless stick stays lit. On my other computer same thing happens but I am using a dlink wireless card. Thought it was the card causing the issue and purchased a belkin usb wireless stick and still getting the same issues. I am also having this issue when I stream online radio, Except it stays streaming for alot longer. When it freezes the it sounds like I have a cd skipping. Screen stays black and all lights are on computer. Harddrive light stays lit and does not indicate that it's working.You tube or online news so far hasn't given me this issue.  

PLEASE HELP!!!

---

### Post by KEE on 2011-08-19
same problem[http://ubuntuforums.org/showthread.php?t=1827471]("http://ubuntuforums.org/showthread.php?t=1827471")

---

### Post by zapho on 2011-11-13
Hi there,

Just to say that I have this problem too, running 11.10 and I didn't have it when running 11.04 or before. My computer doesn't restart though, it freezes and doesn't respond to key commands like ctrl+alt+f1 for terminal or even REISUB. 

Just to confirm other peoples reports, it only happens when running a bittorrent client (I've tried transmission and dulge, happens with both) and also only happens when the download speed exceeds 500kb/s. None of the log files show an error.

---

### Post by thorbs on 2012-03-26
I am actually having a very simillar problem, when ever I starts transmission my system crashes. I do not get a black screen but my hardisk just get into a loop. There is no activity in the processor itself (I can see with top)its just the hardisk getting stuck (I can see and hear) I am not aware of any updates to my system other than that I some days ago added the chromium stable ppa.

t.

---

### Post by claracc on 2012-03-27
I recommend you open a specific new thread for your problem with transmission. This is an old thread.

Describe clearly the problem and also add information about your hardware and the conditions when the crash occurs.

---

