---
title: "Weird alsamixer/gnome-terminal bug"
date: 2011-05-28
forum: General Help
---

### Post by Claritux on 2011-05-28
I've discovered a very weird bug in natty occurring after the following:
1. Run alsamixer in terminal
2. Open Sound Preferences from the sound menu
You should now see 4-5 terminal windows constantly opening and closing themselves. I was hoping someone could file a bug report for me since I'm not used to do so myself/investigate if there already exists a bug report.
BTW: You have to log out in order to get rid of the terminal windows.

Edit: Seems like a terminal window opens every time I open sound preferences, so I'm starting to think this has something to do with my own setup. Also I can't use the volume sliders under the "programs"-tab in sound preferences and there is an entry there saying "speech-dispatcher". Help! :S

Edit 2: The problem seems to go away when I uninstall "speech-dispacher" and I was a little too quick when concluding that I couldn't use the volume sliders. The "problem" was that I had the master volume muted. Boils down to a terminal window that won't go away if I open sound preferences with "speech dispacher"-installed.

Edit 3 (sorry): Seems like I only have to uninstall "gnome-orca" (witch depends on "speech-dispatcher")

---

