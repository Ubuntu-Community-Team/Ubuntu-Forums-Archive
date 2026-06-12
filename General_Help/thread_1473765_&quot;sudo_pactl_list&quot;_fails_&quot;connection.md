---
title: "&quot;sudo pactl list&quot; fails: &quot;connection refused&quot;"
date: 2010-05-05
forum: General Help
---

### Post by produnis on 2010-05-05
Hi folks,

since jaunty, I used a script which check whether music is played.
It uses the following command:

```
pactl list | grep RUNNING
```(if there is no sound, it returns nothing, if there is sound it returns RUNNING)

The script is called from rc.local, and as such, it is run by root.

While in jaunty and karmic, everything works great,
a fresh install of Lucid lets the script die.

If I type in
```
sudo pactl list | grep RUNNING
```it gives me the error:
> Home directory /home/produnis not ours.
Connection refusedI don't know what this means, as the script isn't stored in my home-folder, and it does no actions in my home-folder....

In sum:
Running the comand as user "produnis", everything works well
Running the comand as root, it gives me the error.
Unfortunately, I MUST run the script as root (due to other action it does),
so, is there any hint why it is not working any longer?

thx in advance,

produnis

---

### Post by produnis on 2010-05-05
my dirty hack is to change the script, so it looks like:
```
sudo -u produnis pactl list | grep RUNNING
```
then it works...

strange..

why is root not allowed to run the command any longer?

---

