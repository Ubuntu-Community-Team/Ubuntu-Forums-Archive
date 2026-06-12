---
title: "Time stamping stdout"
date: 2011-05-21
forum: General Help
---

### Post by rhdinah on 2011-05-21
I would like to try to take the stdout of a long-running command, e.g. rsync, and place a timestamp [date] on the beginning of each line of stdout as a trace of progress. For example:

[output of rsync]:
a.mp3
b.mp3
c.mp3
d.mp3

[and create a new output stream]:
Sat May 21 15:51:13 PDT 2011 a.mp3
Sat May 21 15:52:23 PDT 2011 b.mp3
Sat May 21 15:53:33 PDT 2011 c.mp3
Sat May 21 15:54:43 PDT 2011 d.mp3

I know how to do this in bash with simple echos, but the bit with a stdout is a different story.

Any ideas would be appreciated! Thanks! :KS

---

### Post by AlphaLexman on 2011-05-21
You might need to utilize the 'stat' command to incorporate the 'date' command with the 'mv' or 'cp' commands to get the results you desire.

---

### Post by rhdinah on 2011-05-21
No, I don't think the stat command is what I wanted ...

But I did manage to solve this myself. I thought I'd be plummeted into the depths of awk programming, but the solution was considerably simpler.

Solution: where the code between the curly braces simulates the output of a long running command.

{ ls -l; sleep 4; ls -l; } | while read line; do echo `date` "${line}"; done

Each line is properly time stamped. :D

---

