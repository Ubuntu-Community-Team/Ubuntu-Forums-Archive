---
title: "network priority or niceness ?"
date: 2012-03-31
forum: General Help
---

### Post by ohnonot on 2012-03-31
hello everybody!
I'm listening to music over the internet a lot and if it doesn't take too much resources i want to give it total priority. 
for the simple reason that i hate it when it stutters for even 1 millisecond every 10 minutes. 
anyway it does not eat a lot of cpu. 
i have the niceness for the process adjusted, but if i'm downloading sth at the same time the streaming pauses every now and then, hence the question:

can i give priority for network bandwidth?

also i'd like to do the same thing reversed (lowest possible priority) for transmission.

any help/suggestions appreciated.

---

### Post by Ms. Daisy on 2012-04-02
Give this a look, I think it's what you want to do:
 
[http://askubuntu.com/questions/5358/configure-application-priority-to-access-the-network](http://askubuntu.com/questions/5358/configure-application-priority-to-access-the-network)
 
If you try any of those please post back & say how it went.

---

### Post by ohnonot on 2012-05-11
thanks!
i only now got around to testing wondershaper.
i didn't really see much difference while setting it up (i was using speedtest.net). meaning, cutting bandwidth shows clearly, but i didn't really see where it would get better *with *wondershaper than without, no matter how much i fiddled with the settings.
for now, i just cupped the upload speed a tiny bit, let's see if it helps.

the reason i'm posting now is that i didn't get the local priorities right, as i thought.

i'll try to go through this scientifically:
i'm listening to music with shell-fm that gets the music from the net.
let's just assume there's no trouble with the network.
but still the sound is... scratchy sometimes, like it sounds when it doesn't get quite enough cpu time for processing sound.
apart from shell-fm, there's the terminal emulator - will that also need a high priority to make sure there's no dropouts?
sound goes through alsa, channel is pcm.
some time ago i did some adjustments to audio niceness as recommended by linuxmusician.

how can i give shell-fm *and all the other processes it's using* high(est) priority?

i know somebody always raises a finger and says don't give too much prio to any one program, but for me it's very simple:

- i know the program doesn't use much resources
- while i use it, it has very high priority, for me personally.

oh and i will report back about wondershaper.

---

### Post by ohnonot on 2012-05-25
i've been trying wondershaper for a while but there's really no effect.

i'm using mobile broadband (dongle) via usb and connect it with wvdial (in stupid mode). 
the connection is cheap and limited; most probably the service provider keeps an eye on my bandwidth but how they restrict it i have no idea. i suspect high peaks are possible since the connection is physically able of much more. 
what i read about wondershaper, the whole concept doesn't seem to apply here. 
also i don't see any application-specific settings (like shell-fm always has priority over transmission) ...

well it was worth a try and at least it hasn't wrecked anything.
;)

my other question about "normal" priority persists (post #3), but i might have to start a new thread on that.

---

