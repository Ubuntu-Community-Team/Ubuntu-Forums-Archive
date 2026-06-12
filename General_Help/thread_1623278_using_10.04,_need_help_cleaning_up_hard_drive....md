---
title: "using 10.04, need help cleaning up hard drive..."
date: 2010-11-16
forum: General Help
---

### Post by jjb945025 on 2010-11-16
hello. can anyone clue me in on how to free up space on my measly 13GB HD? i tried computer janiotor, deleted downloads, and continuously empty the trash. i dont know what's taking up all the space or where to go to get rid of stuff.. please help. thank you

---

### Post by matt_symes on 2010-11-16
Hi 

Use bleachbit

Kind regards

---

### Post by windowsh8r on 2010-11-16
You can also use Disk Usage Analyzer to see what is using up your memory, it gives a graphical view of folder sizes.

---

### Post by jjb945025 on 2010-11-16
yea, i dont understand how to use it though, thanks anyway

---

### Post by cariboo on 2010-11-16
Open a terminal and type:

```
sudo apt-get clean
```

the above command will remove archived packages from /var/cache/apt/archive. Next in the same terminal type:

```
sudo apt-get autoremove
```

this command will remove any unneeded dependencies.

Running the above to commands wil remove a fair number of packages depending on how up-to-date your. Typically I reclaim anywhere from 500MB to 1Gb.

---

### Post by matt_symes on 2010-11-16
Hi

From a terminal type

sudo apt-get install bleachbit

When it installs

Applications->System tool->Bleachbit

or type 

bleachbit

at the terminal

Kind regards

---

### Post by Axis Mann on 2010-11-16
I don't know how you installed Ubuntu but if you did it like me, I upgraded to 10.04 from 9.10.  I read some wheres that the old kernel, if still present, could be removed.  I haven't tried it yet because space not yet an issue for me.  Maybe this will help you.

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

