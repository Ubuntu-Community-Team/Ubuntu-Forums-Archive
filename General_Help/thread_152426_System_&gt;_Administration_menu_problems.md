---
title: "System &gt; Administration menu problems"
date: 2006-03-29
forum: General Help
---

### Post by jmoschetti45 on 2006-03-29
When I try to open something in the menu, it will prompt me for my password. After I enter it nothing ever comes up. This happens to everything under the Administration menu. Ideas?

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=jmoschetti45]When I try to open something in the menu, it will prompt me for my password. After I enter it nothing ever comes up. This happens to everything under the Administration menu. Ideas?[/QUOTE]
Do you have admin rights ?

---

### Post by majicaldutch on 2006-03-31
I just installed linux and the same thing is happening to me. I enter the password, and at the bottom of the screen it says "starting xxxx" with xxxx being whatever administration option I have chosen. The mouse wheel spins for a few seconds and then it stops, the window with "starting xxxx" has dissapeared and everything returns to as idle.

---

### Post by dcstar on 2006-03-31
[QUOTE=majicaldutch]I just installed linux and the same thing is happening to me. I enter the password, and at the bottom of the screen it says "starting xxxx" with xxxx being whatever administration option I have chosen. The mouse wheel spins for a few seconds and then it stops, the window with "starting xxxx" has dissapeared and everything returns to as idle.[/QUOTE]
Open a terminal and enter:
```
sudo ls
```
Tell us what happens after you enter your password.

---

### Post by xenmax on 2006-03-31
This could be useful:
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)

---

### Post by jmoschetti45 on 2006-04-03
[QUOTE=dcstar]Open a terminal and enter:
```
sudo ls
```
Tell us what happens after you enter your password.[/QUOTE]

I'm sitting at the prompt as root. Its not a privliges thing.

---

### Post by carlosqueso on 2006-04-03
Did you do an expert install? That breaks the GUI tools, which expect you not to.   Unfortunately, I'm not 100% sure what to tell you about fixing it except to reinstall the normal way and use ```
sudo passwd
``` if you want to be able to log in as root.

---

### Post by xenmax on 2006-04-04
if you did an expert install, you can either do a re-install or if you can fix you sudoers list. this is what i did, the thread i posted should help you do that

---

