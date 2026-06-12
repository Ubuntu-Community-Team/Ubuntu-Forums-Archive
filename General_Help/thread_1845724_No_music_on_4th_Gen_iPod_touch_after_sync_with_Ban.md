---
title: "No music on 4th Gen iPod touch after sync with Banshee"
date: 2011-09-17
forum: General Help
---

### Post by teh5abiking on 2011-09-17
[FONT=Arial]I recently installed Ubuntu 11.10 beta 1 to see how much progress has been made on Unity and Ubuntu in general, and overall I'm thoroughly impressed. For a beta, it's largely bug-free. 

Anyway, when I tried to sync my music library that I imported from my third generation iPod nano, after the sync, when I checked to see if the music was on my iPod, nothing was there. I checked to see if the files were in my iPod, and they were, but for some reason, it didn't show up. 

I was originally on 4.3.3, but I thought it was the iPod firmware that was giving me issues, so downgraded to 4.2.1, and still no dice. I also tried Rhythmbox and gtkpod, but still no dice. Music was on the iPod, but wasn't showing up in the music app.

I still had this problem with Ubuntu 10.04 and 11.04.

Anyone know what's wrong? 
[/FONT]

---

### Post by DukeBoxer on 2011-09-17
Make sure your music files have .mp4 after the file name. The same thing happened to me after importing music from an ipod on 11.04. Ubuntu still recognizes the file as a music file, but the ipod doesn't. I have a command you can use in the terminal to change all the files in the folder on your computer to end in .mp4 so that when you move the songs back to your ipod they will play. Ill get it for you when I am home

---

### Post by DukeBoxer on 2011-09-17
Here it is... cd into the directory with the music files and then paste this command

for i in *; do mv "$i" "$i.mp4"; done

so it would be like this 

~$ cd ~/music/Pink\ Floyd
~ /Pink Floyd$ for i in *; do mv "$i" "$i.mp4"; done

got it?

---

### Post by teh5abiking on 2011-09-17
Uh, .mp4 is a video extension, not an audio extension. 

All my music has the m4a extension. which has been compatible with my nano and my touch, therefore it should still be compatible with the iPod, no?

---

### Post by DukeBoxer on 2011-09-18
Sorry, I thought .mp4 was audio. I changed all the files that I pulled off of my ipod to .mp4 and now my Mac, which didn't recognize the file as anything before now sees it as audio. Whatever the extension, make sure there is one on the audio file. That's what I was trying to say

---

