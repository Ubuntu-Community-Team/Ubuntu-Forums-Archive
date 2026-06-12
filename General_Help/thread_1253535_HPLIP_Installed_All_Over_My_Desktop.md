---
title: "HPLIP Installed All Over My Desktop"
date: 2009-08-30
forum: General Help
---

### Post by ttoolin on 2009-08-30
Hi folks-

I really goofed, somewhere . . .

I went to the HP website, and downloaded the newest copy of the HPLIP software.  Following the instructions they provided, it works, but now I have about a zillion files on my desktop.  I think I know what I can do to fix it, but I wish the assistance of someone more knowledgeable, before I totally trash my system.  The details are . . .

The downloaded file was: hplip-3.9.8.run

The website suggested the following in a terminal after changing the directory to the Desktop (cd Desktop):
```
sh hplip-3.9.8.run
```
I did this, but put 'sudo' in front of it, to run it as superuser.

The command started running, and then gives me a warning that I am running this as a superuser, and that the *HIGHLY RECOMMEND* not doing that.  I opted to abort the task, with the prompt provided, and reran it out of superuser mode.

I was watching the screen while it ran, and I saw, but did not act on, a couple of lines that passed on the screen which said it could not open folders (permission denied).  I suspect that is the origin of my problems.

My questions are:  Can I fix the mess on my desktop by starting nautilus as a superuser in the terminal, and simply send all of the files on the desktop to the trash???

After I clean up the desktop, can I successfully install the HPLIP software by doing so as a superuser, and ignoring the warning the program will give me that I am running it as a superuser???  Running it as superuser should give the program permission access to the directories it wishes to use.

Thanks for the help!

terry

---

