---
title: "Rsych Logging"
date: 2009-09-21
forum: General Help
---

### Post by Kayone on 2009-09-21
Hello~

Apparently I am confused about rsync logging. Is there any way I can keep rsync from displaying the files it has checked? I only want the log file to show the files that were actually sync'd (*edit: prob a poor choice of words.. when I say sync'd, I mean I only want to display the src files that have changed. I am trying to pull data from src to dst so i can run some scripts on a non-production network.) 

I am not concerned with debugging. I want to run a post process that utilizes the log file to process all new files.

For instance:

A --|--
B ---> B
C ---> C
D ---> D

If there were no changes in A, I don't want a log file that lists it. 
I am currently using the rsync -rvte options currently..

I am wondering if someone knows how to take advantage of the "--itemize-changes" and/or "--out-format=FORMAT" options. 
Your help would be greatly appreciated.

---

### Post by Kayone on 2009-09-21
Looks like I'm going to probably need to AWK it. Meh! Thanks for those of you that looked at my post and thought about it for a second(+). 

I am still interested in the answer if someone comes up with it at a later date. I think I spent enough time trying to find a solution to a problem I already knew an answer to :)

I was determined to find the functionality already built into rsync. It seems like such a common task request to only show the directory updated?!?!? O-well, back to the drawing board.

Thanks Forum'ers..
-K1

---

### Post by StuartN on 2009-09-21
> **Kayone said:**
> Looks like I'm going to probably need to AWK it. Meh!

I'm confused - I use rsync > backup.log and the file only contains a list of changed, copied files. It does not list any file that was checked and found to be the same.

Occasionally an unmodified file is copied again because the times on the source and destination are fractionally different, which is a little quirk of using ext3 on one and xfs on the other.

---

### Post by Kayone on 2009-09-21
Thanks for replying Stuart,

> **StuartN said:**
> 
Occasionally an unmodified file is copied again because the times on the source and destination are fractionally different, which is a little quirk of using ext3 on one and xfs on the other.

Technically it is only showing the "files" that are new. The problem is that it also shows the directories that it is checking (even if no files are modified).

For instance--> If D.txt was the only file that changed, my log file is showing D.txt in the logs as well as E/F/G. 

A/B/C/D.txt

E/F/G/H.png

Technically, it is only showing the files. I just want to leave out the unnecessary directories. I am already needing to utilize grep so I can limit what I am parsing after rsync has done it's job. Currently, rsync is trying to make me parse too much. It is parsing everything in A/B/C/* and E/F/G/*   ; ;

---

### Post by StuartN on 2009-09-21
> **Kayone said:**
> For instance--> If D.txt was the only file that changed, my log file is showing D.txt in the logs as well as E/F/G.

My log file only contains lines with "path/file.ext" and "deleting path/file.ext". It does not show the directories it is parsing, nor any files except those that have changed.

It is too late at night to think, but if it is purely a matter of stripping off the path, then does either basename or the ${path/file.ext} syntax help? For instance, ${f%.*} strips the extension from path/filename f, or $(basename $f) strips the path.

---

### Post by Kayone on 2009-10-06
Hey Stewart, I just wanted to say thank you for your assistance. I got my script running the way I wanted it to. I really appreciate your time.

/bow

-k1

---

