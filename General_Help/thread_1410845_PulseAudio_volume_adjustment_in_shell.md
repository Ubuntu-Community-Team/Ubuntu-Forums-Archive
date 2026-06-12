---
title: "PulseAudio volume adjustment in shell"
date: 2010-02-19
forum: General Help
---

### Post by eriktheblu on 2010-02-19
So here's my dilemma:
I'm using Mangler and WoW under Wine. Mangler is quiet, WoW is not.

I would like to write a script to adjust the volume of my Wine application (set it to say 50%) and then launch Mangler.

The [CLI page on the PulseAudio wiki]("http://www.pulseaudio.org/wiki/CLI") offers ```
set-sink-volume/set-source-volume

```But I am apparently missing the part of how to apply that to an application.

Can anyone point me in the right direction?



Update: Solved with update to 1.1.2010227

Mangler is awesome

---

### Post by eriktheblu on 2010-02-19
I guess this is due for a bump.

---

### Post by n0dix on 2010-02-19
Try install aumix,
then use: ```
aumix -c +1
```

or amixer.

---

### Post by eriktheblu on 2010-02-20
aumix doesn't look like it would adjust volume for individual applications, just the standard inputs (CD, line, mic, etc.) 

I'm at work currently, but I'll check those out when I get home.

I can use the PulseAudio Volume Control (pavucontrol) GUI to adjust the WoW volume(shows as something like 'ALSA plugin Wine preloader'), but this requires manual manipulation of the slider.

---

### Post by eriktheblu on 2010-02-20
The best I could come up with is
```
pacmd set-source-volume "ALSA plug-in [wine-preloadeoader]" 30000
```
which returns```
Welcome to PulseAudio! Use "help" for usage information.
>>> You need to specify a volume >= 0. (0 is muted, 0x10000 is normal volume)
```

I'm quite perplexed that there is a function that I can do in GUI that I can't seem do in the CLI.

---

### Post by eriktheblu on 2010-02-21
One last bump then I give up.

---

### Post by kostkon on 2010-02-21
You can try the following, although I really don't know if it'll work for sure:

you need to change the cmd that you use to run your wine app (or the command entry of its menu item in your Applications menu, that you need to edit obviously), e.g.:
```
wine ~/.wine/drive_c/Program Files/Mangler/mangler.exe
```
to
```
wine ~/.wine/drive_c/Program Files/Mangler/mangler.exe --property=application.name=Mangler
```
and a separate audio stream for it should appear in the *Applications* tab in *pavucontrol* when you run it. Just select the volume level you want and pulseaudio will remember it.

Hope that helps.

---

### Post by eriktheblu on 2010-02-21
pavucontrol works as you described without modifying the launcher command.
With the launcher as 'wine "d:\World of Warcraft\wow.exe" --property=aplication.name=WoW', pacmd list-clients still returns 'application.name = "ALSA plug-in [wine-preloader]"'

I think I could do this by launching WoW with a volume tag in the command, but this would require restarting WoW every time

The following is an attempt at clarification of intent:
I'm running WoW with Wine.
Mangler is the Linux native Ventrilo VOIP client.
I want to reduce the volume of WoW when I launch Mangler.
When I'm not running Mangler, I want WoW to have normal volume.

I think the most practical thing for me to do at this point is to run Mangler and pavucontrol in the same script and adjust volume manually.

Thanks for the interest.

---

### Post by kostkon on 2010-02-21
> **eriktheblu said:**
> pavucontrol works as you described without modifying the launcher command.
With the launcher as 'wine "d:\World of Warcraft\wow.exe" --property=aplication.name=WoW', pacmd list-clients still returns 'application.name = "ALSA plug-in [wine-preloader]"'

I think I could do this by launching WoW with a volume tag in the command, but this would require restarting WoW every time

The following is an attempt at clarification of intent:
I'm running WoW with Wine.
Mangler is the Linux native Ventrilo VOIP client.
I want to reduce the volume of WoW when I launch Mangler.
When I'm not running Mangler, I want WoW to have normal volume.

I think the most practical thing for me to do at this point is to run Mangler and pavucontrol in the same script and adjust volume manually.

Thanks for the interest.
Misunderstood.

Anyway, you could try [*earcandy*]("http://www.webupd8.org/2009/05/earcandy-is-smart-pulseaudio-volume.html").

---

### Post by eriktheblu on 2010-02-22
> **kostkon said:**
> Misunderstood.

Anyway, you could try [*earcandy*]("http://www.webupd8.org/2009/05/earcandy-is-smart-pulseaudio-volume.html").
That looks quite promising.
I'll check it out tonight. Thanks.

---

### Post by ekilfoil on 2010-02-28
> **eriktheblu said:**
> pavucontrol works as you described without modifying the launcher command.
With the launcher as 'wine "d:\World of Warcraft\wow.exe" --property=aplication.name=WoW', pacmd list-clients still returns 'application.name = "ALSA plug-in [wine-preloader]"'

I think I could do this by launching WoW with a volume tag in the command, but this would require restarting WoW every time

The following is an attempt at clarification of intent:
I'm running WoW with Wine.
Mangler is the Linux native Ventrilo VOIP client.
I want to reduce the volume of WoW when I launch Mangler.
When I'm not running Mangler, I want WoW to have normal volume.

I think the most practical thing for me to do at this point is to run Mangler and pavucontrol in the same script and adjust volume manually.

Thanks for the interest.

You could use the latest mangler developer snapshot and increase the master volume control in mangler :)

---

### Post by eriktheblu on 2010-03-04
> **ekilfoil said:**
> You could use the latest mangler developer snapshot and increase the master volume control in mangler :)

Awesome, I'll try it out. The jukebox looks exciting too.

Earcandy was a great concept and probably would have fit the bill, but I couldn't get it to behave. It kept minimizing all volume, then it would crash.

---

