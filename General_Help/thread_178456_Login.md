---
title: "Login"
date: 2006-05-17
forum: General Help
---

### Post by jamesj1390 on 2006-05-17
I'm a first time user. I just installed ubuntu on my computer and after i put my password in, it comes to saying this: james@ubuntu:~$.  When i type startx, it says command not found. Help me!

---

### Post by jamesj1390 on 2006-05-17
This is an older computer. Its a Compaq 266mhz. 64megs of ram and a four gig hard drive. I cant even get to the Desktop so called. Is there a special command i need or something?

---

### Post by deadgobby on 2006-05-17
[QUOTE=jamesj1390]I'm a first time user. I just installed ubuntu on my computer and after i put my password in, it comes to saying this: james@ubuntu:~$.  When i type startx, it says command not found. Help me![/QUOTE]
Are you talking about your pass word for root in the terminal? If so it may be the same password as yor log in into Ubie. But you can change the pass word.
[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=jamesj1390]This is an older computer. Its a Compaq 266mhz. 64megs of ram and a four gig hard drive. I cant even get to the Desktop so called. Is there a special command i need or something?[/QUOTE]
Did you select "server install ?" A server install does not include a GUI. "startx" shows up as command not found because X server is not installed. If you can connect to the internet try typing the following in terminal.

> sudo apt-get install ubuntu-desktop

---

### Post by deadgobby on 2006-05-17
[QUOTE=jamesj1390]This is an older computer. Its a Compaq 266mhz. 64megs of ram and a four gig hard drive. I cant even get to the Desktop so called. Is there a special command i need or something?[/QUOTE]
Oh Snap, you are using a older computer.
[http://ubuntuforums.org/showthread.php?t=42904&highlight=64megs](http://ubuntuforums.org/showthread.php?t=42904&highlight=64megs)
Or you can try Damn Small or damnsmall linux. DM is made for older PC's.

---

