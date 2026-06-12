---
title: "suid rights"
date: 2006-03-16
forum: General Help
---

### Post by andrey on 2006-03-16
Why this files have a suid bit? :-k 
[FONT="Serif"][COLOR="DarkRed"]
-rwxr-sr-x  1 root games 64948 2005-10-04 03:15 /usr/games/same-gnome
-rwxr-sr-x  1 root games 74388 2005-10-04 03:15 /usr/games/gnomine
-rwxr-sr-x  1 root games 70100 2005-10-04 03:15 /usr/games/gnome-stones
-rwxr-sr-x  1 root games 83444 2005-10-04 03:15 /usr/games/mahjongg
-rwxr-sr-x  1 root games 53140 2005-10-04 03:15 /usr/games/gtali
-rwxr-sr-x  1 root games 44052 2005-10-04 03:15 /usr/games/gnotravex
-rwxr-sr-x  1 root games 102132 2005-10-04 03:15 /usr/games/gnobots2
-rwxr-sr-x  1 root games 45012 2005-10-04 03:15 /usr/games/gnotski
-rwxr-sr-x  1 root games 70804 2005-10-04 03:15 /usr/games/glines
-rwxr-sr-x  1 root games 90612 2005-10-04 03:15 /usr/games/gnibbles
-rwxr-sr-x  1 root games 91268 2005-10-04 03:15 /usr/games/gnometris
[/COLOR][/FONT]
I get this using command:
[FONT="Serif"][COLOR="Green"]sudo find / -type f \( -perm -04000 -o -perm -02000 \) -exec ls -l {} \;[/COLOR][/FONT]

Distro: Ubuntu 5.10

---

