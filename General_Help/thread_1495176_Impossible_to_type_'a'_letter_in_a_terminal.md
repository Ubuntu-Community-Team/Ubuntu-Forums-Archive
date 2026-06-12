---
title: "Impossible to type 'a' letter in a terminal"
date: 2010-05-27
forum: General Help
---

### Post by kisame94 on 2010-05-27
Hi,

Since 2 days, when I type the lowercase 'a' letter in a terminal, nothing is written (it's not the case for the uppercase 'A' letter).
The matter appears with all terminal's software (guake, Terminal, xterm...).
The only way for me to type the 'a' letter is to type 'Insert' key before.
I tried many solutions but the matter is still here.
Here, there is some clarifications and some solutions I tried:
-If I copy and paste a text, 'a' don't appears. For example, if i try to copy and paste
'sudo apt-get install'
'sudo pt-get instll' will appears
-The matter appears 2 days ago. Before that, I removed the .gconf file
-It's not a fresh installation of ubuntu but an update from karmic to lucid. When i was under karmic, I was using KDE. Then I did an upgrade, then I tried Xubuntu and Lubuntu and finally I moved to Ubuntu. The first week under Ubuntu (Gnome) was without any matter and 2 days ago, this matter appeared.

-I tried this following command line:
xmodmap -pke >fichier.conf
and the file called "fichier.conf" (I'm french) contains this line:[FONT=monospace]
[/FONT]keycode  24 = a A a A ae AE ae AE

-When I type this line:[FONT=monospace]
[/FONT]printf "\x61\n"
a 'a' appears in my terminal.

-In tty1 and all the other programs, 'a' appears without any trouble

-I tried with other users in my computer but the matter is still the same no matter wich user I use.

-I tried to change fonts of my environment and I also tried to change fonts only for the terminal but whithout success.

-I tried to change the layout of my keyboard.

Thx for your help.

---

### Post by kisame94 on 2010-05-28
up!

---

### Post by ticlem on 2012-02-23
Just had the same problem but with the x character.
Thanks to [_this post_]("https://bbs.archlinux.org/viewtopic.php?id=117630") I realized that I have a command in my .inputrc that should not be there : xset r rate 250 50

It seems that the first letter of an invalid command in the .inputrc cause every terminal to eat this letter.

Hope this help people encountering this problem.

Ticlem.

---

