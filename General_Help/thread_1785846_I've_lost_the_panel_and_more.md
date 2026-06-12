---
title: "I've lost the panel and more"
date: 2011-06-18
forum: General Help
---

### Post by haapsalu_sall on 2011-06-18
I don't know what I hit. I've lost the panel. Right clicking on top and bottom of the screen does not bring up the "add panel" menu AND Alt F2 doesn't do anything. Any ideas what I did and can I recover everything or will I have to reload the whole thing?
Thanks.

---

### Post by nzjethro on 2011-06-18
These commands will restore your panels to default. I'm not sure if there is a way to restore the panels to how you had them, so run this, then re add the launchers you need.

```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

---

### Post by haapsalu_sall on 2011-06-18
Where do I run this? i can't get to F2 and I have no where else that I know of to run them.

ETA Looking at the screen, the panel seems to BE there, under something else, but I can't move anything to bring it up, right clicking gets me the minimize menu.

---

### Post by nzjethro on 2011-06-18
Try Ctrl + Alt + t to bring up a Terminal to run those commands. Or maybe post a screenshot if you are unsure what the problem is (i.e. if it is "behind" something).

---

### Post by haapsalu_sall on 2011-06-18
Ctrl alt t brought up the terminal! I copied and pasted the commands but nothing happened, it didn't even ask for my password. Below is the screen shot of what things look like. I have my panel on the bottom (when it's there).

---

### Post by nzjethro on 2011-06-18
Hmm, it worked for me on 10.10! Try again with
```
killall gnome-panel
```
instead of
> pkill gnome-panel

---

### Post by dFlyer on 2011-06-18
Open a terminal with cntl-alt t than enter the following command:

killall gnome-panel

---

### Post by haapsalu_sall on 2011-06-19
It says for gnome-panel no process ound.

---

### Post by dino99 on 2011-06-19
- if right click on panel dont work, try Alt+right-click (now Oneiric default)

- if gnome-panel not found, well thats mean its already killed

so logout then login

depend on your login choice, into a terminal, run either:

unity --reset
unity --replace
gnome-panel --replace
gnome-shell --replace
( if gnome-shell is installed of course, from gnome3-team ppa)

---

### Post by haapsalu_sall on 2011-06-19
nzjethro and dFlyer, thanks for the help.

In the clear light of the morning, I got my panels back. I searched Google for add panel to terminal and found this site [http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/](http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/)

The first solution -- pkill or the killall mentioned above did not work (in fact nothing happened). I tried the second command which is

[HTML]gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &[/HTML]The terminal said there was no panel there and prompted me with a sudo apt-get command (apologies, I wasn't paying close enough attention to remember the whole command). It ran like a charm, restarted computer and voila, I have panels.

Also nice to know I'm not the only person who has managed to unwittingly delete a panel.

---

