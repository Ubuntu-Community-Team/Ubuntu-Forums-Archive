---
title: "Stop dialoge that comes up when executing executable text file?"
date: 2010-08-01
forum: General Help
---

### Post by Dustin2128 on 2010-08-01
I made a couple of shell scripts to automate normally boring processes, and put them on my desktop to be used as icons. Whenever I click them, I get the normal dialogue: run in terminal, display, cancel, run, the answer always being just run. How would I turn this off? It's getting rather annoying.

---

### Post by prodigy_ on 2010-08-01
You can move your scripts somewhere else (for example, to your Home Folder) and then just add launchers to your desktop.

---

### Post by Dustin2128 on 2010-08-01
> **prodigy_ said:**
> You can move your scripts somewhere else (for example, to your Home Folder) and then just add launchers to your desktop.
I could, but would that eliminate the dialogue? I think not. I do have a scripts folder though, the ones on my desktops are only cures for annoyances that crop up frequently. For instance, normally I'd have to go to a terminal and browse to starcraft, a directory within a directory within a directory within a directory, then type wine starcraft.exe to start it (for some reason I'm forced to do this to start windows programs), the shell script just automates the process.

---

### Post by prodigy_ on 2010-08-01
> **Dustin2128 said:**
> I could, but would that eliminate the dialogue?
Yes.

For example, if the script you need to run is **/home/username/example.sh**, you'll just need a launcher with the following line in its "Command" field: ```
bash /home/username/example.sh
``` You won't even need to make this script executable.

Alternatively if this script is supposed to generate some output you want to see, the command you'll need is: ```
gnome-terminal -x bash -c "bash /home/username/example.sh; bash"
```

---

### Post by themusicalduck on 2010-08-01
There is a way of setting it to do one or the other automatically. I think it's in nautilus preferences, but I'm not on Ubuntu at the moment so can't check where it is..

If you go to File > Preferences on the file browser and have a look around it should be somewhere in there.

But if you are just launching the files off the desktop, then a launcher like prodigy says should work.

---

### Post by Dustin2128 on 2010-08-01
> **themusicalduck said:**
> There is a way of setting it to do one or the other automatically. I think it's in nautilus preferences, but I'm not on Ubuntu at the moment so can't check where it is..

If you go to File > Preferences on the file browser and have a look around it should be somewhere in there.

But if you are just launching the files off the desktop, then a launcher like prodigy says should work.
that solved it. Except it was Edit>preferences.

---

### Post by Dustin2128 on 2010-08-01
> **prodigy_ said:**
> Yes.

For example, if the script you need to run is **/home/username/example.sh**, you'll just need a launcher with the following line in its "Command" field: ```
bash /home/username/example.sh
``` You won't even need to make this script executable.

Alternatively if this script is supposed to generate some output you want to see, the command you'll need is: ```
gnome-terminal -x bash -c "bash /home/username/example.sh; bash"
```
also thanks for the solution but I prefer solutions to workarounds if you know what I mean.

---

### Post by efflandt on 2010-08-02
For your own scripts or executables, you can create a **bin** directory in your home directory, and that will then automatically be included in your path.

echo $PATH
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Then you could put a launcher on your desktop or top panel to run them when double clicked, and you do not even need to include a path (just the script name).

If you set executables to always run in Nautilus, then you might accidentally run something that you want to view or edit.  For example anything you copy to your system from FAT32 flash will have the execute bit set, whether you want it to be or not, until you change it.

---

