---
title: "flash/youtube videos are slow on ubuntu 11.04"
date: 2011-09-01
forum: General Help
---

### Post by TimeWillShow on 2011-09-01
I am back with another question.

Oke, when I run youtube, or any online video (not movies)it is really slow, I mean the sound is perfect but the video is slow. I think it is because of the flash player. 

can someone help me, ohyea and if you explain something try to do it in a way that an Windows user that is trying to make the convert to ubuntu can understand. 

This makes my internet experience a little disappointing.

I you need more information, please tell me and tell me how I can get that information in ubuntu 11.04

some general info:
I have an acer aspire one (netbook)
It has an SSD disc instead of a hard disk
it has 2gb instead of the one gb internal memory
and I think it is a 32 bit
and it has ubuntu 11.04 installed on it

BTW I tried to search on it, but the explanation was very difficult to understand (not windows user friendly:P) so I hope you guys can help me out in a windows user friendly way:p

---

### Post by BlinkinCat on 2011-09-01
Did you download ubuntu restricted extras from Software Center?

---

### Post by TimeWillShow on 2011-09-01
I did not do that, but I am trying to install it now and that does not work.

It keeps saying check out your internet connection, but nothings wrong with my internet connection:p

---

### Post by BlinkinCat on 2011-09-01
Try this - Open terminal and enter

```
sudo apt-get update
```Report back here with any errors -

---

### Post by TimeWillShow on 2011-09-01
Thanks I think it worked, I am not 100% sure, because sometimes it did and sometimes it didn't but I gues time will show

---

### Post by pqwoerituytrueiwoq on 2011-09-01
install the flash aid addon for firefox it will get you the correct version of flash

you can play streaming flash in the move player and get far better performance like this
```
f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```you will get one line output from it eg "/proc/27070/fd/17"
then you make a sym link in your tmp folder like this notice i used th output from the previous command
```
ln -s /proc/27070/fd/17 /tmp/video.flv
```the to play the movie
```
totem /tmp/video.flv
```doing this lets me play flash videos full screen with <4% CPU usage (results will vary depending on your graphic card)

EDIT:
the 1 line copy/paste version:
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"video-$d.flv";totem /tmp/"video-$d.flv"
```this works on streaming flash (eg youtube,megavideo,myspace,facebook,videozer)
note the video must be steaming (hit play then pause in flash)

---

### Post by lovinglinux on 2011-09-05
> **pqwoerituytrueiwoq said:**
> install the flash aid addon for firefox it will get you the correct version of flash

you can play streaming flash in the move player and get far better performance like this
```
f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```you will get one line output from it eg "/proc/27070/fd/17"
then you make a sym link in your tmp folder like this notice i used th output from the previous command
```
ln -s /proc/27070/fd/17 /tmp/video.flv
```the to play the movie
```
totem /tmp/video.flv
```doing this lets me play flash videos full screen with <4% CPU usage (results will vary depending on your graphic card)

You can also use [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/"), which allows to watch YouTube with a different plugin or external player.

---

### Post by TimeWillShow on 2011-09-05
All of you thanks a lot,

I did not understand the complicated code part (because i just went from windows to ubuntu)

but thanks I will figure this out:p

---

