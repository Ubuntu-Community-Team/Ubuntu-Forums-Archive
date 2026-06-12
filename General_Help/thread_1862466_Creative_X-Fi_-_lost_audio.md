---
title: "Creative X-Fi - lost audio?"
date: 2011-10-16
forum: General Help
---

### Post by kooldino on 2011-10-16
I'm running 11.10 on a fresh install.  I just updated my nividia driver and rebooted.  Upon reboot, I lost my audio. The system shows my creative x-fi and all of the settings, and my speakers even "pop" when the OS is initializing, but I'm not getting any sound output.

Yes, my speakers are hooked up properly, turned up, etc.  My volume is high, and the computer is not muted.

Help?

---

### Post by kooldino on 2011-10-17
Has this happened to anyone else?

---

### Post by Hooker Jay on 2011-10-18
Count me in -- spent all day recovering from a botched upgrade to 11.10 that took my dual-boot WinXP down with it. Full raw format of both 80GB SATA drives, installed WnXP SP3 and now just got done installing Ubuntu when I noticed my Creative X-Fi has no sound at all. Installed latest updates (about 60) that from software manager and nothing. Haven't had time to check on-board sound through my headset yet, but it usually works out of the box except the microphone (it's known as ADI SoundMAX in WinXP) ...

---

### Post by kooldino on 2011-10-19
Great.  The odd thing is that this actually worked at first for me, until I ran some updates.

---

### Post by viperdvman on 2011-10-19
Go to your Terminal and type:

```
alsamixer
```

Check all your sound settings and make sure that none of the entries that deal with what you hear (PCM, Master, etc.). I've had that problem on my Audigy 2 ZS, mainly with WAV/MP3 and Mic capture... and using alsamixer worked wonders.

Hope it helps with your problem. If not, then I don't know :(

---

### Post by kooldino on 2011-10-19
> **viperdvman said:**
> Go to your Terminal and type:

```
alsamixer
```

Check all your sound settings and make sure that none of the entries that deal with what you hear (PCM, Master, etc.). 

Make sure what?  None of them are muted, if that's what you're saying.

---

### Post by Hooker Jay on 2011-10-21
Well, I can't help you there -- my motherboard embraced its inner Danny Glover the other day and flat lined. It was an Asus A8R-MVP and yup, it was definitely getting too old for @^#! I put it through the last month. Plucked the 2 months old CMOS battery out of it, stuck in a Gigabyte GA-K8N Ultra 9 (getting that sucker to POST was FUN!!) I had floating around here with the rest of my hardware from the old MB and spent the last two days just getting WinXP up and fined tuned to my liking. So with all the issues I had with Ubuntu 11.04 and 11.10 with video, sound, and GRUB over the last month, my hard drives have seen more more formats than a Clear Channel radio station and it has wore me out. So I'm gonna make do with a barebones 11.10 VMWare install and take a break for a while ... 

As for the sudden loss of sound with the X-Fi, I went googling and found a potential lead on fixing the issue two days ago ... but that's when my system kicked the bucket before I could give you all a head's up on it. The gentlemen had lost sound on his PCIe Fatal1ty model upon updating to 11.10 and he solved the issue by snagging the most up-to-date source code for the X-FI series, re-compiling the driver(s), and baking it 'em into a rebuilt kernel ...

---

### Post by cbanakis on 2011-10-21
I have a creative X-Fi as well.

I have been through the last 7 Ubuntu Distro's, and that is one thing I NEVER had a problem with.

Does your sound work in different OS's?

Just considering the possibility that your sound card bit the dust.

---

### Post by 1clue on 2011-10-21
I have been searching on my hardware and looking for red flags to upgrading, and you're it.

Please post here when you get it working.  At that point I'll try to upgrade.  :)

---

### Post by masgeeks on 2011-10-21
Same problem here with X-fi, except, I get choppy audio.  Onboard audio is fine, though.  I did a clean install of 11.10 x64 prior, and to clean install, system was 11.04 x64 (clean install as well) and X-fi worked just fine with 11.04 x64.  Prior to that system was 10.04 x64 (also clean install) and X-fi did not work with 10.04 x64.  

Go figure.  

Maybe it will work again with 12.04...??? :razz:

lol

---

### Post by kooldino on 2011-10-24
This really bites.

---

### Post by Hooker Jay on 2011-10-24
> **cbanakis said:**
> I have a creative X-Fi as well.

I have been through the last 7 Ubuntu Distro's, and that is one thing I NEVER had a problem with.

Does your sound work in different OS's?

Just considering the possibility that your sound card bit the dust.

Nope - I was blaring Nazareth's "The Newz" during my last post on WinXP! :p 

And it worked fine in 11.04 Natty once I got the mixer configured right ...

---

### Post by legine on 2011-10-25
> **masgeeks said:**
> Same problem here with X-fi, except, I get choppy audio.  Onboard audio is fine, though.  I did a clean install of 11.10 x64 prior, and to clean install, system was 11.04 x64 (clean install as well) and X-fi worked just fine with 11.04 x64.  Prior to that system was 10.04 x64 (also clean install) and X-fi did not work with 10.04 x64.  

Go figure.  

Maybe it will work again with 12.04...??? :razz:

lol

Ha! Had same Problem. I solved it for me at last.
I did:
```
gstreamer-properties
```
And picked pulseAudio Sound System + Soundblaster XI device.

It works now. Only banshee does not play anything atm, but I guess that is because I unistalled pulseaudio stuff earlier...

Edit: Fixed that too, log out login :P all fine

---

### Post by NullHead on 2011-11-13
Well I'm a bit late to the party. I haven't used linux on my X-Fi machine since 10.04 or so. I'm really super rusty at audio stuff - **but** I'll take a look some time. I'm busy with school stuff now ... so it wont be any time soon. Sorry to disappoint, kooldino. I know you messaged me because of my old how-to thread, but honestly you don't need to use my guide anymore. There's a built in kernel driver. Now that it's in the kernel/alsa, hopefully the only issues you'll be running into are pulseaudio or generic audio problems that are alsa related. If not, always read your dmesg messages and look for modprobe errors. If you find any, I suggest a bug report on launchpad or posting them here. 

Good luck fellas, I'll take a look at some point.

---

