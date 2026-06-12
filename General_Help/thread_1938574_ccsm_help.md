---
title: "ccsm help"
date: 2012-03-09
forum: General Help
---

### Post by mushroomman87 on 2012-03-09
so i just installed ubuntu (meerkat) onto my laptop, everything was fine, lovin ubuntu, set up wine, and a bunch of other stuff.

so then i go to install ccsm in order to change my affects settings and enable the cube, got it installed through the terminal(the synaptic couldnt find it for some reason?)

and now heres my problem, when opening ccsm through system>preferences it says opening ccsm(on the bottom panel) then nothing and it acts as if i hadnt even tried to open it.

so i run to the terminal and try opening it through their and i get this

Info: No sexy-python package found, don't worry it's optional.
Loading icons...
Segmentation fault

and a windows opens for a few seconds then closes. any help?

any ideas?

---

### Post by mushroomman87 on 2012-03-10
bump

---

### Post by mushroomman87 on 2012-03-11
bump

---

### Post by rg4w on 2012-03-12
Not sure about the Python error, but it may help to try to reset Unity with this command:

unity --reset

---

### Post by mushroomman87 on 2012-03-13
caleb@ubuntu:~$ unity --reset
The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity
caleb@ubuntu:~$

installed unity, and reset unity, still same problem, after resetting unity all it really changed is that it got rid of my wobbly windows :(

edit: ok i got it all to work, i installed the newest version of compiz fusion and it fixed it, but now im in another pickle, i cant move windows/resize them on any workspace other than the first.

double edit: actually now i get no window borders at all, cant move or resize any of my windows while running compiz, and it sets my mouse color and behavior back to default. is their any way i can make compiz use the settings i have set in the appearance menu for mouse and window borders/decorators?

lol, one more thing(pardon my noobiness, im excited) how do i use emerald? and how do i change the logon screen background/startup sounds/logon sounds?

---

