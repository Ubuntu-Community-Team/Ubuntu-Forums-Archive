---
title: "Ubuntu 10.10"
date: 2011-03-23
forum: General Help
---

### Post by SexySara on 2011-03-23
I had webcamstudio installed then I uninstalled it and manually removed all the left over directories in terminal. However, when I run..
```
locate webcamstudio
```
... files still show up. But when I run a root gui search for them, there is none to be found... even if I go to directories themselves, there are no files left over at all. So my question is, why do the files still show up in the terminal when I run the locate command, yet I can't seem to see them anywhere? I have attached a screen shot too.

On a side not, I upgraded from 10.04 to 10.10... Maverick seems to faster in all areas for me. Really surprised because I had read that Maverick was considerably slower... not for me, it feels really nice.

---

### Post by andrewthomas on 2011-03-23
I assume that you installed this from a .deb?

If so, you can 

```
sudo dpkg --purge webcamstudio
```

---

### Post by SexySara on 2011-03-23
Yes it was a deb. I ran that command you gave and this is the out put...

```
soultravel369@ANONYMOUS:~$ sudo dpkg --purge webcamstudio
dpkg: warning: ignoring request to remove webcamstudio which isn't installed.
soultravel369@ANONYMOUS:~$ 
```And its still showing up.

I also ran these commands and they it shows up...
```
sudo deborphan | xargs sudo aptitude -y remove --purg
```and
```
sudo aptitude autoclean
```So I dunno whats going on.

---

### Post by andrewthomas on 2011-03-24
Reinstall it and then purge it.

If it doesn't get rid of all the files, then there is something wrong with the package.

Where did you get it from?

---

### Post by Another Monkey on 2011-03-24
I think this is just the database that is used by "locate" being out of date, I have seen it 'find' files that I know I deleted.
Try this and see if the problem goes away
```
sudo udpatedb
```
This should update the database for "locate", by default it updates weekly (I think)

---

### Post by SexySara on 2011-03-26
I tired everything from what all of you had mentioned and still nothing. No worries though, I just backed up my files and did another install. I had a lot of messed up things in there for some reason. My Alt+F2 stopped working for some reason and I couldn't run the emerald command to see the window boarders and stuff. I dunno what happened. I learned now that a clean computer is a good computer. Too many things can go wrong with all the crap I had installed and NEVER used lol.

---

