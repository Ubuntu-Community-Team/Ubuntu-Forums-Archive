---
title: "Set the mixer volume level at system startup or login"
date: 2011-06-09
forum: General Help
---

### Post by darkhelmetchris on 2011-06-09
How-To set the mixer volume level at system startup or login.

A funny story that led up to this how-to first...

(please feel free to skip down if you don't want to read my little story)
Today I went into a meeting with some customers, as I often do.  I fired up my wonderful Ubuntu-packin' laptop for some reference material.  The room was generally peaceful and quiet as everyone was reading or preparing their thoughts, that is until my laptop SCREAMED out my session login sound for everyone to jump and cringe.  You see, I had been enjoying my music library the night before, at home.  I made the obvious mistake of leaving my volume level set to nearly maximum.  Of course, Ubuntu's default behavior is to restore the mixer to its last known state - a point of much irritation at that moment.  This had been a problem in the past as well, and today was the last straw.  So, I did some research, for quite some time I might add, and decided to be a good community member and share my findings.  It seems that there are all sorts of opinions around the web.  The dominant opinion is that a mixer should always be restored to its last known state, that this is all well and good, and why would you ever want it to work any other way.  Lots of people suggested that the startup sound be disabled, which was not a terrible solution, but was still a work-around as it means that the next sound bite to be played is the alarming one.  (ahem).   Needless to say, I wanted to find out what I would call the "proper" way to set the mixer level at startup.  As my laptop uses PulseAudio, and my office desktop uses ALSA audio, the methods were different.

My focus was for PulseAudio as that was the original purpose.  I note here that my method for ALSA is less detailed as it is not the default for Ubuntu audio these days.  So, if you are using ALSA, you might have to be a little creative to make my ALSA note fit your needs.

I have attached 2 files to this post, one for ALSA and one for  PulseAudio.  I hope that some of you benefit from them and find them at  least a little bit useful.

---

### Post by kerry_s on 2011-06-09
just put in the startup:
amixer set Master 20%
or 
amixer set Master toggle
(which will mute it)

"man amixer" to learn more options.

---

### Post by darkhelmetchris on 2011-06-09
> **kerry_s said:**
> just put in the startup:
amixer set Master 20%
or 
amixer set Master toggle
(which will mute it)

"man amixer" to learn more options.

These are good thoughts, I will agree.  However, there are a couple of points to note.  This method was one of the suggestions I had read on several sites, and it just didn't work on my laptop or my desktop either, to the best of my efforts.  I used both the system startup scripts in /etc/rc.n and the "System, Preferences, Startup Applications" area.  I had abandoned this method before I posted.  PulseAudio seems to be loaded after ALSA (amixer is part of ALSA) and PulseAudio overrides this.  Also, this doesn't cover the login screen sound if you put this in the user-startup instead of the system-startup.  The PulseAudio file I attached earlier covers all 3 contexts:  system, default for all users, and only your own user profile.

---

### Post by kerry_s on 2011-06-09
it worked when i used gnome. i now use lubuntu so i can't test.
what did you name it in startup? i think i named mine "sound fix" so it was below pulse in the startup, meaning it ran after pulse started.

---

### Post by darkhelmetchris on 2011-06-09
> what did you name it in startup? i think i named mine "sound fix" so it  was below pulse in the startup, meaning it ran after pulse started.

To be honest, I'm not sure what I named any of the startup scripts I tried earlier, or at what point I found out that PulseAudio started after ALSA.  I'm actually kind of glad it happened that way, because I learned more about how PulseAudio interacts with ALSA.  After going through quite a few forums (this one included) and trying all the various suggestions, I had gone through literally dozens of suggested fixes and then backed them out as I tested.

When I discovered how to handle it directly in the PulseAudio script right in the user profile, it seemed logical and appropriate to do so for a few reasons:
- it didn't require any elevated sudo rights, at least for the single user method
- it meant I didn't have to create a whole new script from scratch
- the adjustment would migrate with me (this was the reason I liked the most) so that when/if I moved my /home partition to a new machine or did a clean install of the system partition later, I wouldn't have to redo it

Once I saw the benefits of the PulseAudio script edit, it seemed quite elegant, so I simply adjusted my notes for the system-wide and default-user circumstances.  That was the point when I decided "Hey, that's knowledge worth sharing."

---

