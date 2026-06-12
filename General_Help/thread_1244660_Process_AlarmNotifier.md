---
title: "Process Alarm/Notifier"
date: 2009-08-19
forum: General Help
---

### Post by newbie_1 on 2009-08-19
Hi,
I wanted to know if there's any way i can get notified as soon as a particular process is terminated. Basically, I am am running a code which takes several hours. So I wanted an alarm which is activated as soon as the process is completed or terminated.

---

### Post by approaching on 2009-08-19
in your command you could do something like this:
my -really /long/command && espeak "everything is finished, everybody can go home now! everything is finished, everybody can go home now! everything is finished, everybody can go home now! everything is finished, everybody can go home now! everything is finished, everybody can go home now! everything is finished, everybody can go home now!"

then ctrl+c it when you hear that it is done

---

### Post by newbie_1 on 2009-08-19
@approaching: I tried this command. Didn't work on my OS. You really got some special OS if that works for you. :P.

---

### Post by approaching on 2009-08-19
espeak comes with ubuntu by default, so this is what i was trying to get you to do:

whatever your command was && espeak "some stuff"

so if your command was like "ls -R /" which would take a while, do this:

```

ls -R / && espeak "i finished the job"

```

the && says that the second command should be completed right after the first. espeak is ubuntu's default text to speach synthesizer, it's a lot of fun to play with, but you could put in any other command that would let you know that it finished.

---

### Post by newbie_1 on 2009-08-19
Oh!.. Sorry.. I thought you were mocking me .. :P.. Anyways... thanks for the help.. it did work :)..

---

### Post by approaching on 2009-08-19
we all have special os's around here.

and that is a pretty common type of format to give examples in. you will probably see a lot of my-command -options /directory/to/your/source/file /destination/file etc, so try and think in generals.

and seriously, ssh into a box and use espeak, soooo much fun.

---

### Post by newbie_1 on 2009-08-19
yeah.. I guess we have .. and espeak surely is fun.. :) thanks again.. just made it read lyrics of a song :D .. and trying to ssh seems to be a nice idea as well

---

