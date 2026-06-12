---
title: "Convert avi to dvd burn dvd"
date: 2011-08-17
forum: General Help
---

### Post by mrag on 2011-08-17
My apologies, I have searched (and searched and searched), but believe I have now used all remaining brain cells. I have Natty (dual boot XP). I have a 700MB avi file. Plays nice on my computer(s), but I would like to play it on my home dvd player with big screen tv. Seems simple enough, in theory, get DeVeDe*, create ISO, use Brasero, burn DVD, play DVD. Well so much for theory....
DeVeDe says I first need 'remove' Libavcodec52, Libavutil50, etc. So I go to 'remove' these pieces and I then get message "to remove Libavcodec52, these items must be removed as well:" This includes VLC and vlc-nox and Ffmpeg plug in! I don't currently use VLC, but understand that is a very good player to have.

Is it really this complicated to get to watch an avi on my dvd player? I must be missing something obvious. Any help much appreciated.

* and yes, I am also confused on the required "dependencies." Like where to get them, why, do I really need them, etc.

---

### Post by ron999 on 2011-08-17
> **mrag said:**
>  in theory, get DeVeDe*... 
Hi
Try using the latest version of DeVeDe.
Download the 3.17.0 deb file from the website here:- [http://www.rastersoft.com/programas/devede.html#download_section]("http://www.rastersoft.com/programas/devede.html#download_section")

---

### Post by mrag on 2011-08-17
Thank you. However, if I go to that site and click on and save the DEB version download and then double click, I get to Ubuntu Software center which then will say there is an older version to install and I am back to where I started. How would I even try to install this latest version? Again, my apologies, I am very new to this and I wasn't all that sharp to begin with.

---

### Post by ron999 on 2011-08-17
> **mrag said:**
> Thank you. However, if I go to that site and click on and save the DEB version download and then double click, I get to Ubuntu Software center which then will say there is an older version to install and I am back to where I started. How would I even try to install this latest version? 
Hi
Ignore the warning about an older version.
'Close' then 'Install Package'.

---

### Post by 741Baus on 2011-08-17
Hi mrag I use a command line script to do exactly what you want to do , I needed to convert avi's to dvd for my nephew who drives a truck up and down the east coast and only has an older dvd player in his truck ,
create a folder in your home directory eg. avi2dvd and copy the avi file to that folder you want to convert in there ,then open a terminal and do the following


```
cd /home/your-username/avi
```

then run this command

```
avi2dvd *
```

be-warned that after it has finished it will delete the original avi file this is why I say copy your avi file(if you want to keep the original copy) to your directory, I have successfully converted over a hundred avi files to dvd ,that play in a stand alone dvd player, this way 
hope this helps

---

### Post by 741Baus on 2011-08-18
I ,sorry mrag I got a bit ahead of my self and forgot to add this tutorial that you have to do to enable avi2dvd to work here is a link 

[URL=http://www.ubuntugeek.com/howto-convert-avi-to-dvd-iso-in-ubuntu.html[/URL]

if you follow these instructions and run the script it will work

---

### Post by mrag on 2011-08-20
Thank you both for your advice. Ubuntu did the same with the "newer" version as the older. So I ended up uninstalling vlc and some other programs that had a conflict. I had to also remove gstreamer ffmpeg but was then able to install DeVeDe. Later I went back and re installed gstreamer and things seemingly work fine.

I liked the avi2dvd concept although I'm still so new to this, the idea of adding a script didn't seem the way to go. Looking at it again now, it might be the way to go.

A side question that perhaps can be quickly answered. I used DeVeDe to convert two different avi's to an iso. I then used Brasero to burn the actual dvd's. The second one, was about 25% longer and there are spots in there where video stops for a few seconds. Seems more towards the end. The first one had no problems. Any ideas why? I'm guessing it could be the source I used, it could be DeVeDe, it might be the dvd media I used or the player I was using or Brasero. Big list, wondered if there was a quick answer.

Again, many thanks for the replies, they spurred me on.

---

### Post by Ubuntu Warrior on 2011-08-26
I have tried to use devede for this but the avi movies seem to get screwed up - the sound starts out in sync but then falls behind more and more until after about 2 minutes it is totally unwatchable. The original avi movies play fine under vlc, movie player or mplayer so devede is definitely messing with the audio syncing in a bad way.

Will check out the avi2dvd option.

---

