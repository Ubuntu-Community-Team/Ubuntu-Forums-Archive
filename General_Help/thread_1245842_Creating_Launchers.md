---
title: "Creating Launchers"
date: 2009-08-21
forum: General Help
---

### Post by coldfusion1313 on 2009-08-21
How do you find the the command of a application and a location?

---

### Post by bchurchill on 2009-08-21
There are a few tools you can use.  If the program is already in the applications menu, you can recreate it using the 'Application Launcher' instead of 'Custom Application Launcher'.

Otherwise, if you know the name of the program you can use

```

$ locate <program-name>

```

Note that the database that locate uses is updated daily, so you may need to manually update it with

```

$ sudo /etc/cron.daily/mlocate

```

If you're looking for help on command line arguments you can use

```

$ man <program name>

```

If you don't know the name of the program that you installed you'll need to do some searching.  The find command allows this if you know part of the name.  For example, if you know that the name contains the phrase "firefox" in it, you could do something like

```

cd /usr
find -name "*firefox*" | grep bin

```

and this will search for everything in a bin directory (where programs are stored) that contains the name firefox.  Similarly you can use locate with grep bin as well, eg.

```

locate firefox | grep bin

```

Hope that helps.

---

### Post by coldfusion1313 on 2009-08-21
This helps but I am confused, I have programs install but they are not in the menu. One of them is apache2 and I need get to it. Like the command to put it on the desktop.

---

### Post by Bonster on 2009-08-21
just go to the synaptic and look at the name. To locate use the 'whereis' command Ex: whereis firefox

---

### Post by bchurchill on 2009-08-21
> **coldfusion1313 said:**
> This helps but I am confused, I have programs install but they are not in the menu. One of them is apache2 and I need get to it. Like the command to put it on the desktop.

apache2 is a webserver that you usually don't start using a quick-launch button.  Rather, the apache server is a daemon that runs at startup. I've never used it myself, but it seems that /etc/init.d/apache2 is the daemon.  If you need to restart it you can use 

```
sudo /etc/init.d/apache2 restart
```

otherwise it's probably already running... try directing your browser to [http://127.0.0.1](http://127.0.0.1).  From what I'm reading, it looks like your files will be in /var/www.

---

