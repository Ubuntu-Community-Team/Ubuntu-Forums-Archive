---
title: "Using amixer to set volume via the terminal"
date: 2010-01-05
forum: General Help
---

### Post by Altay_H on 2010-01-05
I'm interested in writing a script that increases the volume linearly. Before Ubuntu 9.10 this was relatively simple. I could place "amixer set Master 1+" inside a loop which would iterate the necessary number of times. With the advent of Karmic, however, the sound controller on the panel now modifies both Master and PCM.

From what I can tell it exhibits the following behavior:
1. At full volume Master and PCM are both 100%
2. If the volume is decreased PCM is decreased and Master remains at 100%
3. Once PCM reaches 74% it remains constant and decreasing the volume lowers Master
4. Once Master reaches 0% it remains constant and decreasing the volume lowers PCM
5. At no volume Master and PCM are both 0%

I'm sure this behavior is indeed an improvement for most users, but it complicates my script. I could write my script to do exactly what I outlined in the above steps, but I suspect I may be overcomplicating such a simple task. Is there an easier way to do this? Thanks for any help.

---

### Post by kostkon on 2010-01-06
You could use the [CLI]("http://pulseaudio.org/wiki/CLI") of PulseAudio to modify the volume of the default sink, instead of trying to directly access and modify the PCM and Master volumes.

---

### Post by Altay_H on 2010-01-06
Thanks for your response, but I'm confused by how using PulseAudio will simplify my script. Based on what I gathered from reading over the page you linked the command "pulseaudio -nF set-source-volume input 65536" should set the volume to 100%. Unfortunately it gives me the following error instead:
```

E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

Thanks for your help.

---

