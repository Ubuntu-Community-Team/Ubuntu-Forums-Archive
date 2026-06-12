---
title: "running audio clips in Crontab"
date: 2011-07-20
forum: General Help
---

### Post by moverlin on 2011-07-20
I have a question regarding crontab.  I have opened crontab -e.  I have typed the following command to make a .flac audio file play:

48 13 29 7 3 cd /home/moverlin/Desktop/folder1/folder2/ && mplayer "audio_file1.flac" && cd $home

So, if I schedule a task to run today at:
some_hour:some_minute, the task seems to actually be executed/run from
some_hour:some_minute:01.00 to some_hour:some_minute:02.00.
^^Perhaps those times aren't accurate.   Nonetheless, my point is that the task is executed in that 1 second  interval.

Is there some addition I can make to the single line above which will allow the audio file to play for all x seconds that is the length of the file?
Or...is there something else I can do to fix this problem?

Thanks!

---

