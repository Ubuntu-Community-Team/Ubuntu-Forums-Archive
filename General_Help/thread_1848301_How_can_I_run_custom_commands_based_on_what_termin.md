---
title: "How can I run custom commands based on what terminal profile I am opening?"
date: 2011-09-22
forum: General Help
---

### Post by dmg412 on 2011-09-22
My use case is the following.  I have two terminal profiles, A and B.  When I open each profile, I would like to execute different commands (that are currently in .bashrc) dependent on weather the profile is A or B.  I want to set up different aliases, env vars, as wells as run different commands.  How is this achieved?

---

### Post by patryk77 on 2011-09-22
Not sure how that would work, but check under Edit / Profile Preferences, on the Title and Command tab; you can define a custom command to run for each terminal... 

Might require a small script to launch bash with the proper settings.

Either way, I never tried it :P

---

### Post by dmg412 on 2011-09-22
Yeah, it seems like this way would need to run a script that does your custom profile-specific logic, then run a command that launches terminal with the profile.

It would be much nicer if there was a way to do something similar to the following in your bashrc:

if $PROFILE = A then
   do some A specific stuff
else if $PROFILE = B then
   do some other stuff

Something like this seems like it would be much easier to expand over time and add functionality to.

---

### Post by patryk77 on 2011-09-22
Probably, but GNOME-Terminal doesn't export the profile to a variable, as far as I can't tell.

---

