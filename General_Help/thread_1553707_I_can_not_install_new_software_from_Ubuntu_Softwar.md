---
title: "I can not install new software from Ubuntu Software Center"
date: 2010-08-15
forum: General Help
---

### Post by tc101 on 2010-08-15
I am running 10.04.  I go to Applications/Ubuntu Software Center.  I select something to install and click the install  button.  Nothing happens. 

How do I debug?

Synaptic works.

---

### Post by snowpine on 2010-08-15
What is the name of the app you're trying to install? Let's try installing it from the Terminal. Copy & paste the output here so we can see what's going on.

```
sudo apt-get update
sudo apt-get install foo
```

Replace "foo" with the actual name of the app you're trying to install. :)

---

### Post by celldweller1591 on 2010-08-15
> What is the name of the app you're trying to install? Let's try  installing it from the Terminal. Copy & paste the output here so we  can see what's going on.

 	Code:
 	sudo apt-get update
sudo apt-get install foo 
Replace "foo" with the actual name of the app you're trying to install. :smile:

This one is a good way...Better yet to try Synaptic, type your package in search and click "apply"

---

### Post by tc101 on 2010-08-15
How do I get the correct name?  For example the first game listed, 20,000 Light years into space.  What would be the name that I replace "foo" with?

---

### Post by snowpine on 2010-08-15
> **tc101 said:**
> How do I get the correct name?  For example the first game listed, 20,000 Light years into space.  What would be the name that I replace "foo" with?

It's called "lightyears."

[http://packages.ubuntu.com/lucid/lightyears](http://packages.ubuntu.com/lucid/lightyears)

---

### Post by tc101 on 2010-08-15
I just installed the game "Abuse" from the command line using your instructions and it worked fine.  Earlier I installed the html editor Kompozer from synaptic and it worked fine.  There seems to be something wrong with the software center.

Or maybe I just need to wait longer.  When you click the install button, does it do anything or do you just wait  a few minutes while it installs?

---

### Post by tc101 on 2010-08-15
I  pressed the install button for  the game "Abe's amazing adventures" about  3 minutes ago.  The  install button is greyed out. Nothing is happening.  I assume it  is not working.

---

### Post by tc101 on 2010-08-15
> **snowpine said:**
> It's called "lightyears."

[http://packages.ubuntu.com/lucid/lightyears](http://packages.ubuntu.com/lucid/lightyears)

How did you know that?  How could I get that info from Ubuntu Software Center?

---

### Post by snowpine on 2010-08-15
> **tc101 said:**
> How did you know that?  How could I get that info from Ubuntu Software Center?

I Googled it. I've never used Ubuntu Software Center before in my life, sorry I can't be more help in that department. ;)

---

### Post by tc101 on 2010-08-15
> I Googled it. I've never used Ubuntu Software Center before in my life, sorry I can't be more help in that department.

Thanks anyway.  I  can just use synaptic.  Maybe someone will come along and explain the problem with Ubuntu Software Center.  I am curious but don't need to use it.

---

### Post by -Robert- on 2010-08-15
Do you get error messages when you start Ubuntu Software Center from a terminal?

Command:

```
software-center
```

---

### Post by tc101 on 2010-08-15
Yes, this is what I get

> tomcarr@tomcarr-desktop:~$ software-center
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()


Then software center comes up

---

### Post by -Robert- on 2010-08-15
I am getting the same message so I don't think there is any harm in it.

This topic looks a bit like your problem: [http://ubuntuforums.org/showthread.php?t=1500473](http://ubuntuforums.org/showthread.php?t=1500473)

What happens when you start the software center with **gksudo software-center** Are you able to install apps?

---

### Post by tc101 on 2010-08-15
That worked.  Then I read the thread you pointed to and did this:

> Easiest way to fix Ubuntu Software Center. Go to: System> Prefs> Main Menu> highlight the Software center, click properties> add "gksudo" without quotes to the beginning of the Command

And it seems to be working.

Thanks

---

### Post by -Robert- on 2010-08-15
Glad it worked, you're welcome.

---

