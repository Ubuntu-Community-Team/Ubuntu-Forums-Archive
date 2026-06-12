---
title: "remove tcl/tk look"
date: 2006-06-15
forum: General Help
---

### Post by wousser on 2006-06-15
Hi

Yesterday I've installed amsn and tcl/tk but amsn wasnt my thing so I removed it but now several applications have that tcl/tk look like gedit and synaptic.
How can I change that look, I've tried to remove tcl/tk 8.5 but that didnt work.

Thanks in advance

ps. I see it happens only when I run an application as root.

---

### Post by SlCKB0Y on 2006-06-15
that looks like the base gnome theme to me.

---

### Post by Ramses de Norre on 2006-06-15
```
sudo cp ~/.themes /root/.themes && sudo cp ~/.icons /root/.icons && sudo cp ~/.fonts /root/.fonts
```

---

### Post by wousser on 2006-06-15
[QUOTE=SlCKB0Y]that looks like the base gnome theme to me.[/QUOTE]
could be, but it happens after tcl/tk or amsn.
[QUOTE=Ramses de Norre]```
sudo cp ~/.themes /root/.themes && sudo cp ~/.icons /root/.icons && sudo cp ~/.fonts /root/.fonts
```[/QUOTE]

that doesnt work i get an error about the themes map.
```
cp: map `/home/wouter/.themes/' wordt overgeslagen
```
map .themes is skipped.

---

### Post by Ramses de Norre on 2006-06-15
```
sudo cp -R ~/.themes /root/.themes && sudo cp -R ~/.icons /root/.icons && sudo cp -R ~/.fonts /root/.fonts
```
I forgot the -R option =)

Van waar ben je overigens? Ik zie dat je nederlands praat.

---

### Post by wousser on 2006-06-15
[QUOTE=Ramses de Norre]```
sudo cp -R ~/.themes /root/.themes && sudo cp -R ~/.icons /root/.icons && sudo cp -R ~/.fonts /root/.fonts
```
I forgot the -R option =)

Van waar ben je overigens? Ik zie dat je nederlands praat.[/QUOTE]

Thanks! problem fixed

en ik kom uit Driebergen (Utrecht)

---

