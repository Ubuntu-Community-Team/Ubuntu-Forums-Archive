---
title: "I am new to Ubuntu and need help"
date: 2010-03-31
forum: General Help
---

### Post by aamirshf on 2010-03-31
Hi everyone, I am new to Ubuntu and need help. I have been using windows but now I want a change this is why I have also installed ubuntu 9.10 in my pc using wubi with win7. I like it a lot.
 
For now, I do not have internet connection and when I go to the software center it requires an internet connection for software installation.
 
Is is possible if I can download softwares for ubuntu from any computer and then install them onto my PC??
 
Thanks.

---

### Post by N92 on 2010-03-31
yes you can I have done it a couple of times.
you just need to put it on the pc you want the program installed on.
If you download a .deb file all you need to do is double click on the file and click install.
If the download is a .tar you will need to double click on the file and extract it to your home folder then double click on the folder you just extracted then double click on the readme file and follow the instructions.

Hope this helps.

---

### Post by neednewlaptop on 2010-03-31
The Ubuntu software is stored in repositories on the web, that is why software center needs to be on-line. You can make these repos available off-line. For that you can take a look at thread [http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460).

I haven't tried it myself and it seems like a lot of work, but it's possible.

For getting just one or a few software packages I would probably use N92's reply.

---

### Post by nothingspecial on 2010-03-31
You can do it from [[COLOR="Magenta"]here[/COLOR]]("http://packages.ubuntu.com/karmic/")

Download the deb file

Bear in mind that you will have to download all the dependencies as well (signified by a red circle)........

.......and download all the dependencies of those dependencies etc etc.

Put them all in the same place, eg your Desktop

then```


cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by trideceth12 on 2010-04-01
1) install a wireless card
2) put your unit in a backpack
3) go to McDonalds
4) buy a cheeseburger / small fries
5) set up your computer (you may need to bring a powerboard & extension cord
6) Download as much as you like :D



I'm only half joking... IMO If you want to install something which has a lot of dependencies the most convenient way is taking your computer to the internet and letting synaptic do it, rather than individually downloading each package.

---

### Post by aamirshf on 2010-04-01
Thanks to all of you.... specially 'nothingspecial'

It looks like that I have to have an internet connection to download softwares and plugins etc. Right now I cannot even run any video or audio file as the formats that I have is mp3 and avi mpg etc.

Anyways thanks again all of you.

Best regards.

---

