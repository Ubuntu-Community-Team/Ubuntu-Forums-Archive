---
title: "alacarte(Menu Editor) problems"
date: 2010-02-04
forum: General Help
---

### Post by WutCake on 2010-02-04
well, i recently installed a program that ended up in *Others* and i wanted to move it to *Programs* but, it seems like it's readonly.. kinda.
i could add a entry, but not remove it or move it.
so now, i got like 4 launcher of that program in the same folder >_<

help* please*?
oh and, im using Jaunty.

---

### Post by WutCake on 2010-02-05
_[SIZE=1][SIZE=4][COLOR=DarkOrange]B[/COLOR][/SIZE][SIZE=3][COLOR=Indigo]u[/COLOR][/SIZE]**[SIZE=2][COLOR=DeepSkyBlue]m[/COLOR][/SIZE][SIZE=1][COLOR=Lime]p[/COLOR][/SIZE]**[/SIZE]_ :guitar:

---

### Post by howefield on 2010-02-06
What is it that stops you from creating a completely new launcher in Programs ?

The ones in "Other" won't harm anything, just leave them.

---

### Post by WutCake on 2010-02-06
> **howefield said:**
> What is it that stops you from creating a completely new launcher in Programs ?
i dont need one, i just want to remove the extra launchers and move the original to games category.
> The ones in "Other" won't harm anything, just leave them.
it does not, but it's annoying, i want them to go away, plus, it's really silly that i can't delete or move, just add stuffs.

---

### Post by WutCake on 2010-02-07
Bump, i would like to know how u can fix this.
:popcorn:

---

### Post by WutCake on 2010-02-10
_[SIZE=1][SIZE=4][COLOR=DarkOrange]B[/COLOR][/SIZE][SIZE=3][COLOR=Indigo]u[/COLOR][/SIZE]**[SIZE=2][COLOR=DeepSkyBlue]m[/COLOR][/SIZE][SIZE=1][COLOR=Lime]p[/COLOR][/SIZE]**[/SIZE]_ :guitar:

---

### Post by mc4man on 2010-02-10
If you wish an installed app to show up in a particular menu and not create a new menu item then familiarize yourself with .desktop files and in particular the line - 
Categories=

So if your unmentioned app installed a <whatever>.desktop to somewhere (typically /usr/share/applications or /usr/local/share/applications
then open the <whatever>.desktop in a text editor (as root if needed) and adjust/add that line with a Game; and it will show up in Applications -> Games after a restart

While sometimes a little experimenting is needed, this would probably do - 

Categories=Game;

---

### Post by WutCake on 2010-02-11
> **mc4man said:**
> If you wish an installed app to show up in a particular menu and not create a new menu item then familiarize yourself with .desktop files and in particular the line - 
Categories=

So if your unmentioned app installed a <whatever>.desktop to somewhere (typically /usr/share/applications or /usr/local/share/applications
then open the <whatever>.desktop in a text editor (as root if needed) and adjust/add that line with a Game; and it will show up in Applications -> Games after a restart

While sometimes a little experimenting is needed, this would probably do - 

Categories=Game;
oh, right.
my app is the game "enemy-territory"
it's launched thu a file, called "et"..

> 
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./et.x86 "$@"


---

### Post by WutCake on 2010-02-14
bump, can't find that ".desktop" file.

---

### Post by chaanakya_chiraag on 2010-02-14
Check in /home/$USER/.local/share/applications

---

### Post by WutCake on 2010-02-14
> **chaanakya_chiraag said:**
> Check in /home/$USER/.local/share/applications
yeah, found it, but where's the rest of the ".desktop"s :O

Edit: nvm, found them xD.

---

