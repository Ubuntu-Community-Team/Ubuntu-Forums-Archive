---
title: "Can the desktop also act as an apache server out of the box?"
date: 2009-10-23
forum: General Help
---

### Post by wyattbiker on 2009-10-23
I want to setup my own Ubuntu web/network server but I have a dilemma.

I like to use all the end user GUI based tools and GUI of the desktop.

Can the desktop function as a server out of the box or do I need to install LAMP.

Also, does the server version include the GUI and end user tools installed or do they have to be downloaded and installed. When installing it do you have an option to install all the desktop's facilities?


Thanks

---

### Post by Giblet5 on 2009-10-23
No.

You have to install a couple of packages onto the desktop edition that install at the outset on the server edition. This will provide what LAMP provides: ```
sudo apt-get install apache2 mysql-server php5-dev php5-cli
```

The server edition makes an excellent desktop environment.

You can have it either way.

---

### Post by rockstarrem on 2009-10-23
Yeah, if you want to do it that way I'd install the server then afterwards install the desktop. I did that for one of my home PC's.

Basically, install the server with everything you need, then:

```

sudo apt-get install ubuntu-desktop

```

It will take a while, but it's probably what you want.

---

### Post by nicol_bolas on 2009-10-23
> **rockstarrem said:**
> Yeah, if you want to do it that way I'd install the server then afterwards install the desktop. I did that for one of my home PC's.

Basically, install the server with everything you need, then:

```

sudo apt-get install ubuntu-desktop

```

It will take a while, but it's probably what you want.

+1 to this method.

---

### Post by wyattbiker on 2009-10-24
Would be nice if it was one install and just choose options.  But i like the server method idea.   --thanks

---

