---
title: "Problem when configuring packages in terminal"
date: 2010-08-26
forum: General Help
---

### Post by 4NG3L9 on 2010-08-26
I have no idea what makes my terminal look like this when I install and configure any package :(
[ATTACH]167584[/ATTACH]

When should work and look like 
[ATTACH]167585[/ATTACH]

How do I get it to work properly?

---

### Post by oldos2er on 2010-08-26
The first screenshot looks as though ncurses is not installed.

---

### Post by 4NG3L9 on 2010-08-27
Thanks for your advice.

After trying to install ncurses tried again and I realized the real problem.

The problem was that I was not reading #-o

[ATTACH]167663[/ATTACH]

---

### Post by itcotbtoemik on 2010-08-27
...though to be accurate, the screenshots show whiptail,
which has less flexibility for screensize than dialog
(accounting for a line or two, depending on the screen).

---

### Post by 4NG3L9 on 2010-08-28
My laptop screen is 10" and almost every time I install something I do not need a size too large for the terminal. So I used the smallest size possible due to the size of my screen :(

I had trouble installing ncurses so I'd rather stay with a 80x24 terminal :D

---

