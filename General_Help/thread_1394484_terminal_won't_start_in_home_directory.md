---
title: "terminal won't start in home directory"
date: 2010-01-30
forum: General Help
---

### Post by malachi1990 on 2010-01-30
Hi!

Very recently, my terminal aps (Eterm, gnome-terminal, and konsole) have started in the /usr/share/icons folder, and a-- I don't know how that happened, and b -- I can't get it to start in my home directory (where it's supposed to start).

If anyone can help, that'd be great.

Thank you for your time.

---

### Post by anaconda on 2010-01-30
> **malachi1990 said:**
> Hi!

Very recently, my terminal aps (Eterm, gnome-terminal, and konsole) have started in the /usr/share/icons folder, and a-- I don't know how that happened, and b -- I can't get it to start in my home directory (where it's supposed to start).

If anyone can help, that'd be great.

Thank you for your time.

Don't know why/how you succeeded to change it, but you can "correct" that problem eg. by writing a script, which will cd to your home directory, and then start the terminal

And then you could change the terminal launcher-icon to point to that script instead of the gnome-terminal..

here is a script that would do that: (It works, I tried it)
```
cd /home/anaconda
gnome-terminal
```
Copy this to an editor, and save it to eg. terminal.sh
Just change the "anaconda" to whatever your username is.

yeah, and if you are not familiar with scripts, then remember to make the script executable by:
chmod a+x launch_terminal.sh
And you can try running it, by being in the same directory than where you saved it and running
./launch_terminal.sh

---

### Post by SuperSonic4 on 2010-01-30
> **anaconda said:**
> Dont know why/how you succeede to change it, but you can "correct" that problem eg. by writing a script, which will cd to your home directory, and then start the terminal

And then you could change the terminal launcher-icon to point to that script instead og the gnome-terminal..

here is a script that would do that: (It works, I tried it)
```
cd /home/anaconda
gnome-terminal
```
Copy this to an editor, and save it to eg. terminal.sh
Just change the "anaconda" to whatever your username is.

yeah, and if you are not familiar with scripts, then remember to make the script executable by:
chmod a+x launch_terminal.sh
And you can try running it, by being in the same directory than where you saved it and running
./launch_terminal.sh

I'd find it easier to put the following line in ~/.bashrc ```
cd ~
```

---

### Post by pbrane on 2010-01-30
Do what SuperSonic4 said. That's how I do it and it works.

---

### Post by malachi1990 on 2010-01-30
Thanks, and I wish I knew how it happened to begin with myself.

---

