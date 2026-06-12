---
title: "Slow response after audio change"
date: 2009-11-01
forum: General Help
---

### Post by crosstalk on 2009-11-01
I just got a new headset with headphones and a microphone. I was working with audio settings to get capture from the microphone working (I was using sound recorder to test it.) I eventually ran across an article ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)) that told me to add "options snd-hda-intel model=6stack-dig" to the end of /etc/modprobe.d/alsa-base.conf, which I did.

I then rebooted, but it didn't work. However, it had a side effect, so I removed it and rebooted again. This side effect persisted, and I later was able to get the microphone working correctly.

This side effect is that all the menus are slow. If I go and click "Applications" in the menu, it takes a couple seconds for the menu to load. Moving my mouse cursor around, the item I am hovering over does not highlight (change orange) for a couple seconds, and it takes a couple seconds for a click to open another sub-menu. In Firefox, too, the menus are slow. Also, drop-down boxes are slow (I discovered this while posting this thread.)

In the Sound Recorder application, however, once I hit "Record" or "Stop," I usually have to wait a few (several) seconds for anything to happen. I do not recall whether it was like this before.

Does anyone have advice on how to restore my system's normal responsiveness?

Any help is appreciated.

EDIT: I forgot to report that, according to "top", nothing is draining my processor more than normal.

---

### Post by crosstalk on 2009-11-02
Sorry for double-posting, but can anyone help?

A minute ago, it took me 30 seconds to open the "System" menu, I thought it had completely crashed. I hope it's not getting worse with time.

Thank you for any halp.

---

### Post by crosstalk on 2009-11-03
Sorry to post again, but can I get some help?

The menus are becoming less and less responsive, and some are no longer opening correctly (to get a terminal, I have to open Applications -> Programming, then move my pointer up to Games and step up slowly twice before the Accessories menu will open.)

Thank you for any assistance.

---

### Post by skylark on 2009-11-03
Yes this certainly sounds like an odd bug.

Do the menus speed up after they initially load? If so then it could be that you've struck a bug where your HDD access has become very slow (since the menus load all the icons when fired up for the first time). You may want to test your HDD speed "sudo hdparm -tT <HDD device>", e.g. "sudo hdparm -tT /dev/sda". Buffered disk reads of most modern HDDs are usually >30MB/s

Are mouse movements slow? What about mouse-clicks in general... are mouse-clicks responsive in general (excepting the context menus?) Is the keyboard responsive?

Do you have a dual-screen setup?

Some random suggestions that might help:
1) Try disabling Compiz (if it is same as in Jaunty then you can do this by selecting "None" in the System->Preferences->Appearance->Visual Effects tab).
2) Check your system logs for anything strange going on (e.g. "tail -100 /var/log/syslog" and look for very rapid similar messages, also look for anything odd in "dmesg" output).
3) Check you are not near 100% disk-usage "df -h"

Of course there is also the thermo-nuclear option of a complete re-install! Maybe others have other suggestions since I'm just stabbing in the dark at the moment.

---

### Post by crosstalk on 2009-11-03
I don't currently have any time to do testing, but here's what I have off the top of my head:

The menus do not speed up/stay responsive after one load.

My mouse and keyboard both otherwise respond fine.

I do have a dual-screen setup.

I use Compiz Fusion (IIRC) for its effects.

I am near 100% disk usage (the 30GB max of Wubi.)

Thank you for your help, will do more testing when I have time.

---

### Post by A_Hole_Marcus on 2009-11-04
I've been having the same issue since using Jaunty... Everything worked fine for a long while, but a couple of months before the release of Karmic, I saw the same behavior in Jaunty.

I have Karmic now... Same issue with the menus and stuttering video... Like a system wide slowdown (but most noticeable with the slow menus and "skipping" mouse cursor).

I also experienced this on Kubuntu (9.10).

In my case, I THOUGHT it may have been a problem with Pulse Audio or even ALSA... Removed them both and using OSS, but still have this issue.

Seems to come up when I view flash video in Firefox AND when I tamper with audio settings (as in the multimedia selectors)

What's odd is that it persists through reboots... SOMETIMES...

Sometimes the system is fine... sometimes the "slowdown" lingers even after reboots.

Now that I saw mention of disabling Compiz... the system responsiveness is back...

SO... I guess it must have something to do with one of the more recent releases of Compiz... Since I've been dealing with this on and off through both 9.04 and 9.10.

Not sure what Compiz would have to do with audio processing in Ubuntu... BUT, I'll follow the thread and post again if the problem isn't isolated to Compiz disrupting the audio, or if I see anything else relevant.

---

### Post by A_Hole_Marcus on 2009-11-04
Think this actually may have been an Nvidia driver issue.

I'd been shifting back and forth between version 185 and (I think) 192... Whatever the latest ones are, and have had the same problem. I just didn't think to revert to older video drivers for what I assumed was an audio problem.

But going back to Nvidia version 173 has fixed all the problems with system slowdowns. Compiz is back on and using ALSA again with no problems.

Hope it helps.

---

