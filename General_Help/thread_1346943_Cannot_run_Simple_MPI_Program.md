---
title: "Cannot run Simple MPI Program"
date: 2009-12-05
forum: General Help
---

### Post by start_game316 on 2009-12-05
Hello there, here is the deal, I compiled a simple MPI program using something like this: mpicc -o hello hello.c 

Running Program:
root@ahmed-laptop:~# mpd &
[1] 20137
root@ahmed-laptop:~# mpirun -np 2 '/home/ahmed/Desktop/hello' 
[mpdcon]: mpirun for the ch_p4mpd device, and other mpd commands,
[mpdcon]: require an mpd to be running on the local machine
[mpdcon]: See the Installation and User Guides for how to start mpd's
[mpdcon] local_connect failed to connect to an mpd: : -1 | strerror: No such file or directory: No such file or directory

How does it require mpd to be running after I typed the "mpd &" line??

Any clue anyone?

---

