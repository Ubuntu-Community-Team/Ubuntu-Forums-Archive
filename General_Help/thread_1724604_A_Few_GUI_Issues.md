---
title: "A Few GUI Issues"
date: 2011-04-08
forum: General Help
---

### Post by dniMretsaM on 2011-04-08
I have a few GUI issues that aren't really a problem, but are still annoying.

[S]The first one is with Minefield 4.2 (I also had this issue on 4.0). When the is small, it cuts off the top half of the tabs.[/S] <-Solved! [S]The second is with Deluge. On the left side of the screen (big or small) the drop down list of trackers and things is partially cut off.[/S] <- Not really solved, but I don't need help anymore because I'm now using qBittorrent. I would like to know if there is a way to fix either of these or if I should do a bug report.

---

### Post by dniMretsaM on 2011-04-09
B[COLOR=Red]u[COLOR=Lime]m[/COLOR][/COLOR][COLOR=Blue]p[/COLOR][COLOR=Magenta].[/COLOR]

---

### Post by dniMretsaM on 2011-04-10
Last bump then bug report time.

---

### Post by Sidewinder1 on 2011-04-10
This is definitely NOT meant as an insult but have you tried maximizing the window? Have you tried to resize the panes which have the info you need, that's cut off?
I have found that almost all things are possible in Ubuntu; sometimes it takes some research and help from the tireless volunteers on this forum.

HTH,
Side

---

### Post by Frogs Hair on 2011-04-10
This may be simple , but turn off tabs on top close and open Firefox  and set to tabs on top again. I have Minefield as well but have not seen this . Also , try another theme to see what happens.

---

### Post by dniMretsaM on 2011-04-10
> **Sidewinder1 said:**
> This is definitely NOT meant as an insult but have you tried maximizing the window? Have you tried to resize the panes which have the info you need, that's cut off?
I have found that almost all things are possible in Ubuntu; sometimes it takes some research and help from the tireless volunteers on this forum.

HTH,
Side

Yes I have. I'm not a total idiot. Maximising Minefield does work. That's why I said when it was small. Resizing does nothing for either Minefield or Deluge and Deluge has the glitch either large or small. I'll try your suggestion later Frogs Hair, thanks. Right now, I have to leave.

---

### Post by dniMretsaM on 2011-04-15
Your suggestion didn't work, so I did a little experimenting with some of my userChrome.css edits and finally got it fixed. Apparently, one of the edits I used included the tab-trimming (it also cut off the URL bar when the tabs were on the bottom). I removed that part and now it works great. BUT, I still haven't had any advice on my Deluge issue. I'll wait a little longer and then do a bug report.

---

### Post by pqwoerituytrueiwoq on 2011-04-15
does this help?
most apps tend to curt off the other side but i am not familiar with Deluge

---

### Post by dniMretsaM on 2011-04-15
> **pqwoerituytrueiwoq said:**
> does this help?
most apps tend to curt off the other side but i am not familiar with Deluge
Nope. Stays the same.

---

### Post by apochry on 2011-04-15
Hi dniMretsaM,

I used to have the exact same issue with deluge. Now not any more, but I don't know what fixed it....
Here is what I did with my deluge:
I was angry that can't find a solution for the problem, so I turned off the the sidebar by unchecking View -> Sidebar. I used it like that for like a month or something and than came new problem. I was unable to download at all. Torrents with a lot of seeds did not start. I was working on solving this problem, that makes deluge totally useless, for several weeks. In this time I uninstalled/installed/reinstalled deluge several times. I also reseted the deluge's settings to their defaults by deleting everything in the ~/.config/deluge/ folder. That brought the sidebar back on and I noticed that  my first issue had been fixed somehow. That same thing solved the download problem too.

Later I've noticed that limiting the upload speed makes deluge unable to download torrents with plenty of seeds (for some reason, unknown to me, the developers and the universe).

This is everything I can provide you with. I hope I would be useful somehow.

So in my eyes: Deluge = best torrent client I know but pretty buggy (at least on my system)!

Izzo

---

### Post by dniMretsaM on 2011-04-15
I tried showing/hiding the sidebar, deleting the contents of  home/.config/deluge, and reinstalling but to no avail. So, this gave me a  good excuse to try out qBittorrent which as been highly recommended. I  have to say, it seems really nice! I'll definitely be using qBT from now  on.

I'm marking this thread as solved even though it really isn't.

---

