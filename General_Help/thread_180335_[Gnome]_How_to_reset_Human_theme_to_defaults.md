---
title: "[Gnome] How to reset Human theme to defaults?"
date: 2006-05-22
forum: General Help
---

### Post by krzykwas on 2006-05-22
I ran a programme with sudo to check why it didn't behave properly. It gave me nothing but changed the default Human theme. How to fix the changes?
My desktop looks like this: [http://img210.imageshack....utekranu3jq.png](http://img210.imageshack....utekranu3jq.png)
I would like it to look like this: [http://www.ubuntu.com/htd...5.10-themes.jpg](http://www.ubuntu.com/htd...5.10-themes.jpg)

---

### Post by unnes on 2006-05-22
Your image links do not work.

---

### Post by krzykwas on 2006-05-22
Sorry, now everything should work.
Normal theme: [http://www.ubuntu.com/htdocs/local/ubuntu-5.10-themes.jpg](http://www.ubuntu.com/htdocs/local/ubuntu-5.10-themes.jpg)
My theme: [[img=http://img407.imageshack.us/img407/8905/zrzutekranu4mu.th.png]](http://img407.imageshack.us/my.php?image=zrzutekranu4mu.png)

The problem description:
1. I installed a game of my friends ([http://eros.vlo.gda.pl/~m2tek/Projekt1/szuter.tar.gz](http://eros.vlo.gda.pl/~m2tek/Projekt1/szuter.tar.gz)) that uses HawkNL 1.68 ([http://www.hawksoft.com/hawknl/](http://www.hawksoft.com/hawknl/)) and Irrlicht libraries (included).
I installed also libgl1-mesa-dev, libglu1-mesa-dev, libxxf86vm-dev, x11proto-gl-dev, x11proto-xf86vidmode-dev.
2. Game: /usr/local/szuter, libraries: /usr/local/include and /usr/local/lib. I had to put "/usr/local/lib" into /etc/ld.so.conf and run sudo ldconfig -vn /usr/local/lib because of problems while running the game (NL.so.1.6 not found).
3. I made a mistake trying to join the server 127.0.0.1. I should have chosen the localhost to be a host. Then I tried to use sudo to check whether modes are the problem.
4. After my friend had told me that it was my mistake, everything started to work fine (I chose "host").
5. I went on to do another task. It means editing text files, so it couldn't brake anything.
6. Later I ran Synaptic - it looked awkward. After restarting the system, there came these changes.

How to fix them?

I found some piece of information about gconf-editor and gconftool-2. Will they help me to reset the settings? How to do that?

I found also a similar problem when deleting ~/.gconf and reinstalling ubuntu-artwork helped. Unfortunatelly, not in my case. :(

---

