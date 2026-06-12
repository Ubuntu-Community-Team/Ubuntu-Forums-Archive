---
title: "Google voice on aspire one - can you here me now?"
date: 2010-10-27
forum: General Help
---

### Post by trikster_x on 2010-10-27
Hi everyone.  I was wondering if anyone has gotten the built-in microphone on an AOA150 to work successfully with the google-voice feature of google-talk.  I read around and found that the application uses auto-leveling that isn't exactly friendly with the aspire one's mic.  There used to be a fix involving editing a line in the options file for google-talk, but that file has since been removed.  Has anyone gotten this working recently, or am I just out of luck here?

---

### Post by trikster_x on 2010-10-28
Okay, so I got it up and running.  What I had to do is create a file in /home/user_name/.config/google-googletalkplugin named "options".  Add a line to the file:
```
audio-flags=1
```

Then I had to install pavucontrol, go to the input device tab, unlock the sliders, mute the left channel and adjust the right channel to a decent volume.  Restart the web browser and like magic it works :D

---

