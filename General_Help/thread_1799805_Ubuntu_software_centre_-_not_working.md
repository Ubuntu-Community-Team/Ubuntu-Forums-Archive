---
title: "Ubuntu software centre - not working"
date: 2011-07-08
forum: General Help
---

### Post by mrmjtudor on 2011-07-08
I can open the software centre but it doesn't load any options - simple a titled blank box
any ideas?

---

### Post by ArrrghJ on 2011-07-08
Bump.

I'm having the same issue in Ubuntu. Came here hoping to find answers...

---

### Post by flipper T on 2011-07-08
had same problem yesterday

open up system monitor and selected the tab showing running processes

there will be an entry something similar to "ubuntu software centre"

kill it

your problem should be gone

---

### Post by Rubi1200 on 2011-07-08
Open a terminal with Ctrl+Alt+T and run the following command:

```
sudo apt-get update
```

Post back with any error messages.

---

### Post by mrmjtudor on 2011-07-09
Thanks Flipper worked a treat

---

### Post by ArrrghJ on 2011-07-12
Flipper, I don't have that process in my System Monitor.

And Rubi, I can't update. I get this error:

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


I get the same thing when open Synaptic or Update Manager.

---

### Post by flipper T on 2011-07-12
try changing the mirror you are using in "software sources" and re run update

if that fails, copy & rename the file in question, then delete the original

re run up date

ps if you are not comfortable woth the command line, so what i do, run "sudo nautilus" in a terminal. then do the copy/rename/delete.

---

### Post by Rubi1200 on 2011-07-12
Hi ArrrghJ,
you can fix that error by opening a terminal with Ctrl+Alt+T and running the following commands (please copy and paste to avoid typos etc.)

```
sudo rm /var/lib/apt/lists/* -vf
```

This command removes corrupted package lists and nothing else.

```
 sudo apt-get update
```

The second command updates/refreshes the lists.

By the way, please get into the habit of using gksudo for graphical applications.

In the advice posted by flipper T the correct command to use a root file browser would be this:

```
gksudo nautilus
```

---

### Post by flipper T on 2011-07-12
while i obviously bow before your command line knowledge, sudo nautilus as always worked fine for me


:)

ps discussion on the relative merits of sudo vs gksudo not needed, thx in advance

---

### Post by ArrrghJ on 2011-07-21
Thank you so much, Rubi. That worked perfectly. I haven't been able to update or install anything in ages! Do you know what was wrong exactly?

---

### Post by Skin74 on 2011-08-02
thanks Rubi, we've got the same problem here and being newbies to Ubuntu, your instructions were easy and WORKED! :)

---

### Post by Rubi1200 on 2011-08-02
ArrrghJ, I am glad this worked for you.

Skin74, welcome to the forums and ditto :-)

---

