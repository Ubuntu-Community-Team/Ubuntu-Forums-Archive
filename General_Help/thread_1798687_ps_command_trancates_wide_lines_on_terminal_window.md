---
title: "ps command trancates wide lines on terminal window"
date: 2011-07-06
forum: General Help
---

### Post by rpaskudniak on 2011-07-06
Hi Family.

This is not a question, just a way to share a minor concern and raise the issue.

Here's an interesting couple of screenshots.  I am running an grsync at the moment (in background) and I wanted to see the entire rsync commands that are running.  Simple enough: ```
ps -f
```Right?

Well, not so fast.  Here's what I got on a 80-column Terminal window:
[SIZE="1"][FONT="Lucida Console"]rasputin@maxwell:~$ ps -f
UID        PID  PPID  C STIME TTY          TIME CMD
UID            PID  PPID  C STIME TTY          TIME CMD
rasputin      4321  4315  0 12:49 pts/1    00:00:00 bash
rasputin      5936  4321  1 12:52 pts/1    00:00:27 /usr/bin/grsync
rasputin      5966  5936  2 12:57 pts/1    00:00:45 rsync -r -t -p -o -g -x -v --pro
rasputin      5968  5966  0 12:57 pts/1    00:00:00 rsync -r -t -p -o -g -x -v --pro
rasputin      5969  5968  3 12:57 pts/1    00:00:58 rsync -r -t -p -o -g -x -v --pro
rasputin      8451  4321  0 13:23 pts/1    00:00:00 ps -f[/FONT][/SIZE]

Now, I **know** the rsync command line is longer than that.  So I ran the same command and piped it through cat.  Now I got:

[SIZE="1"][FONT="Lucida Console"]jake@maxwell:~$ ps -f | cat
UID        PID  PPID  C STIME TTY          TIME CMD
rasputin      4321  4315  0 12:49 pts/1    00:00:00 bash
rasputin      5936  4321  1 12:52 pts/1    00:00:27 /usr/bin/grsync
rasputin      5966  5936  2 12:57 pts/1    00:00:45 rsync -r -t -p -o -g -x -v --pro
gress -u -l -H -b -s /media/Media/Music/ /media/FreeAgent GoFlex Drive/Music-Backup/
rasputin      5968  5966  0 12:57 pts/1    00:00:00 rsync -r -t -p -o -g -x -v --pro
gress -u -l -H -b -s /media/Media/Music/ /media/FreeAgent GoFlex Drive/Music-Backup/
rasputin      5969  5968  3 12:57 pts/1    00:00:58 rsync -r -t -p -o -g -x -v --pro
gress -u -l -H -b -s /media/Media/Music/ /media/FreeAgent GoFlex Drive/Music-Backup/
rasputin      8452  4321  0 13:23 pts/1    00:00:00 ps -f
rasputin      8453  4321  0 13:23 pts/1    00:00:00 cat
[/FONT][/SIZE]

I also tried it with an ls -l command, which wraps without piping to cat.  I'm not about to start testing a godzillion commands to see which will wrap and which will not.  I just found it curious that the ps -f command truncated its output without comment.  So curious that I did the following experiment:
On an 80-character-wide terminal I typed: export "COLUMNS=150" and ran the same ps -f command.

It wrapped.

This tells me that the ps command gives a hoot about the terminal type and configuration, that if stdout is a terminal it will look at COLUMNS and truncate lines accordingly.

I happen to think this is a bad idea.  Anyone agree?  I don't know if this has always been part of ps on Ubuntu; it certainly isn't on other OS's.

---

