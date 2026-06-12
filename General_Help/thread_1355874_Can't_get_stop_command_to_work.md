---
title: "Can't get stop command to work"
date: 2009-12-15
forum: General Help
---

### Post by Talistan on 2009-12-15
Hello, and thanks for reading:
I am running a program and in the shell I do

alex@alex:~$ jobs -l
[1]+  2590 Running                 brasero &

I can use `kill' with a stop signal to stop it and then start it again, but in the tutorials I am looking at it speak of the stop command which I only find the man pages for. 

alex@alex:~$ stop  2590
stop: Unknown job: 2590

but the man stop pages are the same for initctl
alex@alex:~$ initctl stop 2590
initctl: Unknown job: 2590

So I am confused about how to get these commands to work, if I am able to read the man pages correctly. I would like to learn how to use these commands that are available to do the purpose of kill as well.

All the best and thanks.

---

