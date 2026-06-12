---
title: "Recording screencasts while using Gnome Shell"
date: 2011-11-05
forum: General Help
---

### Post by robbiemacg on 2011-11-05
Hi,
I'm trying tot record a screencast while using Gnome Shell. It's proving more difficult than you might think.

In the past I've always used **Kazam** to record screencasts ([https://launchpad.net/kazam](https://launchpad.net/kazam)). It's my all time fav.
However, in order to manage/finish a recording in progress, I'd use the GUI you access via Kazam's appindicator. Of course, this indicator's  not visible in Shell's system tray.
I don't think I can manage Kazam via CLI, but maybe I can make some change that'd result in an icon appearing in the Shell tray?
Does any one know of an extension, tool, hack I might use to accomplish that?

While searching for a solution, I've also experimented with running **recordmydesktop** from CLI. This works OK, but, it kills/hides Gnome Shell's system tray for the duration of recording. That's less than ideal.
I'd be just as happy if someone experienced with recordmydesktop could suggest an option to suppress this behaviour.

Thanks very much for your help,
Robbie

p.s. I'm running Gnome Shell on top of an up to date version of 11.10 and have all appropriate sources.

---

### Post by Script Warlock on 2011-11-05
afaik thats how gshell works by hiding some of your activities not like unity but bringing back is by pressing only the win/key.

---

### Post by robbiemacg on 2011-11-05
I appreciate the speedy response, [Script Warlock]("http://ubuntuforums.org/member.php?u=299765"), but I think you've misunderstood the issue I'm experiencing.
It's not that running **recordmydesktop** hides the Desktop, opens the Overview. 
It's that it hides/kills the Gnome Shell System Tray (the area at the top of the screen where applications in focus, time, accessibility options, user, etc. are all displayed). I want this area visible if I'm recording a screencast that's supposed to highlight Shell features and UI.
I'm comfortable using Gnome Shell day-to-day, understand its functioning (and its shortcomings), this is something new.

Thanks

---

### Post by Script Warlock on 2011-11-05
uncheck the outline capture area and reset capture area. is that what you mean?

---

### Post by robbiemacg on 2011-11-06
Not exactly. The Shell system tray isn't just outside of the capture  area (not visible in the resulting screencast), it actually becomes  unavailable to the user for the duration of recording.

I think I'm just going to have to make judicious use of the ffmpeg from CLI for the time being. **Kazam**  is really just a GUI for doing a nice x11grab while recording sound  from your machine's mics, so you can do a voice over on the fly. I can  do that via CLI.

I'm still looking for  away to white list  indicators in the system tray (or convert appindicators to something  that'll show up there).

Thanks

---

### Post by robbiemacg on 2011-11-08
After a few recent updates, I'm actually now able to see this icon (and all similar icons) in Shell's pop up notifications area.
I'm marking this thread solved. I learned a bunch about ffmpeg, and then somebody really solved my problem. Pretty decent if you ask me.

---

