---
title: "Playing mp3 and DivX in ubuntu 9.1"
date: 2010-03-27
forum: General Help
---

### Post by thanuja on 2010-03-27
Hi Im using ubuntu 9.1. I need to be able to play mp3 files and DivX files. How can i achieve that..How to install codecs for ubuntu 9.1???

Pls help me on this!! Thanks

---

### Post by TeoBigusGeekus on 2010-03-27
1.Open terminal
2.Type
```
sudo apt-get install ubuntu-restricted-extras
```
3.Press enter
4.Type your password (you won't see anything typed on monitor)
5.....
6.Profit

---

### Post by zvacet on 2010-03-27
From software center install ubuntu-restricted extras.Add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your source list and in synaptic search for w32 codecs and install them.

---

### Post by dineshs on 2010-03-27
Did you try vlc player?

---

### Post by thanuja on 2010-03-27
Thanks.. It seems im unable to install VLC.. Do i have to download it? I couldnt find it in SYnaptic manager.

---

### Post by Phrea on 2010-03-27
Try the update button in Synaptic, then search for VLC again.

Have you done the previous posted restricted-extras install ?

---

### Post by zvacet on 2010-03-28
@ **thanuja**

To install VLC you have to enable universe repository.In system>admin>software sources>check all under ubuntu software and first two under updates tab.Reload.In synaptic find VLC and install it.You can use any other player like Mplayer...

---

