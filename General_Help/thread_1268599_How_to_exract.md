---
title: "How to exract"
date: 2009-09-17
forum: General Help
---

### Post by TUXOR21 on 2009-09-17
hi all, i just downloaded  one movie which is split up in 4 rars password protected and I want to help me with howto extract these files!! I tried everything archive manager, winrar through wine, xarchiver but nothing...
help!

THanks in advance

---

### Post by ubongo2008 on 2009-09-17
sudo apt-get install unrar

---

### Post by bryncoles on 2009-09-17
do you know the password? at what point do the files fail to extract?

---

### Post by TUXOR21 on 2009-09-17
> **ubongo2008 said:**
> sudo apt-get install unrar

yes and then what..?

---

### Post by khelben1979 on 2009-09-17
Well.. if you don't know the password then there's nothing you can do. Do you?

```
man unrar
```

---

### Post by TUXOR21 on 2009-09-17
> **bryncoles said:**
> do you know the password? at what point do the files fail to extract?

yes I know hte password. wait I upload you a screenshot with the error

---

### Post by wojox on 2009-09-17
Open a terminal and go to the directory the movie is in:

```
unrar e filename.rar
```

It should ask for a password.

---

### Post by rob-ward on 2009-09-17
I beleive that all you need to do is run the command:

```
unrar -e YOURRARFILE
```

this will then ask you for a password(I think, its being a while)

---

### Post by TUXOR21 on 2009-09-17
here is the screenshot with the error of Archive Manager: [http://i32.tinypic.com/2e5veop.png](http://i32.tinypic.com/2e5veop.png) 
here is the screenshot with the error of Winrar (through Wine): [http://i26.tinypic.com/icuwsg.png](http://i26.tinypic.com/icuwsg.png)

---

### Post by bryncoles on 2009-09-17
Ah! Try re-downloading the second part of the archive - I think it might be corrupted.

---

### Post by TUXOR21 on 2009-09-17
thanks!prob solved!

---

### Post by bryncoles on 2009-09-17
Thread tools -> solved? And what was the issue in the end? Duff download? Post for future generations posterity please!

Also: Yay! Problem solved! ;)

---

### Post by TUXOR21 on 2009-09-17
> **bryncoles said:**
> Thread tools -> solved? And what was the issue in the end? Duff download? Post for future generations posterity please!

Also: Yay! Problem solved! ;)

the prob is that the 2nd file rar was broken. Archive manager works perfectly i tried it by extracting some other rar files.

---

