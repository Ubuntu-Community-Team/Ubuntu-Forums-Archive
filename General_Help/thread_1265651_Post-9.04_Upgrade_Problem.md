---
title: "Post-9.04 Upgrade Problem"
date: 2009-09-13
forum: General Help
---

### Post by Techrocket9 on 2009-09-13
I have a Ubuntu install that I upgraded from 8.04 to 8.10 and now finally to 9.04. After upgrading to 9.04, I have had some major problems. I don't really know how to describe them, so I took pictures of each major stage of the boot process. They are below:

[IMG]http://imgur.com/bAScTl.jpg[/IMG]
[IMG]http://imgur.com/dQO9Ml.jpg[/IMG]

Please note that the screen flashes a few times on this screen and then goes to the one below automatically.


[IMG]http://imgur.com/9hSIbl.jpg[/IMG]
[IMG]http://imgur.com/4HHHyl.jpg[/IMG]
[IMG]http://imgur.com/gmqYLl.jpg[/IMG]
For this first group, You can view the full size versions at: [http://imgur.com/bAScT&dQO9M&9hSIb&4HHHy&gmqYLl](http://imgur.com/bAScT&dQO9M&9hSIb&4HHHy&gmqYLl)

[IMG]http://imgur.com/Te3byl.jpg[/IMG]
[IMG]http://imgur.com/k1PO1l.jpg[/IMG]
For these last two, you can view them full size at [http://imgur.com/Te3by&k1PO1l](http://imgur.com/Te3by&k1PO1l)


[SIZE=5]Anyway, after those screens, I can log in and use Ubuntu, but only in limited graphics mode :-(no Compiz)-:[/SIZE] [SIZE=5]Yes[/SIZE], [SIZE=5]I have tried the reconfigure graphics option. It did no good. Any/all help is appreciated.

Oh, btw, I only have time to work on this problem occasionally, so don't think I no longer care if I take a day or two to respond or even longer to try suggested fixes.
[/SIZE]

---

### Post by biebel on 2009-09-13
First thing I'd try is to rename xorg.conf.
Had a shedload of problems with jaunty after the upgrade too and I noticed that it actually works fine without one.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo reboot

```

---

### Post by XCan on 2009-09-14
Actually, renaming/removing xorg.conf will force Ubuntu to create a new one, i.e., starting off from a clean slate.

---

### Post by Techrocket9 on 2009-09-26
[LEFT]Thanks Biebel! The boot up problems are gone! However, now I am losing my window decorations (title bar, close button, .etc) when Visual Effects is set to anything but none. I have tried both restricted drivers available from the device drivers menu, but to no avail. Any further help is appreciated.
[/LEFT]

---

### Post by J V on 2009-09-26
Window decorations in compiz are set to on? Titlebars in compiz require window decorations

---

### Post by Techrocket9 on 2009-09-26
How can I set them to on? I can't open compiz-config settings manager.

---

### Post by J V on 2009-09-26
Yes, compiz used to be a seperate package, now its built in and they forgot the control panel (smart eh?)

sudo apt-get install compizconfig-settings-manager

---

### Post by Techrocket9 on 2009-09-26
I have it installed already. In fact, I tried reinstalling it -- to no avail. It still won't open.

---

### Post by J V on 2009-09-26
are you trying to run it from cli? the command to open it is ccsm, I thought you would look in the gui first...

---

### Post by Techrocket9 on 2009-09-26
When launching from the cli I get:
```

@Primary-Ubuntu:~$ sudo ccsm
[sudo] password for : 
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions
@Primary-Ubuntu:~$
```

---

### Post by Techrocket9 on 2009-10-03
Any further help??

---

### Post by Techrocket9 on 2009-10-04
I hate to bump repeatedly, but I still need help.

---

