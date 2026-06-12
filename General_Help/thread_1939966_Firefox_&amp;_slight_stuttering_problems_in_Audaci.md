---
title: "Firefox &amp; slight stuttering problems in Audacious"
date: 2012-03-12
forum: General Help
---

### Post by SPARTAN-118 on 2012-03-12
Hi, I recently installed Lubuntu after trying out Sabayon and even regular Ubuntu, but both were just too much for my hardware. Which, before I go any further, is:
AMD Athlon 64 3200+ @ 2GHz
2GB DDR2 667MHz Corsair RAM
500W Cooler Master PSU
ATi/AMD HD Radeon 3650 (AGP) 512MB
Biostar mobo (eugh)

So anyway, as the title implies, Firefox causes stuttering issues when playing music in Audacious (ie slowdowns). Which doesn't make much sense, because with 2GB RAM and a 2GHz processor, you'd think Lubuntu would have no issues. But I had this problem on Sabayon and Ubuntu (which was far worse) - mind you, that was with only 1GB RAM (I recently got replacement RAM from Corsair as my previous 2GB was defective). 
But this is Linux, not Windows Vista. There are reports of people getting Lubuntu working fine on PIIIs and 512MB of RAM. Actually, come to think of it, Vista works relatively fine on another partition, only slightly slower than I would like, but Windows just isn't for me.

I've tried "lightweight" browsers such as Arora (which was a mess) and Midori, which is actually what I'm using now to type this. Those help immensely, and even using Chromium helps somewhat (though there is slight stuttering at times), but I am just too used to Firefox. (It helps that FF Sync keeps all my bookmarks and RSS feeds, while importing bookmarks loses those feeds with other browsers.)

Any suggestions on how to reduce the slowdowns on my system? The only extensions I have installed in Firefox are AdBlock+, Personas+ and Personas Rotator. That, and the default Ubuntu-integration stuff that comes from installing it with Synaptic.

---

### Post by gunksta on 2012-03-12
- Start the system monitor. 
- Start firefox and audacious. 
- Start playing your music. 
- Watch the system monitor. Do you get any weird spikes? If yes, where/when?

Truthfully, I notices 2-3 releases back that my computer sometimes stutters when playing music. It is really annoying and I haven't found a solution, although I confess I haven't tried very hard. This is on an i5 system with 4G of RAM, so I know its not a resource problem. I use banshee/rhythmbox. Next time I play some music, I'll do this too.

---

### Post by marinara on 2012-03-13
seems like i had this problem a few months ago.  i can't remember how i fixed it, but one thing i did was remove pulseaudio on lubuntu

---

### Post by SPARTAN-118 on 2012-03-13
> **gunksta said:**
> - Start the system monitor. 
- Start firefox and audacious. 
- Start playing your music. 
- Watch the system monitor. Do you get any weird spikes? If yes, where/when?

Truthfully, I notices 2-3 releases back that my computer sometimes stutters when playing music. It is really annoying and I haven't found a solution, although I confess I haven't tried very hard. This is on an i5 system with 4G of RAM, so I know its not a resource problem. I use banshee/rhythmbox. Next time I play some music, I'll do this too.

Loading a new page, CPU usage spikes to the 70-90% range. By contrast, just reading plain text on a page, the CPU usage hovers around 40-50%. I'd say average usage is around 60%. 
That's way too high for having only three programs open, and it's not even that. It's just Firefox. I can have multiple Nautilus (or whatever file manager Lubuntu uses) open, with multiple large file operations happening, and Audacious won't miss a beat (literally).

> **marinara said:**
>  seems like i had this problem a few months ago.  i can't remember how i  fixed it, but one thing i did was remove pulseaudio on lubuntu

One thing I've noticed that I'm quite pleased with in Lubuntu is that turning up the system volume to max doesn't cause issues when playing music. That is to say, in both Sabayon and Ubuntu (GNOME 3 and Unity respectively) when the volume went past "Unamplified" distortion was clearly heard in *all *sounds that played. I don't know if PulseAudio has anything to do with it, or maybe just the lower resource consumption, but if it was because the other OS's were using ALSA and Lubuntu uses PulseAudio, then I don't think that's a good idea.
Please correct me if I'm wrong. I know that Firefox is the cause here, but unless I have to, I'd rather not use Midori. I mean, come on, only 361 MB of my RAM is being used right now. There's no reason this should be happening on ***Linux***, let alone Lubuntu.

EDIT: I just noticed in the Audacious preferences that the current Output Plugin is ALSA. PulseAudio is also available. Selecting that is only just better, or maybe I'm imagining it. I just want flawless playback while browsing, like I have (or think I have) in Vista with Foobar2000.

EDIT: After selecting "Pulseaudio" in Preferences then clicking "Close", reopening the Preferences menu shows that ALSA has been automatically reselected. I don't see a button for saving settings, so I'd presume clicking "Close" would save the default output plugin as Pulseaudio. Obviously something's not right here. In fact, after selecting any of the other output options, no music plays. Audacious just rapidly goes through every song I have then stops. It seems just ALSA works.

---

