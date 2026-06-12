---
title: "Rhythmbox probllems"
date: 2006-03-21
forum: General Help
---

### Post by matthewinuk on 2006-03-21
I ripped a few cds following advice from

[http://www.ubuntuforums.org/showthread.php?p=848409#post848409](http://www.ubuntuforums.org/showthread.php?p=848409#post848409)

to make good quality mp3s. They play perfectly when u put the mouse pointer over the file icon but in rhythmbox it plays about 3 seconds then stops, then plays again and continues in this manner for the whole song.

any ideas why?

Any reccomendations for a better mp3 player?

---

### Post by neoroses on 2006-03-21
grab automatix and install the multimedia codecs and the players with plugins

---

### Post by matthewinuk on 2006-03-21
i already ran automatix yesterday. Just figured it out. I was running grip and it was going dead slow. about 0.3x. So i closed it and now it plays perfectly. only problem being that it wont rip this cd i have

---

### Post by neoroses on 2006-03-21
turn off cd parranoia in grip and turn on drm in automatx :)

---

### Post by matthewinuk on 2006-03-21
[QUOTE=neoroses]turn off cd parranoia in grip and turn on drm in automatx :)[/QUOTE]


How

---

### Post by neoroses on 2006-03-21
in grip:

config --> rip --> tick the two boxes there and apply..and to turn dmr on just select in in automatix :) you kan now ripp at your max speed

---

### Post by matthewinuk on 2006-03-21
[QUOTE=neoroses]in grip:

config --> rip --> tick the two boxes there and apply..and to turn dmr on just select in in automatix :) you kan now ripp at your max speed[/QUOTE]

tick which boxes? i currently have cdparanoia as my rip option. The problem was only with one cd. Other cds rip at about 1.5x. also how do i open automatix. think i lost it

---

### Post by neoroses on 2006-03-21
ok in -->config-->rip yo u should see 
disable cd paranoia and disable extra cd paranoia --- tick both of them

and the other two detection and repair if you wish 

automatix should be in 

application --> system tools, if it isnt re-grab it with 

```
sudo apt-get install xterm
wget http://beerorkid.com/automatix/automatix_5.6-2_i386.deb
sudo dpkg -i automatix_5.6-2_i386.deb
```

then it will again be in 

application --> system tools

after this you should be able to rip at 20x +

---

### Post by matthewinuk on 2006-03-21
quick additional question. did u mean, enable DMA?? you said dmr. thanks  so much faster now though, i enabled dma and got rid of paranoia. hopefully wont matter that v disc is scratched up a bit

---

### Post by neoroses on 2006-03-21
hehehe yes sorry

---

