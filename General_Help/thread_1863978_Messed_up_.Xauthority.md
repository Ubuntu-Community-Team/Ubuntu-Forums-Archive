---
title: "Messed up .Xauthority"
date: 2011-10-18
forum: General Help
---

### Post by blinxwang on 2011-10-18
[FONT=Calibri][SIZE=3]Hello,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I messed up my~/. Xauthority file yesterday when I couldn’t log in. I removed it using sudo rm –rf since it was owned by root (and hence I couldn’t log in). Now, I log in and I can’t mount my disk drives or use anything that requires “administrator level” access (excluding sudo). How can I fix this and rebuild the .Xauthority file to the default state? Thanks in advance![/SIZE][/FONT]

---

### Post by flangemonkey on 2011-10-18
[http://manpages.ubuntu.com/manpages/hardy/man1/xauth.1.html]("http://manpages.ubuntu.com/manpages/hardy/man1/xauth.1.html")

The gist  seems to be to run 

```

sudo xauth generate :0 . trusted

```

good luck :)

---

### Post by blinxwang on 2011-10-18
> **flangemonkey said:**
> [http://manpages.ubuntu.com/manpages/hardy/man1/xauth.1.html]("http://manpages.ubuntu.com/manpages/hardy/man1/xauth.1.html")

The gist  seems to be to run 

```

sudo xauth generate :0 . trusted

```

good luck :)

Thanks, that did the trick!:p

---

### Post by flangemonkey on 2011-10-18
glad to be of service :)

---

