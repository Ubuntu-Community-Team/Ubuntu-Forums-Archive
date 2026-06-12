---
title: "Unix alias command"
date: 2006-03-11
forum: General Help
---

### Post by ubuntukid on 2006-03-11
I have quake on my computer and everytime I want to play the mission pack I have to type quake2 +set game rogue to play it. Is it possible for me to make an alias command for this so that I can just type quake2-mp2 when I want to play it? It would be preferable if this command is permanent so I can use it after the machines been restarted.

---

### Post by engla on 2006-03-11
[QUOTE=ubuntukid]I have quake on my computer and everytime I want to play the mission pack I have to type quake2 +set game rogue to play it. Is it possible for me to make an alias command for this so that I can just type quake2-mp2 when I want to play it? It would be preferable if this command is permanent so I can use it after the machines been restarted.[/QUOTE]

Do you want this in the shell, or a desktop launcher?

You can create a desktop launcher by right-clicking the desktop, "Create launcher". 
Enter something for the name "Quake 2 Mission Pack"
Then enter something for the command, in this case "quake2 +set game rogue", then save it.

If you want a shell alias you can put this in the file ~/.bash_profile (create if it doesn't exist)

alias q2mp='quake2 +set game rogue'
and start a new terminal

---

### Post by ubuntukid on 2006-03-11
The desktop thing worked for my Quake 2 game but not for the mission pack. I think the problem is that I`m trying to run two commands at the same time. This is what I`m trying to do

cd /usr/share/games/quake2; quake2 -set game rogue

If I don`t navigate the terminal to this folder it just launches regular Quake 2 instead of the mission pack. Problem is that if I put this command in the launcher it starts the terminal and imidiately stops it again.

---

### Post by kaamos on 2006-03-11
```
sudo gedit /usr/local/bin/quake2rogue
```
> #!/bin/bash
#

cd /usr/share/games/quake2
quake2 -set game rogue
```
sudo chmod +x /usr/local/bin/quake2rogue
```
And create a laucher with "quake2rogue"

---

