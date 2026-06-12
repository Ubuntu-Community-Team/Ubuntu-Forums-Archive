---
title: "Audacity jumps when recording, why?"
date: 2009-07-03
forum: General Help
---

### Post by sponsoredwalk on 2009-07-03
Hi I just upgraded to 8.04 from 7.10 and Audacity, when i record, begins to jump and stall ruining the recording every time, it's really affecting me, it began for no reason just before i upgraded to 8.04 and has not gone away, seriously slowing me down and ruining the whole idea of linux, i have tried lowering the sample rate, sudo nice -20 audacity, using xcfe session while trying these also doesn't help. Thanks so much for any assistance it's a big problem.
Amabo Te :)

---

### Post by dcstar on 2009-07-03
> **sponsoredwalk said:**
> Hi I just upgraded to 8.04 from 7.10 and Audacity, when i record, begins to jump and stall ruining the recording every time, it's really affecting me, it began for no reason just before i upgraded to 8.04 and has not gone away, seriously slowing me down and ruining the whole idea of linux, i have tried lowering the sample rate, sudo nice -20 audacity, using xcfe session while trying these also doesn't help. Thanks so much for any assistance it's a big problem.
Amabo Te :)

Install a later version of Audacity, or enable the Backports for your system and a newer version should appear on the upgrade list.

---

### Post by ToFue on 2009-07-03
would it matter if the kernel is real-time or not?

dcstar, Are you running regular Ubuntu, or "Ubuntu Studio" ?

(just throwing darts..)

 If this *Just* started to occur *Before* the upgrade, then I would think that the upgrade itself could be ruled out..

On traditional DAWs this problem usually occurs with fragmented or full hard drives. It's common practice to use a second (smallish) drive altogether for the actual tracking of music, allowing less stress of read/write/buffering and more heads available that are dedicated to read/write during a session, and to have a (large) archive drive for storage of completed/offline sessions.. RAID also helps in performance, but isn't really necessary.. 

Also, commonly could be the buffer size, not necessarily the sample/bit rates (though they do scale a balance when tweaking for performance vs stability when choosing the right bufferings at whatever sample/bit rate depending on your actual soundcard).. so play with the buffers, and increase the play buffer (try reducing the rec buffer as well, but increase if symptoms still exist) if doing 'realtime' tracking.. another tactic is just play each track to a metronome, save file, then pool the waveforms into a single session for playback editing, and increase the playback buffers.. but expect latency. The whole reason for the balancing act is to reduce latency while keeping the system's performance stable & smooth.. which is where pro gear comes in to accomplish this with putting the least stress on the computer itself by crunching DSP functions like audio in/out routing, plugin processing(architecture dependent), A/D-D/A conversions and mixing functions, slaving to the audio app's engine..

 these solutions apply across O/S platforms and are step-1 to troubleshooting the symptom you described above. Beyond that, try Ardour and see if the symptom persists, and balance the buffers.. as a universal starting point use 44k or 48k samplerate @ 24 or more bitrate  when playing w/ buffers and turn off any plugin effects ::shrug::

---

### Post by sponsoredwalk on 2009-07-04
> su (give password)
nice -20 audacity

^:|^ if i give my password i seen to get a different audacity, it doesn't have any of my previous recordings saved in "recently used projects" and i get a welcome message with this one. It's strange because the one under >sound and video. is still not good, but i'm really happy i got it some version of audacity workinbg, thanks :)

---

