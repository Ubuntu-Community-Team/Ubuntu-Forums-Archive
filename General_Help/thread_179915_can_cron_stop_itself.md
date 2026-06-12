---
title: "can cron stop itself?"
date: 2006-05-21
forum: General Help
---

### Post by evaristegalois on 2006-05-21
Here is my assignment: I want to do a scheduled recording of audio streaming (Austrian Public Broadcasting, if you are interested). I know how to start this process as a command on the command line with mplayer (mplayer -dumpfile out.rm -dumpstream [www.stream.address)](www.stream.address)). I can figure out how to make cron start my recording (I am in North America, and the good stuff in Austria is in the middle of the night, of course) but how can I make it stop the recording? By hand I would just press Ctrl-c. Any ideas? Thanks, --evaristegalois [ps. using ubuntu breezy]

---

### Post by Denis on 2006-05-21
If you use the command "killall mplayer" mplayer will be shut down, just like you would press ctrl-c. 

Add this command to your cron job at the appropriate time and see how it works out.

---

