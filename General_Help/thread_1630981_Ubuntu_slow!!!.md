---
title: "Ubuntu slow!!!"
date: 2010-11-26
forum: General Help
---

### Post by Juand_au on 2010-11-26
Hi,

I have been using ubuntu for a while and i like it a lot, im a web developer and i have windows xp installed in virtual box, i moved completely to linux and just use windows to test in ie, it had been a while since i didnt use windows  and i had to use in the last few days and noticed how much faster it is, the thing that bothered me the most is when opening folders in the desktop or the recycle bin, in windows its instant, in ubuntu opening a folder takes a long time to open nautilus, is this normal or is my installation bad, any comments are appreciated, i dont want to abandon ubuntu,  i really like it but it really bothers me that nautilus is so slow to open.

Thanks

---

### Post by Sazhen86 on 2010-11-26
Hi.  

I would say that it is your installation as folders in Nautilus open quickly for me.  How long does it take for yours to open?  Are we talking several seconds?  If so, then there's definitely a problem.

Cheers

---

### Post by bodhi.zazen on 2010-11-26
> **Juand_au said:**
> Hi,

I have been using ubuntu for a while and i like it a lot, im a web developer and i have windows xp installed in virtual box, i moved completely to linux and just use windows to test in ie, it had been a while since i didnt use windows  and i had to use in the last few days and noticed how much faster it is, the thing that bothered me the most is when opening folders in the desktop or the recycle bin, in windows its instant, in ubuntu opening a folder takes a long time to open nautilus, is this normal or is my installation bad, any comments are appreciated, i dont want to abandon ubuntu,  i really like it but it really bothers me that nautilus is so slow to open.

Thanks

It does not sound normal, but hard to identify the "problem" from your post.

---

### Post by Lod on 2010-11-26
I experienced the same problem. I did a fresh install of 10.10 and afterwards copied my files (about 80 Gb) from the backup drive to a directory in my home. 
Opening this folder (and subfolders) took ages to complete, i.e. 8-10 seconds. After moving the files to their destinations (music to music etc.) it is fast again.

I thought it had something to do with some background indexing process or so.

---

### Post by balaji31d on 2010-11-26
I have got similar issue as well.. So, Its not just you and its not a mis-configuration.

---

### Post by Juand_au on 2010-11-26
I dont mean opening folders once nautilus is open, i mean when i open a folder in my desktop nautilus takes a little bit more than windows, im impressed by windows speed when i click the recycle bin or any other folder in the desktop, you havent finished the second click and its open, ubuntu is more like 2 clicks 1 2, sometimes 3 seconds and then  open, and its not just at that, i hadnt noticed this because i always used windows but after being using ubuntu for a while and then using windows, windows felt more responsive, i dont know. Its not a huge difference but still makes it feel better clicking thing on windows, it is the same on my friends laptop with windows 7, he clicks something and its instantly open, very fast.

---

### Post by 3rdalbum on 2010-11-26
Windows XP is a bit more lightweight than Ubuntu; you're comparing a nearly decade-old operating system with the cutting edge latest OS.

The delay you speak of does sound a bit longer than it should be. If you add the System Monitor applet to your panel, does it show a lot of CPU or IOwait when the system is idle?

---

### Post by WorMzy on 2010-11-26
If nautilus is too slow for your liking, try a lightweight file manager, like emelfm2, pcmanfm, rox, or thunar.

---

### Post by Juand_au on 2010-11-26
Yeah that did it, i tried thunar and its just as fast as windows file manager, such a better feeling when clicking folders, shame cant make it the default one, oh well thanks for your help, i hope they make nautilus faster.

---

### Post by WorMzy on 2010-11-26
Here, check this out for replacing Nautilus: [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by notte on 2010-11-26
I use pcmanfm since a long time. It's faster...

> **Juand_au said:**
> Yeah that did it, i tried thunar and its just as fast as windows file manager, such a better feeling when clicking folders, shame cant make it the default one, oh well thanks for your help, i hope they make nautilus faster.

invert the procedure shown here: 
[http://ubuntuforums.org/showthread.php?t=1395896](http://ubuntuforums.org/showthread.php?t=1395896)

or better: 


open gconf-editor, go to desktop&#8594;applications&#8594;component_viewer
change the value of exec = nautilus %s to thunar %s or pcmanfm %s

it should work!

---

### Post by Juand_au on 2010-11-26
Hey i tried that and it works, only that i lost all my desktop items, any ideas????

---

### Post by theozzlives on 2010-11-26
As posted above, it's hard to tell without more info. "It's slow" don't tell us your system specs, if you don't mind.

---

### Post by Juand_au on 2010-11-26
Well its not really that slow, i just want it like thunar, thunar is just like windows, i dont really think that there is a problem, its just the way it is, because i tried thunar and it acts just like window, you click and instantly open, great!!! my pc is a dell 1.4 ghz dual core and 2gb ram. It opens fast just not as snappier as win xp or thunar. thats all, it just makes the experience so much better when you open folders like thunar. If i could just totally replace nautilus with thunar problem solved

---

### Post by bodhi.zazen on 2010-11-26
> **Juand_au said:**
> Well its not really that slow, i just want it like thunar, thunar is just like windows, i dont really think that there is a problem, its just the way it is, because i tried thunar and it acts just like window, you click and instantly open, great!!! my pc is a dell 1.4 ghz dual core and 2gb ram. It opens fast just not as snappier as win xp or thunar. thats all, it just makes the experience so much better when you open folders like thunar. If i could just totally replace nautilus with thunar problem solved

I suggest you either perform a minimal install and then install gnome (rather then ubuntu-desktop) or try Xubuntu.

If you want to go lighter still, try Lubuntu (LXDE is openbox plus the LXDE panel) or Fluxbox.

---

### Post by notte on 2010-11-27
> **Juand_au said:**
> Hey i tried that and it works, only that i lost all my desktop items, any ideas????

If you used pcmanfm probably have an old version which managed the desktop. Go to preference and check, I cannot remember which is the correct tab, but it should be clearly visible.

Actual version needs to be started with the --desktop option to show it.
I remember there was an option like pcmanfm -nodesktop, try using this.

If you didn't use pcmanfm... I have no idea, since i don't believe that thunar has got its own desktop.

---

