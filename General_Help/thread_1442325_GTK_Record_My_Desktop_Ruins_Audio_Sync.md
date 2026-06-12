---
title: "GTK Record My Desktop Ruins Audio Sync"
date: 2010-03-29
forum: General Help
---

### Post by CJay554 on 2010-03-29
I should mention this report is in Ubuntu 10.04, though this also happens in Ubuntu 9.10, but if i play around with the FPS in 9.10 i can get a balance between audio and video, but with 10.04 doesn't seem to work at all.

When using gtk-recordmydesktop to obviously record my desktop i turn on "encode on the fly", and my recorded video moves too fast for the audio and loses sync, video ends about 2x faster than the audio itself.

If i leave the encode on the fly off, then my video is choppy (less choppy with compiz off) but still a distraction.

my graphics card info is as so:
```
*-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:fc100000-fc1fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
```

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

Any idea? i've had bugs here and there with this graphics card though the basics of ubuntu works with it... its just the small things that pester me..

---

### Post by spiderbatdad on 2010-03-29
I remember seeing in the documentation, some time ago, that setting audio and video each to 50% achieves the best results. The default setting is 100% each. As far as recording desktop effects, I never had great results...maybe my processors have always been too slow. But I have been able to make good a/v recordings by starting cheese and running gtk-recordmydesktop on the cheese window...much better than what the cheese record feature can produce.

---

### Post by nemilar on 2010-03-29
I had this problem and couldn't solve it, even after several long google sessions.

I wound up using a separate program to record the audio, and then using one of the many encoding programs (I think it was either ffmpeg or mencoder) to combine the two files.

---

### Post by markeric on 2010-03-31
> **CJay554 said:**
> When using gtk-recordmydesktop to obviously record my desktop i turn on "encode on the fly", and my recorded video moves too fast for the audio and loses sync, video ends about 2x faster than the audio itself.

If i leave the encode on the fly off, then my video is choppy (less choppy with compiz off) but still a distraction.


I had similar problems of dropping or choppy sound. My tests didn't run long enough to observe if the audio got off from the video. 

In searching around, I found this video where the guy put all the info together in a single video. 
[http://www.youtube.com/watch?v=LsisVZ9Y9Q8](http://www.youtube.com/watch?v=LsisVZ9Y9Q8)

Here's the details of what I had to change:

[LIST]
[*]In recordMyDesktop, I set my audio and video quality to 50%.  (Don't think that has anything to do with it, but it didn't hurt either).
[*]recordMyDesktop > "Advanced" button
[LIST]
[*]"Sound tab", Device: plughw:0,0 (was "DEFAULT")
[*]"Performance" tab, checked "Full shots at every frame"
[/LIST]
[/LIST]
After doing that, my audio seems to work great now. I've observed a little audio hick-up right at the start if I was talking in the beginning. A slight pause at the start and it seems to work great.

Good luck!
-Mark E.

---

### Post by optimusmedia on 2010-03-31
> **markeric said:**
> 
In searching around, I found this video where the guy put all the info together in a single video. 
[http://www.youtube.com/watch?v=LsisVZ9Y9Q8](http://www.youtube.com/watch?v=LsisVZ9Y9Q8)


That video was the key to helping me.. woot woot!  however I needed to return to 15 fps.  My settings are in attached screenshot.

---

### Post by CJay554 on 2010-04-03
Thanks a bunch! this def seems to have improved the delay, though i can still notice a few glitches, for me i have to have 10 fps in order for the video to be in sync with audio, from time to time it looks like voice and video don't quite sync but they end up syncing shortly after. Very odd bugs, this def seems to be a audio driver problem, im using pulse, but in the device im using the plughw:0,0 entry

---

### Post by zagaboy on 2011-01-24
Thanks [optimusmedia]("http://ubuntuforums.org/member.php?u=429937") You rock! No more choppyness and sync is good!

---

### Post by mehdieft on 2012-02-21
> **CJay554 said:**
> I should mention this report is in Ubuntu 10.04, though this also happens in Ubuntu 9.10, but if i play around with the FPS in 9.10 i can get a balance between audio and video, but with 10.04 doesn't seem to work at all.

When using gtk-recordmydesktop to obviously record my desktop i turn on "encode on the fly", and my recorded video moves too fast for the audio and loses sync, video ends about 2x faster than the audio itself.

If i leave the encode on the fly off, then my video is choppy (less choppy with compiz off) but still a distraction.

my graphics card info is as so:
```
*-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:fc100000-fc1fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
```

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

Any idea? i've had bugs here and there with this graphics card though the basics of ubuntu works with it... its just the small things that pester me..
Hi
on the Advanced Menu change the following Setting
Performance\Frame per Second = 10
enable the following option:
1-encode on fly
2-zero compression
3-quick subsampling
4- full shot at every frame

---

### Post by natema on 2012-06-04
I've tried to fix this for a long time. thank you!

---

