---
title: "Audio player"
date: 2006-06-20
forum: General Help
---

### Post by loserboy on 2006-06-20
Just installed ubuntu for 64 bit and this is my 1st time with linux, is there a player like winamp available through synaptic or something... somone said xmms but i dont know how to get it  :(    and if i do it through command line plz give me a step by step.

also if somone answers that i got plenty more.

thanks in advance
mike

---

### Post by GoogleNinja on 2006-06-20
xmms and beep-media-player are both very popular, and are both in synaptic

---

### Post by loserboy on 2006-06-20
lol wow that was easy enough thanks

---

### Post by loserboy on 2006-06-21
hey i cant move skins into the skins folder, says i dont have permission-not the owner, but im on with the only profile i have

---

### Post by mcduck on 2006-06-21
[QUOTE=loserboy]hey i cant move skins into the skins folder, says i dont have permission-not the owner, but im on with the only profile i have[/QUOTE]
You should put them to your *own* skins directory, inside your home dir. I think it's inside ~/.xmms (~ is your home, and all files/directories with a . in the beginning are hidden files)

In Linux/Unix you are never the only user of your machine. Most of the filesystem belongs to root. Other users only have write access to their own home directories.

In ubuntu, the first user belongs to admin group, and can do things as root with the 'sudo' command.

Here's more info about Ubuntu and root: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by loserboy on 2006-06-21
i guess i still dont get it

im using bmp and the only folder i can find is in

/usr/share/bmp/skins

am i being dumb?

---

### Post by mcduck on 2006-06-22
for bmp, your personal dir would be /home/[yourusername]/.bmp/ (or ~/.bmp/)

You need to set Nautilus (the file manager) to show hidden files to see this directory.

---

### Post by loserboy on 2006-06-22
thanks

---

