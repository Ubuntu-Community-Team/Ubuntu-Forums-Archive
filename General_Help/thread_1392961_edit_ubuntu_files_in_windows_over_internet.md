---
title: "edit ubuntu files in windows over internet"
date: 2010-01-28
forum: General Help
---

### Post by blank bank on 2010-01-28
I have a remote server running Ubuntu, but the only computer that I have physical access to runs windows xp.  Is there any way to edit the files remotely?

Right now, I'm using ssh and then nano to edit the files, but I'd rather use a windows text editor (notepad++).  I know I can use pscp to copy files, but every time I make a change to the file, I have to uploaded again to see the results (very tedious).

PS- the win xp computers im using are at my college.  You CAN install software on them, but there's a firewall to the outside internet blocking SOME ports... SSH, port 80, port 8080 work fine right now. I can get admin access to the windows computer, and I have root control over the ubuntu one.   Also, I can only use whatever computer is open... so I'd prefer to use a program that can be installed on a USB stick.

Any suggestions?

Thanks

---

### Post by t4thfavor on 2010-01-28
SCP them to te windows pc, edit to your hearts desire then scp them back.
All is good, its easy enough to use nano though.

---

### Post by blank bank on 2010-01-28
I'm programming, so it's just so tedious to keep typing my password into scp every time i change a comma or whatever.

---

### Post by t4thfavor on 2010-01-28
Is there not a remember password checkbox?

You could copy all the files over, and edit them all at once. Then you can put them back all at once too. If you get a compiler for windows for the language your writing in, you can do it all there, then put it back when your done working out the bugs.

---

### Post by falconindy on 2010-01-28
Learn Vim, imo. It's a superior text editor with equivalent (or more) features compared to most text editors. The learning curve is vertical, but well worth the time investment, particularly as a programmer or as anyone who spends **any** amount of time with a Linux console.

The downside is that after a while you start wanting Vim bindings (hjkl) in **all** your programs.

---

### Post by llamabr on 2010-01-28
> **falconindy said:**
> Learn Vim, imo. It's a superior text editor with equivalent (or more) features compared to most text editors. 
Yes, if you like having a sore pinky.

Text editors are a matter of preference.

To the original question, you could download the code, edit it all you want, and then scp it back.  Problem solved.

---

### Post by pirateghost on 2010-01-28
winscp.

edit the files directly with the built in editor in winscp

---

### Post by goldencako on 2010-01-28
Alternatively, if the boot process isnt blocked by your university, you could run you preferred live edition linux on a usb stick. Not optimal for speed, but since you are only editing files, that might not be such an issue.

---

