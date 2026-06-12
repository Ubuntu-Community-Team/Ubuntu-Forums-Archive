---
title: "MythTV Sound Problem..."
date: 2006-04-14
forum: General Help
---

### Post by StalfoS on 2006-04-14
Hi all,

I have installed Ubuntu on my Athlon xp 64 3000+ machine and I must say I am impressed so far.  Pretty much every piece of hardware that I have "just worked".  

I installed MythTV for its PVR abilities, however, I can not get any sound to work.  I have 2 sound cards: the onboard AC97 and a USB M-Audio duo.  My TV tuner is a Leadtek TV2000 XP Deluxe which has a little external cable for audio that is connected internally to my motherboard's aux line in.  Now here's the deal

-Both sound cards work fine to play system sounds, mp3s, etc.
-By un-mutting the the AC97's aux input in the ALSA mixer, i can hear sound in TVTime, and even in MythTV -- however in MythTV, usinng this method, the sound is out of sync.  This is because mythTV buffers the video and I am getting live audio.
-So I tried setting the AC97's aux as the capture source, and muting the output but then I get no sound.

Ideally, i would record from the aux line in and playback with the M-Audio Duo, but at this point i would be happy with any playback.  Im not sure what to set the sound devices to in MythTV.  I have tried just abut every combination in hopes that one would work: /dev/dsp (the ac97 i think), /dev/dsp1 (the duo?), ALSA:default (??), ALSA:hw:0,0 (????).

If anyone has any ideas, please help me out.  

Oh yeah.. and one more thing to conclude this long post.  Any idea why the tv tuner's picture quality is so bad on mythtv but OK on tvtime?

Cheers.

---

### Post by rebeljt on 2007-04-08
> **StalfoS said:**
> 

Oh yeah.. and one more thing to conclude this long post.  Any idea why the tv tuner's picture quality is so bad on mythtv but OK on tvtime?

Cheers.

I have the same problem as you with PQ. I am going to guess its due to lack of Hardware Mpeg 2 . I think I am going to go to Circuit City today and buy the Hauppauge HVR 950. It has an ATSC Tuner. Allegedly it works in Linux and with mythtv. I guess I'll find out. 

JT

---

### Post by grahams on 2007-05-02
Hi

Did you get your Hauppauge HVR-950 working ok? Any issues or recommendatiosn?

---

### Post by RayVad on 2007-07-22
Maybe this is your solution:
[http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound]("http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound")

---

