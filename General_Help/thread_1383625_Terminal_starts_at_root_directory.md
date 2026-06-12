---
title: "Terminal starts at root directory"
date: 2010-01-17
forum: General Help
---

### Post by Vyder on 2010-01-17
Hi

I've just installed Ubuntu 9.10 dual booting with W7. I noticed that the terminal is now starting up at <username>@<host>:/$ instead of <username>@<host>:~$

It's just annoying to have to cd ~ before i get started every time for every new terminal window.

Is there anyway I can change this default? (As far as I remember, this hasn't happened on any other unix systems I've used).

Vyder

---

### Post by septekin on 2010-01-17
Isn't this something that you may set in your .bashrc file at PS1 entry?

---

### Post by Vyder on 2010-01-18
I don't know. The first thing I did was to read through the ~/.bashrc file. I didn't find any code/comments that explained anything about default directory.

---

### Post by Vyder on 2010-01-18
[Solved]

I fixed it by adding "cd ~" at the end of my .bashrc file. I found out that when the terminal starts up, the bash code in the bashrc file is executed. So any bash commands added in there get executed too.

Vidur

---

