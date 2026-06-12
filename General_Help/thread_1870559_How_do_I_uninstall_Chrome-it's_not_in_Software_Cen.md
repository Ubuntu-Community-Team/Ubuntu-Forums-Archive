---
title: "How do I uninstall Chrome-it's not in Software Center installed programs list?"
date: 2011-10-27
forum: General Help
---

### Post by pretty_whistle on 2011-10-27
How do I uninstall Chrome-it's not in Software Center installed programs list?

I probably have to use terminal, but how?

---

### Post by veggis on 2011-10-27
installed from repositories or downloaded?

---

### Post by oldtimer7777 on 2011-10-27
> **pretty_whistle said:**
> How do I uninstall Chrome-it's not in Software Center installed programs list?

I probably have to use terminal, but how?

You go step by step with a walkthough like this:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by Gawains Green Knight on 2011-10-27
If it was downloaded it would be as a deb file.... if it was opened by software center it should still be there? Apt-get is the command line program for this kind of thing....

---

### Post by pretty_whistle on 2011-10-27
> **veggis said:**
> installed from repositories or downloaded?
I don't recall unfortunately.  But it's listed in the Application>Internet menu.

Oh yeah.  I have Ubuntu 11.04.
I forgot to add that.

---

### Post by collisionystm on 2011-10-27
> **pretty_whistle said:**
> How do I uninstall Chrome-it's not in Software Center installed programs list?

I probably have to use terminal, but how?


sudo apt-get remove google-chrome

---

### Post by pretty_whistle on 2011-10-27
> **collisionystm said:**
> sudo apt-get remove google-chrome

Thanks.

---

### Post by pretty_whistle on 2011-10-27
I used this:

> sudo apt-get remove google-chrome

... and got a funny message:

> Virtual programs like google-chrome cannot be removed.


What's that about?

---

### Post by veggis on 2011-10-27
see if this help
[http://ubuntuforums.org/showthread.php?p=8868755](http://ubuntuforums.org/showthread.php?p=8868755)

---

### Post by pretty_whistle on 2011-10-27
> **veggis said:**
> see if this help
[http://ubuntuforums.org/showthread.php?p=8868755](http://ubuntuforums.org/showthread.php?p=8868755)

Thanks I tried this and it said no installed package by that name:

> sudo dpkg -r google-chrome

Guess it's gone then.  GOOD.

---

