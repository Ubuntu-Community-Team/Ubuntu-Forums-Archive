---
title: "sync all data in /home between two computers?"
date: 2010-02-05
forum: General Help
---

### Post by heiNey on 2010-02-05
i was wondering if there was a way to sync two computers so that all the data in the /home directory was exactly the same on both, and it was done automatically as soon as theyre both turned on and connected to the same network?

i have a laptop and a desktop that i want to basically mirror each other.

i take my laptop everywhere, so i want to be able to do work on it, take it home, turn on my desktop and as soon as my laptop is connected to the network, it'll automatically sync the files to the desktop.

i want the reverse to also occur - meaning i do some work on the desktop and have it automatically sync up to my laptop while im working on the desktop if the laptop is on at the same time, or as soon as i turn the laptop on.

i had rsync set up before, but i had to initiate it manually, and i was never sure if it was overwriting files or appending.

any help is appreciated

---

### Post by Seq on 2010-02-05
There are some solutions like dropbox and UbuntuOne, but they target more of a single directory sync. Basically you're looking for:

1. Network File System
2. With Disconnected operation support
3. And conflict resolution

I haven't found anything that does this very well. I ended up using unison, which still requires a manual operation, but it gives you a long list of changes (on both sides), and will even show you the differences between files. It does two-way merge, so if you update file A on your laptop, and B on the desktop, it will copy A to the desktop and B to the laptop. It will indicate if a file was modified on both sides, and you can take whatever steps you feel neccessary to resolve the situation.

I've been doing this for over a year to keep my laptop in sync with my network (my desktops use plain nfs from the server).

---

### Post by dcstar on 2010-02-06
> **Seq said:**
> 
.........
I haven't found anything that does this very well. I ended up using unison, which still requires a manual operation
.........

Unison has command line capability: Help-Running Unison.

---

### Post by Seq on 2010-02-06
> **dcstar said:**
> Unison has command line capability: Help-Running Unison.

Yes, but it still requires manual interaction for conflict resolution. Ideally it would be nice to have it run as a daemon based on availability, and use d-bus or something to force a UI action or notification to resolve conflicts.

---

### Post by heiNey on 2010-02-06
hmmm ok, ill look into this unison program.  thanks.  

is there no way to set it up to run automatically at certain times of the day then?  like update manager does?  that's better than nothing.

---

### Post by Seq on 2010-02-06
> **heiNey said:**
> hmmm ok, ill look into this unison program.  thanks.  

is there no way to set it up to run automatically at certain times of the day then?  like update manager does?  that's better than nothing.

Yes, everything can be automated with cron in our hands! :)

You can set up a profile with the gui, then you can make a cron-job to run the cli-version periodically. This will only do the default actions, it will not sync conflicts, so you should periodically do it manually with the gui as well. Personally I avoided this as I could not be sure either machine was consistent at any particular that point.

Anyway, run the unison gui, create a profile, do the sync, etc. To get comfortable with the actions, you may wish to run "unison-gtk -auto profile", where -auto causes it to automatically sync using it's default actions. "profile" is the name of the profile you set up earlier. The nice thing about unison is the cli and gui versions have the exact same arguments. So if you are comfortable with that, removing the "-gtk" part gives you the command-line version.

From a terminal, you can set up your user's crontab by running `crontab -e`. Add the following line, again replacing "profile" with the name of your profile.:

```
0 * * * * unison -auto profile
```

That will cause it to run every hour at 0 minutes. 25 would run at :25 minutes past the hour. `man 5 crontab` is helpful for understanding your options.

---

### Post by Seq on 2010-02-06
Whoops, looks like you also need "-batch" to actually have it run unattended.

---

