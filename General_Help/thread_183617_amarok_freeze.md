---
title: "amarok freeze"
date: 2006-05-28
forum: General Help
---

### Post by kb3hkg on 2006-05-28
I just upgraded to Dapper Drake and it is great, but now amarok keeps locking up. I can't even get a full song out of it now, but before it was working great. Any suggestions?

---

### Post by hakker.de on 2006-05-29
Does amaroK play a portion of the song or does it lock up right when double clicking a song? If the second holds, you may check if your backend (xine, gstreamer) is configured properly and works.

---

### Post by kb3hkg on 2006-05-29
it was after a song had played for a bit, but I can't seem to get it to happen with any consistency. It works sometimes and not at others.

---

### Post by hakker.de on 2006-05-30
This sounds like a problem with multithreading. Do you have a hyperthreaded cpu (Pentium 4 and above) and an SMP enabled kernel in dapper, now? You can check this with

cat /proc/cpuinfo

if you can see two processors, hyperthreading is turned on. Amarok is known to have issues with it. You may try to switch to a single processor kernel.

---

### Post by kb3hkg on 2006-05-30
it shows only the one processor, but I do have a hyper threading processor. how would I go about fixing this?

---

### Post by hakker.de on 2006-06-05
You have the default single processor kernel running, and hyperthreading is turned of. No problems expexted here. You can check by doing a cat /proc/version , this should show the 2.6.15-23-386 kernel.

For further analysis of the problem, I would run amaroK from the command line, just type amarok in a terminal window. If something goes wrong, an error message should appear.

---

### Post by DAaaMan64 on 2006-06-06
I too continue to have this problem, on gnome and kde, with and without xgl+compiz running.  Other problems I have are:

1.  The Sys tray icon only shows up 10% of the time, and only on a restart.

2.  The freezes also happen when I do some sort of action such as "get album cover from amazon.com".

Very irritating, made me try banshee, but it sucks :p.  Anyways I don't think it the back end, but I will keep looking.

---

### Post by Robgould on 2006-06-06
I have a multi-threading p4 and I can't use Amarok either.  It does not matter what kernel I use.  It is a shame because I think Amarok is the best media player you can get for linux, but I can't use it.  I get random crashes with.  I did in Breezy and in Dapper.  Rhytmbox sucks.

---

### Post by Robgould on 2006-06-06
I've not tried this myself, but you might want to give it a shot.  People seem to like it.
[http://ubuntuforums.org/showthread.php?t=159879&highlight=media+player]("http://ubuntuforums.org/showthread.php?t=159879&highlight=media+player")

---

### Post by Robgould on 2006-06-10
ok....I just tried it myself.  This is an awesome media player and a bit of amarok clone.  It is only missing minor features and does not lock up.  If you have trouble with amarok, try[ Exaile]("http://www.exaile.org/").

---

### Post by DAaaMan64 on 2006-06-22
I downloaded the latest version of amarok via this repo:

[http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14)

It solved all freezing I had.  New versions a little ugly imo, buts it's good ol' amarok!
good luck

---

### Post by Robgould on 2006-06-30
The new version still freezes for me.  The only way that I can get around it is to disable hyperthreading.

---

### Post by the badger on 2007-08-12
I'm going to give exhaile a try...
after a few weeks of running amarok, the program has been freezing on me almost everytime I use it! it is also coming up with funny playlists I've never played, forgetting the last playlist I've used, and has begun adding in songs from an ipod shuffle i can't access. glitch city! since i am all but completely unfamiliar with The Glowing Black Screen (er, well, White Screen in this case), most "helping" feedback is incomprehensible to me and leaves me unable to fix many errors I'm getting with ubuntu (i'm on 6.06 for 6 months now - no, i've no dual boot). too bad i am left for now trying to skirt around the issue by changing programs! ack!

---

