---
title: "Remix 10.04 crashed on two computers"
date: 2010-12-14
forum: General Help
---

### Post by compmom on 2010-12-14
I have two laptops.  Both had Netboox Remix 10.04 and were running great.  Several weeks ago when I would update I would get a box saying to put Meekrat in dvd/cd.  I sort of just clicked my way around that.

Now, within hours of each other, both computers went to a gray fuzzy screen that looks almost broken.  One came back up but the desktop would not work.  Was very light and if clicked on something it would just flash on screen and be gone.

So, I reinstalled.  Got everything working.  Looking pretty.  Played around on net, got Firefox set up the way I like and remembered I needed to update after install.  After I updated (took about fifteen minutes with 300+ things it said), I restarted the computer and ......the nice gray blank but fuzzy screen.  What is going on??

Intstructions need to be basic.

Thank you.

---

### Post by fatharraxman on 2010-12-14
paste your graphic type  the following command in terminal to tell you 
```
lspci | grep VGA
```

---

### Post by compmom on 2010-12-14
> **fatharraxman said:**
> paste your graphic type  the following command in terminal to tell you 
```
lspci | grep VGA
```

claudia@claudia-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
claudia@claudia-laptop:~$

---

### Post by fatharraxman on 2010-12-14
try this link
[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by fatharraxman on 2010-12-14
You may need to check these liks too:
1-[Nvidia manual]("https://help.ubuntu.com/community/NvidiaManual")
2-[BinaryDriverHowtoNvidiaNouveau]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia/Nouveau")
3-[Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=restricted+nvidia-glx&orderby=datecreated")
good luck

---

