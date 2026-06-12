---
title: "Autostart script"
date: 2006-04-03
forum: General Help
---

### Post by GregaS on 2006-04-03
Everytime I turn on my PC I have to run webserver from console by entering: 

sudo /opt/lampp/lampp start

What do I have to do, to start this command when computer boots up :-k 

PS: Sorry for my english.

---

### Post by niviche on 2006-04-03
Download the [Autostart application](http://www.kde-apps.org/content/show.php?content=35038). Right click on it, and install the package.

You can then go to your KDE settings and chose the script to run at startup.

---

### Post by GregaS on 2006-04-03
Which script?

---

### Post by niviche on 2006-04-03
[QUOTE=GregaS]Which script?[/QUOTE]

```

sudo /opt/lampp/lampp start

```

---

### Post by njf on 2006-04-03
Just go to ~/.kde/Autostart folder, "Create New" -> "Link to Application..." and put the
sudo /opt/lampp/lampp start
in the command field. 
And also go to "Advanced Options", untick "Enable launch feedback", if you doesn't like it ;) .

---

### Post by GregaS on 2006-04-04
[QUOTE=njf]Just go to ~/.kde/Autostart folder, "Create New" -> "Link to Application..." and put the
sudo /opt/lampp/lampp start
in the command field. 
And also go to "Advanced Options", untick "Enable launch feedback", if you doesn't like it ;) .[/QUOTE]

It's not working!

---

### Post by njf on 2006-04-04
[QUOTE=GregaS]It's not working![/QUOTE]

It's not? It works for me ... :-k 

Nvm then, just make a executable shell script with that ```
sudo /opt/lampp/lampp start
```
and put it in the Autostart folder.

ADDED:
Or download the application as niviche suggested, and choose to run the shell script i mentioned above (though i suppose you can directly invoke command from there, no time to test it...).

---

### Post by GregaS on 2006-04-04
I have downloaded Autostart application but I can't run it. How do I make executable script?

---

### Post by njf on 2006-04-04
Open the Autostart folder in Konqueror, right click to make the context menu pop up, go to "Create New" -> "Text File".  Type any filename you want.

Open the text file with Kate, and type the "sudo /opt/lampp/lampp start" in it.

Then in Konqueror right click on the file and select "Properties". In the "Permissions" tab, tick the "Is executable" checkbox.

---

### Post by GregaS on 2006-04-04
[QUOTE=njf]Open the Autostart folder in Konqueror, right click to make the context menu pop up, go to "Create New" -> "Text File".  Type any filename you want.

Open the text file with Kate, and type the "sudo /opt/lampp/lampp start" in it.

Then in Konqueror right click on the file and select "Properties". In the "Permissions" tab, tick the "Is executable" checkbox.[/QUOTE]

If I do that, nothing happens except kate opens with that line:

sudo /opt/lampp/lampp start

---

### Post by njf on 2006-04-04
At the start of the file, add 
```
#!/bin/sh
```

---

### Post by GregaS on 2006-04-06
Still not working.

---

### Post by niviche on 2006-04-06
What are the permissions of your text file in the Autostart folder (right click to see this)? It has to be executable, I think.

---

### Post by GregaS on 2006-04-06
It is.

---

### Post by niviche on 2006-04-06
Does it work now?

---

### Post by GregaS on 2006-04-06
Nope.

---

### Post by GregaS on 2006-04-09
Anyone?

---

### Post by GeneralZod on 2006-04-09
This doesn't work because sudo requires user input (i.e. - your password!).

You can do what you want using suid, but there are horrible security [risks](http://www.samag.com/documents/s=1149/sam0106a/0106a.htm) to doing this.

If you want it to start up on *boot*, then using KDE's autostart is sub-optimal, as this will start it everytime you start KDE (and *only* when you start KDE).  It would be far better to add it as an init script; see e.g. [here](http://www.debian-administration.org/articles/28) for more info.  "sudo" should not be used as scripts run in this way automatically have root priviledges.

Note that running a webserver as root is an incredibly - *incredibly* - bad idea, security-wise, and I'd *strongly* advise that you run it as a limited user.  You can downgrade to running it as a limited user by doing (I think)

```

sudo -u **limitedusername** opt/lampp/lampp start

```

---

### Post by GregaS on 2006-04-09
I would really like to start webserver at boot but I don't know how to write a script :(

---

### Post by incubus on 2006-04-09
This is a little dirty trick that I used to do for lampp (I stopped using it).

1. Have it installed. It's probably in /opt/lampp as you described (the default place).

2. Create a link to the script in the init.d directory:
```

$ sudo ln -sf /opt/lampp/lampp /etc/init.d/

```

3. Update the initscripts:
```

$ sudo update-rc.d -f lampp defaults

```

That should do the trick. You can also start/stop/restart with:
```

$ sudo invoke-rc.d lampp [start|stop|restart]

```

If you want to remove the auto-start behavior:
```

$ sudo update-rc.d -f lampp remove
$ sudo rm -f /etc/init.d/lampp

```

Note that this will make it for the whole system, not just for your user. But I hope it helps.
By the way, you probably know that installing Apache2, MySQL, PHP, phpmyadmin, etc in Ubuntu is also very easy.

incubus

---

### Post by GregaS on 2006-04-11
Thank you very much. It worked.

---

