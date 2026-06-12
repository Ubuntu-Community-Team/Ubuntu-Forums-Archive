---
title: "no audio in certain programs?"
date: 2011-05-29
forum: General Help
---

### Post by rhobere on 2011-05-29
Let me start off by saying I'm a n00b to ubuntu. I installed studio x64 11.04 yesterday and I am running into issues with my Lexicon Lambda audio interface. Both Banshee and Audacious play music, but I get no sound. But if I get online and go to pandora, youtube, or whatever it works fine. I hooked the interface up to my laptop which is running the regular x32 11.04 and it acted the same way.

after doing some searching through the forum here, I found a thread where someone was having the exact same problem and they concluded that they just needed the realtime kernel. the problem now is that I can't get the rt kernel to install. I've tried doing it through the terminal with:

sudo apt-get install linux-rt

and it just says unable to locate package linux-rt

after some more searching, it seems that maybe there isn't a realtime kernel for 11.04? is this true? if so, is there an alternative to the rt kernel that will do the same thing?

---

### Post by linuxinstalledfromhdd on 2011-05-29
I'm going to make two quick observations here.

If you are using this for recording purposes and you have additional equipment that you will need to interface with this OS, you are probably going to only have 32-bit proprietary drivers to work with, so the whole concept behind having a 64-bit system may be overkill. And you may at some point hit a wall with using 64-bit OS when 32-bit would have totally sufficed for what you needed to do with that system.

The other thing would be that I would have recommended you go for a more stable version like 10.10 and use the PAE Kernel instead.  11.04 still has some bugs, and we are getting to them as fast as we can.  As long as you don't mind the hassle of that at the same time as being a new user to Ubuntu, so be it.:D

---

### Post by rhobere on 2011-05-29
I'm not currently using it for recording. I just use the interface to hook up to an equalizer/monitors to play music, movies, etc and this interface is only a temporary until I get the money to fix my PreSonus FireStudio. honestly, the only reason I picked ubuntu studio is because I thought it would be nice to have the right software in the event I do start recording again (long story short, I'm a drummer temporarily living in an apartment). As I've learned from all my searching, it wasn't really necessary for me to get studio at all, but that's besides the point. Really, I just need to be able to play music right now.

luckily, I'm patient and don't NEED it to work 100% for a little while so I guess I'll just sit tight for now and consider downgrading if need be in the future.

Thanks for the quick response. If anyone has any experience with this problem and knows of a good audio/video program that does work with this interface, let me know.

---

