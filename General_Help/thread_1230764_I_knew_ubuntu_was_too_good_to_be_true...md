---
title: "I knew ubuntu was too good to be true.."
date: 2009-08-03
forum: General Help
---

### Post by Codix121 on 2009-08-03
Sigh I need some help,
I'm starting to get very weary of linux,
I loved it at first, but now it seems I'm on these forums
24/7, problem after problem... so much for stability...

anyways, 
well I need help with my sound,
I just spent the last 2 hours, finally
getting my webcam to work. 

and now I'm trying to get my headphone jack working,
here is my output on 
```
cat /proc/asound/card0/codec#* | grep Codec
```

Result:

```

Codec: Realtek ALC861-VD
Codec: LSI ID 1040

```

I tried the PulseAudio option,
it did nothing except stop ALL sound from working all together,
Uhm the only way I could get my sound fully working was with
"ALSA OSS"
which is what all my settings are set to now,
and it seems to be the only one that works.

but my issue now,
is that my headphones dont work,
which is annoying, since I can't hook up my speakers...
it's very frustrating,
and I've been searching and searching and no answer in sight..
I'd really like to get my headphones working..

Ubuntu is on my last string...
I mean windows was bad... but atleast simple issues
such as a headphone jack worked :(

Someone please help me :(

EDIT:

Oh and I also downloaded the latest Drivers, Utilities and Lib from the Alsa Website,
and installed it but it made no difference in either Alsa or Alsa OSS or Pulseaudio.
So they are update to the latest but headphones still don't work.

---

### Post by jmszr on 2009-08-03
Codix121,

Have you tried using the alsamixer? It's in the repositories, gnome-alsamixer, also alsamixergui. Just a thought.

---

### Post by Codix121 on 2009-08-03
yeah I have all that installed and still no luck,
I've tried all sorts of solutions,
but support on these forums aren't very good, no offense,
I've asked several questions often with only one lousy answer lol....

but yes I have installed it and it didn't seem to help my case.

---

### Post by jmszr on 2009-08-03
Codix,

In Tutorials and Tips I found this: [http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa)  (ALSA Upgrade Script) , if you haven't seen it yet. Then for whatever use these might have: [http://ubuntuforums.org/showthread.php?t=1229804&highlight=alsa](http://ubuntuforums.org/showthread.php?t=1229804&highlight=alsa)  and: [http://ubuntuforums.org/showthread.php?t=789578&highlight=alsa](http://ubuntuforums.org/showthread.php?t=789578&highlight=alsa) .

You probably have already seen these, but on the off-chance that you haven't....

---

### Post by Azuu on 2009-08-03
> **jmszr said:**
> Codix,

In Tutorials and Tips I found this: [http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa)  (ALSA Upgrade Script) , if you haven't seen it yet. Then for whatever use these might have: [http://ubuntuforums.org/showthread.php?t=1229804&highlight=alsa](http://ubuntuforums.org/showthread.php?t=1229804&highlight=alsa)  and: [http://ubuntuforums.org/showthread.php?t=789578&highlight=alsa](http://ubuntuforums.org/showthread.php?t=789578&highlight=alsa) .

You probably have already seen these, but on the off-chance that you haven't....
thanks I just asked the question that you answered at the third link.:)

---

### Post by ninjapirate89 on 2009-08-03
I can't help with your problem, but I wanted to say don't give up on Ubuntu. In my experience it's far less troublesome than xp or vista.

---

### Post by Azuu on 2009-08-03
> **ninjapirate89 said:**
> I can't help with your problem, but I wanted to say don't give up on Ubuntu. In my experience it's far less troublesome than xp or vista.

Vista yes, Xp no. Xp has general troublesome issues that irritate, *butnu fixes this by having short bursts of monitor-out-the-window-syndrome:D

---

### Post by ninjapirate89 on 2009-08-03
> **Azuu said:**
> Vista yes, Xp no. Xp has general troublesome issues that irritate, *butnu fixes this by having short bursts of monitor-out-the-window-syndrome:D

When I had to reinstall xp on my laptop before I switched to Ubuntu, xp didn't even have my ethernet port working properly, I had no way to even download the proper driver for it. Don't get me started on the problems I had with the wireless. When I installed Ubuntu both ethernet and wireless (along with everything else for that matter) worked right away without any configuring. I actually had less trouble reinstalling Vista on my desktop than I did with xp. That's just my experience though. I know for some people Ubuntu gives them a lot of trouble.

---

