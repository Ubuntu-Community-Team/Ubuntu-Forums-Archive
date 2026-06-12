---
title: "cleaning up a log file"
date: 2011-11-13
forum: General Help
---

### Post by ctoon6 on 2011-11-13
i have a log file with several thousand lines and i would like to remove specific lines, and only output parts of the lines that do not match the above criteria.

this is some example text of the log file

> "pixelvis_debug"

 client

 - Dump debug info

"rope_subdiv" = "2" min. 0.000000 max. 8.000000

 client

 - Rope subdivision amount

"rope_collide" = "1"

 client

 - Collide rope with the world

"rope_smooth" = "1"

 client

 - Do an antialiasing effect on ropes

"rope_smooth_enlarge" = "1.4"

 client

 - How much to enlarge ropes in screen space for antialiasing effect

"rope_smooth_minwidth" = "0.3"

 client

 - When using smoothing, this is the min screenspace width it lets a rope shrink to

"rope_smooth_minalpha" = "0.2"

 client

 - Alpha for rope antialiasing effect

"rope_smooth_maxalpha" = "0.5"

 client

 - Alpha for rope antialiasing effect

"rope_wind_dist" = "1000"

 client

 - Don't use CPU applying small wind gusts to ropes when they're past this distance.

"rope_averagelight" = "1"

 client

 - Makes ropes use average of cubemap lighting instead of max intensity.

"cl_rumblescale" = "1.0"

 client archive

 - Scale sensitivity of rumble effects (0 to 1.0)

"cl_debugrumble" = "0"

 client archive

 - Turn on rumble debugging spew

"mp_usehwmvcds" = "0"

 client

 - Enable the use of the hw morph vcd(s). (-1 = never, 1 = always, 0 = based upon GPU)

"soundscape_fadetime" = "3.0"

 client cheat

 - Time to crossfade sound effects between soundscapes

"cl_soundscape_flush"

 client cheat server_can_execute

 - Flushes the client side soundscapes

"playsoundscape"

 client cheat

 - Forces a soundscape to playi would like to automatically omit lines that do not start with a quote.
and the lines that do begin with a quote i would like to only have the contents of the first set of quotes output to a file.

i was able to do the first thing by doing grep -v '^ ' log.txt > log2.txt

that gets rid of most of the undesirable lines, but others still start with a letter so they are not removed, how do i just keep lines starting with a ".

thanks for any help.

edit: i was able to only keep lines starting with '"' by doing grep '"' log.txt > log2.txt

---

### Post by jonkiribati on 2011-11-13
you can use cut for that for example cut -d'=' -f1 that means if we have this "text1" = "text2" it'll split that into 2 fields and get the first field which is "text1"

---

### Post by ctoon6 on 2011-11-13
> **jonkiribati said:**
> you can use cut for that for example cut -d'=' -f1 that means if we have this "text1" = "text2" it'll split that into 2 fields and get the first field which is "text1"

thanks, worked like a charm

---

