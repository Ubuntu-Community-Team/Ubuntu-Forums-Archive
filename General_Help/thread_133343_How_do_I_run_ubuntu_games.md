---
title: "How do I run ubuntu games?"
date: 2006-02-20
forum: General Help
---

### Post by johnnymo87 on 2006-02-20
Hi,

I just downloaded a few games from synaptic package manager with universal repositories. I found where they downloaded to (usr/share/games), but I can't figure out how to run any of them. I'm new to linux, but in windows I'm used to being able to find a .exe file among all the other require3d game files to run the program, but I can't find anything like that in these games folders.


On a side note, can anyone recommend a program that I can write music in, like cakewalk in windows?

---

### Post by el3ktro on 2006-02-20
Most games should have a link in Applications->Games. But besides that, in Linux executable files are not determined by an extension (.exe, .com etc.), but by the executable bit. Executable files are showed green in the Terminal. E.g. if you do "ls /usr/bin" you'll see a lot of green files, which are all executable. Usually just typing the name of the game in lowercase starts it. Yes this is a little complicated & confusing in the beginning, but hey Linux is not meant to be Windows, and you'll get used to it, believe me ;-)

Tom

---

### Post by Lux Perpetua on 2006-02-20
Look in /usr/games also; the executables might not be in /usr/share/games. Typing the name of the game from a terminal should also work in most cases. (If /usr/games isn't in your search path, you might have to prefix it with /usr/games/.) Also, see if you have a games submenu under the main Gnome menu (e.g., in "Applications").

---

