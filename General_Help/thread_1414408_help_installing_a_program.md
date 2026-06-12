---
title: "help installing a program"
date: 2010-02-23
forum: General Help
---

### Post by skibster on 2010-02-23
i know im a noob, and im missing something, but im trying to install a program off of the internet and i cannot figure it out. i need to install an updated version of deluge, the updated version is not in the ubuntu catalog yet. so here is the process i went through.

1) went to deluges site, clicked download version 1.2.1 on homepage.
2) went to ubuntu category and chose: "The Deluge packages in Ubuntu:"
3) went to the exact hits category and chose the lucid 1.2.1 version of deluge. 
4) went to bottom of page and under "download deluge" and clicked the link
5) chose one of the north america choices
6) chose to open with GDebi Package Installer (default)
7) gave me this error in red letters at top : Error: Dependency is not satisfiable: deluge-gtk (= 1.2.0-1)

i know it is a stupid question, i apologize in advance

---

### Post by mcduck on 2010-02-23
Well, your problem is that you tried to install the package that was made for the current development version of Ubuntu (Lucid) instead of the Ubuntu version that you are actually running (9.10, probably). That's not going to work.

If you want to download Deluge 1.2.0 for Ubuntu 9.10 you'll have to get it from GetDeb.net: [http://www.getdeb.net/app/Deluge]("http://www.getdeb.net/app/Deluge") or use the PPA repository: [https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/~deluge-team/+archive/ppa")

---

### Post by skibster on 2010-02-23
ok i did that and it installed, but it didnt replace the old version nor can i find the new version, the reason i did this was because my trackers were going to support deluge 1.2.1 but i guess they do not now, so i suppose i will switch to transmission:(

---

