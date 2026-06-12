---
title: "Games...new to ubuntu, tried running free doom..."
date: 2009-11-12
forum: General Help
---

### Post by jotto! on 2009-11-12
Just browsed some of the games available and installed the 2 doom type games, Freedoom and Free DM.

Both appeared to install OK but when I run them, after about 15 seconds, they just disappear. Am I doing something wrong or is this just a glitch?

Thanks.

---

### Post by isoToxin on 2009-11-12
It's a known bug.

[https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498](https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498)

The safe way to play for the time being is to install the older debian stable package which runs fine.  You can download from here:

[http://packages.debian.org/stable/games/prboom](http://packages.debian.org/stable/games/prboom)

Just grab the correct deb file for your hardware (probably i386), save it to your home folder, the double click and install.

---

### Post by jotto! on 2009-11-12
Thanks for the reply. DL the file and tried to install but it said a later version is already installed. uninstalled both versions I had and tried again but got same error. Any ideas?

---

### Post by isoToxin on 2009-11-13
Hi,

Sorry for the late reply, wasn't near a computer last night.  did you have any luck getting this to work?  I have just tried on a fresh karmic install, and I was able to recreate your problem, along with a workaround.  Here is how I worked around it (in case you haven't already figured it out).

- Go to synaptic, and run a search for doom.  Check "freedoom" for installation.  Apply.

- Tried to run.  Doom exited after a few seconds.

- Go back into synaptic, and find the prboom package.  Mark for complete removal.  This will also remove freedoom.

- Once that's done, download prboom package from debian stable repository.

- Double click on the deb file.  Package manager will load and it will warn that there is a later version in the software channel and that you are strongly advised to get that version instead.  Just ignore this and continue to install.

- After this, go back into synaptic and mark freedoom for installation.

- Once it's installed, you should be able to play.

- Just tested this exact sequence and it worked fine.  Good luck.

---

### Post by jotto! on 2009-11-13
Thanks, will give it a go when Ive worked out my new problem of ubuntu now not booting! Kernel panic.....

---

### Post by isoToxin on 2009-11-13
Argh. Definitely higher priority than being unable to play doom. Good luck. :)

---

### Post by jotto! on 2009-11-14
Well Im back! lol.

Downloaded the amd64 package as it was the correct one for me, installed it but cannot find it in my list og games or installed software.

Where would it be located and can I create a shortcut to it?

---

