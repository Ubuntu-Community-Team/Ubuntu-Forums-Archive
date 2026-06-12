---
title: "processes persisting beyond user session"
date: 2010-08-14
forum: General Help
---

### Post by sirjasonr on 2010-08-14
Hello,
I am wondering whether there's an easy way to make processes continue beyond the current session without being terminated when the terminal window, ssh session or gnome/kde session is closed.

The reason I would like to know this is that I often run quantum mechanical calculations using the software package GAMESS on my personal computer (6 cores). Often these jobs take from hours to days to complete, so I have them running in a terminal window as I go about my other business. I do, however, want to be able to launch them remotely by SSH when I am not at home, but it would be impractical to leave the SSH session open until the job completes.

I have used PBS queuing systems before, but are these things appropriate to run on workstation computers? Sounds like overkill to me... All I want is to be able to write a script that doesn't exit when my terminal does.

Any suggestions?

Cheers,
Jason

---

### Post by kidders on 2010-08-15
Hi there,

Assuming your script doesn't need access to an X server, you have two options.

You could run your script in the background. For example, if you log into your machine over SSH, run **sleep 60 &**, log out & back in again, you'll notice the process is still running. There are lots of reasons this can get awkward, but it's nice & simple, and does the job if you're happy to redirect any interesting output to a file, and lose the ability to interact with the process after you terminate the terminal session that initiated it.

Something like **find / -size +10M > ~/big_files &** fits the bill. It's time-consuming, requires no interaction, and the output is just as handy in a file as anywhere else.

---

Alternatively, if you need something more elaborate, you could try screen (a console "window" manager). It does lots of nice stuff, but the feature you'd be most interested in is the ability to detach a process from your terminal session.

For example, you could start screen, run something like **ctorrent -s whatever -p 6881 huge_file.torrent**, wait a while to make sure it gets going, and hit [CTRL]+A d to detach it. You can get it back by running **screen -r** to restore your session.

If you want, you can start a whole *collection* of processes & re-attach them to your terminal as a group, later ...

[LIST]
[*]Start screen.
[*]Run your script.
[*]Hit [CTRL]+A c to create a second session.
[*]Run your script again with different arguments.
[*]Hit [CTRL]+A d and log out of the server. Both processes carry on running.
[*]Log back in again.
[*]Run **screen -r**.
[*]Hit [CTRL]+A twice to toggle between the two instances of your script.
[/LIST]

I hope that helps.

---

### Post by sirjasonr on 2010-08-17
For some reason I was under the impression that the processes run in the background using **&** were killed when the session is closed... But I guess I was mistaken.

In any case, you're advice regarding **screen** is excellent. Thanks you very much for sharing! I appreciate it very much!

Jason ):P

---

