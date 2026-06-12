---
title: "autolaunching banshee when audio player is connected"
date: 2010-08-24
forum: General Help
---

### Post by kiddykoff on 2010-08-24
i had nautilus configured to autolaunch rhythmbox when i plugged in my ipod, but i've installed banshee now.

I want banshee to launch but when i am prompted the dropdown box is grayed out saying no applications found.

can anyone take the time to help me out?

---

### Post by micheledm on 2010-08-25
Did you installed Banshee using the repository?

Can you see it under System->Preferred Applications?

---

### Post by kiddykoff on 2010-08-25
it's coming from LP-PPA-banshee-team-banshee-daily/lucid

it is listed and is set as my preferred application

and i just upgraded it. I used synaptic though as it was being held back using apt-get.

It's probably unrelated but i do have a autorun script on it.

---

### Post by kiddykoff on 2010-08-31
bump

---

### Post by kiddykoff on 2010-10-23
alright i had an auto launch script working for me for a while. it was

#!/bin/bash
scrobblethis .scrobbler.log &&
banshee-1

since i upgraded to 10.10 something has went wrong. Now when i run the script an error message tells me "Cannot find the autorun program"

I've rewrote the script with gnome-terminal:

#!/bin/bash
gnome-terminal

I'm still getting the same error message. I went to my bin folder and bash is there, so what's not being found?

---

