---
title: "Cron or schedule the execution of playlists w/ bmp ?"
date: 2006-03-18
forum: General Help
---

### Post by glave on 2006-03-18
I've got an old laptop running breezy for the purpose of streaming music for my bedroom. I'd love to find a way to schedule it to 'change channels' during different parts of the day... IE- 6am it changes to an easy listening station, 10am to a rock station, 10pm to a classical station, etc...

By default beep plays my playlists and shoutcast streams, so how could I tell bmp to kick them off? I thought of trying a cronjob to just execute the playlist, but then realized that this ISN'T windows and that would fail as the playlist isn't an executable.

Any thoughts or ideas?

---

### Post by dcstar on 2006-03-18
[QUOTE=glave]I've got an old laptop running breezy for the purpose of streaming music for my bedroom. I'd love to find a way to schedule it to 'change channels' during different parts of the day... IE- 6am it changes to an easy listening station, 10am to a rock station, 10pm to a classical station, etc...

By default beep plays my playlists and shoutcast streams, so how could I tell bmp to kick them off? I thought of trying a cronjob to just execute the playlist, but then realized that this ISN'T windows and that would fail as the playlist isn't an executable.

Any thoughts or ideas?[/QUOTE]
Playlists may not be executable, but the program that runs them is.

Look at the man page for that program, and then experiment with a script until it does what you want, then get cron to run the script.

---

