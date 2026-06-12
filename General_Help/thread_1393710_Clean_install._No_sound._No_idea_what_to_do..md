---
title: "Clean install. No sound. No idea what to do."
date: 2010-01-29
forum: General Help
---

### Post by heysean on 2010-01-29
This is my eleventieth attempt to get Ubuntu working on my computer and I feel that if I can't get this working I'll probably give up.

I bought an Emu 1616m soundcard before I decided to give linux a stab, so there is no other sound card for me to use. I use it for audio production, but do all that in Windows and don't want to bother transferring mounds of stuff into linux. I'd rather have this be my general use OS.

I'm still pretty dang new to Ubuntu, so if I leave something off please let me know.

Ubuntu 9.10

```
sean@ionstar:~$ lspci | grep audio
04:07.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

```

When I went dabbling through distros it worked out of the box in openSUSE 11.1. However, I didn't like YaST or the rest of how it was set up so I decided to leave it.

I'm looking foward to wining StarCraft.exe, and sitting back to watch and hear those guys get killed by the zerg like :popcorn: :D

---

### Post by gabo.cr on 2010-01-29
Can you hear the computer sounds when you login?
Have you try listening to MP3 and DVD?
Have you try playing videos or music from Firefox?
Is there anything enabled under System > Preferences > Sound.

If nothing works, you should check to see if the sound drivers are installed.

---

### Post by ks07 on 2010-01-29
Hey, just searched for the soundcard chipset and have found what sounds like your problem in another topic. Check out the solution in this topic and see if it works (it may not as it is for the alpha release): [URL="http://ubuntuforums.org/showthread.php?t=1221005"]http://ubuntuforums.org/showthread.php?t=1221005
[/URL]

---

### Post by heysean on 2010-01-29
**Can you hear the computer sounds when you login?** Nope.
**Have you try listening to MP3 and DVD?** Yes. No luck.
**Have you try playing videos or music from Firefox?** I've been wrestling with getting flash installed, but that's another beast I'll tackle at a later date.
**Is there anything enabled under System > Preferences > Sound.** Window sounds were disabled, but the device shows up as "Internal Audio" under hardware.

**If nothing works, you should check to see if the sound drivers are installed.**

How is that done?
I've looked for way to do that, but everywhere says "They should already be installed."

---

### Post by heysean on 2010-01-29
@ks07

I found the actual bug report of that a little while ago.
My gnome-alsamixer doesn't have those buttons :/
I tried doing it in alsamixer to no avail

---

### Post by howefield on 2010-01-29
Try alsamixer in a terminal, check the sound levels ?

Edit : sorry, too slow.

---

### Post by heysean on 2010-01-29
@howefield

no luck after turning everything up some

---

### Post by gabo.cr on 2010-01-29
> How is that done?
I've looked for way to do that, but everywhere says "They should already be installed."

Go to System > Administration > Hardware Drivers.

It will show you any restricted drivers installed and any restricted drivers that need to be installed.
Have you try this webpage:
[http://hardware4linux.info/component/16482/](http://hardware4linux.info/component/16482/)

---

### Post by heysean on 2010-01-30
It only shows the nVidia drivers.

I also apologize for being a total noob, but that hardware4linux page makes absolutely zero sense to me. I really don't know what I'm looking for.

---

### Post by heysean on 2010-02-02
I'll bump this in a final attempt.
I'm guessing I'm doomed to continue with Windows?

[edit]
If anyone comes across a solution and would be generous enough to tell me, please email me at [email]hey.sean@yahoo.com[/email]. Thanks
[/edit]

---

