---
title: "links2 in graphics mode"
date: 2006-06-17
forum: General Help
---

### Post by gorilla on 2006-06-17
links2 -g in terminal is only possible with sudo. It works well, but I don't feel so well browsing the net with root privileges.
As user: error opening /dev/tty0 --> permission denied

Isn't there a way to draw into the framebuffer as normal user?
If I try it in Konsole under kde it works as user btw.

I also have the same issue with mplayer in terminal; playing music works, but movies only play for root.

---

### Post by ardchoille on 2006-07-21
> **gorilla said:**
> links2 -g in terminal is only possible with sudo. It works well, but I don't feel so well browsing the net with root privileges.
As user: error opening /dev/tty0 --> permission denied

Isn't there a way to draw into the framebuffer as normal user?
If I try it in Konsole under kde it works as user btw.

I also have the same issue with mplayer in terminal; playing music works, but movies only play for root.

I have the same exact problem. I can run links2 -g in a gnome-terminal, btw.

Ideas anyone?

---

### Post by gorilla on 2006-09-19
ok, I found it out finally.
You need to have gpm running (General Purpose Mouse server).
Otherwise links2 cannot use the framebuffer for some reason.

---

### Post by jdarias on 2007-05-24
I found a clue about using DirectFB on a user account on this page: [http://www.vivaolinux.com.br/artigos/verArtigo.php?codigo=2402&pagina=4](http://www.vivaolinux.com.br/artigos/verArtigo.php?codigo=2402&pagina=4)

They say overthere that one has to give permossion to /dev/tty0 so
```
~$ sudo chmod 666 /dev/tty0
```
When it's done, they mention the mouse probably stops working, so we give permossion to /dev/<mouse port>. In my case, I did
```
~$ sudo chmod 666 /dev/input/mice
```
This will enable users to use links2 with directfb, wich is WAAY better and faster than normal fb. It even supports mouse wheel. 
However, it will only work for the curent session, so these commands will have to be issued next time the computer boots. :(

Is there any way to make it permanent? i suspect that some edition in the 40-permission.rules file has to be done, Does somebody know how to do that safely?

---

### Post by jdarias on 2007-05-24
Got it working! I'm posting a howto.
[http://ubuntuforums.org/showthread.php?t=453667](http://ubuntuforums.org/showthread.php?t=453667)

---

