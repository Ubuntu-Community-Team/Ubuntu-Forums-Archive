---
title: "serious disk space shortage"
date: 2010-06-29
forum: General Help
---

### Post by shaftesburyiv on 2010-06-29
I have a dell mini with 4 gb of sd memory as the hard drive.  I am running Ubuntu 9.04 NBR on it and have run out of space ... I don't have enough space to update anymore, nor enough space to upgrade.  I need 1200 mb for these purposes, but I have managed to free up only 100 MB.  I have zero personal files, I have deleted many programs, including F Spot and even Mozilla, my only browser on that computer, in an attempt to make space.  It seems most of my memory is dedicated to lib files, followed by var and dev.  Any options besides a clean swipe? I am worried with the new ubuntu I will eventually have all of the same problems as it installs lib files through updates regularly.

---

### Post by flick on 2010-06-29
Try :

sudo apt-get clean

See how much that cleans up.

---

### Post by stderr on 2010-06-29
There are a few commands you can run like

```
sudo apt-get autoclean
sudo apt-get autoremove
```

I find the Disk Usage Analyser to be very useful in determining what's taking up space. If it's installed, you can launch it with: **baobab**.

There are many more ideas [here]("http://ubuntuforums.org/showthread.php?p=800462#post800462")

edit: And as luck would have it, a similar thread's taking place [here ]("http://ubuntuforums.org/showthread.php?t=1520657")- user drs305 has an excellent contribution.

---

### Post by jwbrase on 2010-06-29
4 gig is rather tiny. I carry around 16 gig in two thumb drives in my pocket on a keychain...

---

### Post by vegetarianshrimp on 2010-06-29
Try a minimal installation:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

"Total size is just under 1 GB"

---

### Post by shaftesburyiv on 2010-06-30
Sorry, I should have said that I ran autoclean, etc. already.  Thanks for the tip for the minimal installation, that seems like exactly what I need.

M

---

### Post by snowpine on 2010-06-30
I am running CrunchBang Linux on my Dell Mini 9. It takes up about half the space of UNE. If you want to go even lighter than that, check out Puppy! :)

---

### Post by mpsz on 2010-07-05
I have an EeePC 900 with 4gb mounted in / and 16 gb mounted in /home sdd and have the same problem. I also have a sdcard with 8gb.
is the minimal instalation the solution...?
Can I mount the sdcard with another file directory to save space from the small 4 gb sdd?

---

### Post by giddyup306 on 2010-07-05
I found this yesterday while I was looking to clean up myself...

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

