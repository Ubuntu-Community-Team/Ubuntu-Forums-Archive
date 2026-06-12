---
title: "Audio Not Working"
date: 2010-04-02
forum: General Help
---

### Post by Fernando Hernandez on 2010-04-02
I don't know what happened, but I have a guess at least...yesterday, I put my computer into hibernation with a few programs open because I was in a hurry...one of them was VLC; I had a video paused when I went into hibernation.  When I booted back into it, my audio wasn't working for anything...system sounds, programs, Flash video online, etc.

I went into the sound options and noticed that the 'test' button was giving me sound for HDA Intel (ALC268 Analog) but not for Pulse audio...well, for a while now, my programs tells me 'HDA Intel not working, falling back on Pulse Audio' or some such thing...which is why it's so odd that HDA Intel is working when I click 'test' in the options but Pulse isn't.  But it still falls back on Pulse for every program, and since Pulse isn't giving me any sound......I'm not getting audio and I don't know how to fix it.  HDA Intel hasn't been working properly for a while, but again, falling back on Pulse still worked so I was always too lazy to learn how to fix that.

Oddly enough, I did manage to get it working again with Amarok...at first nothing was outputting sound, but now Amarok is working again.  But that's it - nothing in VLC, YouTube isn't making sound, no Pidgin IM noises, no startup and shutdown sounds, nothing.  It's very baffling.

Is there something I can do to fix this issue?  Anyone have any ideas why it might be doing this in the first place?  All I know is that when I booted back in from hibernation, my volume controls were muted and my internet wouldn't let me connect and said 'networking disabled'.  I had to restart to get that working again and I thought nothing of it until I noticed I had no audio.  I don't know what happened, why, or most importantly how to fix it...I just know it's very *very* frustrating to not be able to get audio working!!

Can someone help me?  Please dumb it down as much as you possibly can (IE give specific terminal commands, packages to fix/install, settings to go into, etc).

---

### Post by Fernando Hernandez on 2010-04-02
Anyone?  I need to hear things :(

---

### Post by lidex on 2010-04-02
Check your alsamixer settings in a terminal: "Applications>Accessories>Terminal"
```
alsamixer
```

Go here and setup pulseaudio correctly:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Fernando Hernandez on 2010-04-03
[IMG]http://i41.tinypic.com/121py6r.jpg[/IMG]

They look fine to me.

Last night, Konversation got audio back, so I rebooted to see if everything did and I even got my startup/shutdown sounds back...but Pidgin, VLC, YouTube, etc - most things still aren't outputting audio.  I have no idea why some are working and some aren't...when I go into my sound settings, the default is the same for all of them, and when it tells me HDA Intel isn't working and it's falling back on Pulse Audio, then shouldn't everything be falling back on Pulse Audio?  So why is it only working for some programs and not others?  I'm getting really frustrated, and I'm afraid to try messing around with things when I don't know what I'm doing and don't want to screw my system up...

Edit: Also, the video previewer in Dolphin still plays audio and video.  But VLC won't play audio for the same videos.  It's like some applications are accepting it but others aren't...the inconsistency is really really confusing me!!

---

### Post by lidex on 2010-04-03
Sounds like pulseaudio. Take a look here:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")
Scroll down to the entries for your non-functioning programs.
More here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
For streaming:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Fernando Hernandez on 2010-04-09
Well I tried to follow various guides but I can't figure it out...most of what I'm hearing is that Pulse is not recommended for Kubuntu, but then how do I fix the HDA Intel audio?  When I go to test my audio that's the one that works when I click 'test', and Pulse does not output any sound...but most of my programs are telling me HDA Intel is broken and it's falling back on Pulse Audio!!  I'm so confused, and I'm too much of a n00b to know what I'm doing wrong/not doing at all (Ubuntu guides not recommended for Kubuntu and such) and don't want to screw up my system...but I can't do half of the things i like to do on my computer without audio!!  Will I have to format and reinstall everything from scratch, or is there some way I can fix this?  It really sucks to have to use my Windows machine just to do things like watch YouTube videos...

---

### Post by shaka_zulu on 2010-04-09
just remove all pulseaudio packages from your system and then you should hear some sound. Generally pulseaudio always mess with KDE and since it's packages are not necessary for KDE you can remove them.

---

### Post by lidex on 2010-04-09
> **shaka_zulu said:**
> just remove all pulseaudio packages from your system and then you should hear some sound. Generally pulseaudio always mess with KDE and since it's packages are not necessary for KDE you can remove them.

Agreed. Your programs should work with alsa.

---

