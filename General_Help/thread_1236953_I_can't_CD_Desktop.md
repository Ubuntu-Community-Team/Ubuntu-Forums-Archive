---
title: "I can't CD /Desktop"
date: 2009-08-10
forum: General Help
---

### Post by Pepse3 on 2009-08-10
I am running KUBUNTU 8.04.  I downloaded Google Earth and I can't install it as I Googled that problem and was told to " cd -/Desktop ".  I did that (in a terminal, of course) and I got bashed: bash: cd: -/: invalid option
cd: usage: cd [-L|-P] [dir]  .  Of course I have no idea why it doesn't work.  I also created a folder in /Home and I can't even CD to that either.  

Later. Pepse.

---

### Post by theozzlives on 2009-08-10
It's ~ not -.

---

### Post by Pepse3 on 2009-08-10
I tried it minus the " - " and I still get bashed.

Pepse.

---

### Post by doorknob60 on 2009-08-10
Try either
```
cd ~/Desktop
```
or
```
cd $HOME/Desktop
```
or
```
cd Desktop
```

They should all work if typed right, although the last one will only work if you're in your home folder (which is usually where your terminal defaults to though).

---

### Post by cwbar_1 on 2009-08-10
[http://en.wikipedia.org/wiki/Tilde](http://en.wikipedia.org/wiki/Tilde)

It's not a minus sign.  The tilde "~" represents your home directory.  For example, if my home directory were "dave" I could type cd /home/dave/Desktop or I could type cd ~/Desktop.

---

### Post by Pepse3 on 2009-08-10
That is what I was missing.  The site that gave the command for doing so had the - not the ~ .  I missed the tilde in the first reply.  

  Thanx.  Now wish me luck once I attempt to run Google Earth.

Later. Pepse.

---

