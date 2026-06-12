---
title: "HELP!!!! Can't login!!!!"
date: 2006-02-02
forum: General Help
---

### Post by CYNY on 2006-02-02
i've just installed ubuntu 5.10 on my PC, but after i type in the username and password, a "ubuntu rectangle" pops up and the screen freezes, anyone knows what should i do to make it work?????

---

### Post by dcstar on 2006-02-03
[QUOTE=CYNY]i've just installed ubuntu 5.10 on my PC, but after i type in the username and password, a "ubuntu rectangle" pops up and the screen freezes, anyone knows what should i do to make it work?????[/QUOTE]
Does the "rectangle" say anything?

Press CTRL-ALT-F1 **and see if you get a text login screen, then try to log in and report back the results.**

---

### Post by CYNY on 2006-02-03
i've login from the text login screen, but what should i do after that???? and the "rectangle" i was talking about has the "ubuntu logo" in it. i also hear music when the rectangle box shows up, so my guess is that is the start up screen.

---

### Post by dcstar on 2006-02-03
[QUOTE=CYNY]what should i do after pressing Ctrl+Alt+F1???? and the "rectangle" i was talking about has the "ubuntu logo" in it. i also hear music when the rectangle box show s up, so my guess is that is the start up screen.[/QUOTE]
Do what I said in the other post.

---

### Post by CYNY on 2006-02-04
after i typed my name and password in the text login screen, the following appears:

[B]Last login: Fri Feb 3 18:17:15 2006 on :0
Linux Linux 2.6 12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GUN/Linux

The programs included with Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

charles@Linux:~$[/B]

(charles is my login name)

---

### Post by Protex on 2006-02-04
Well that means that you are logged in.

Try typing 'startx' from that command line and tell us what happens.

---

### Post by CYNY on 2006-02-04
after i typed "startx" the following appears:

[B]xauth: creating new authority file /home/charles/.serveranth.7914

Fatal server error: 
Server is already active for display 0
If this server is no longer running, remove /temp/.xo-lock

please consult the The X.Org Foundation support at [http://wiki.X.Org](http://wiki.X.Org) 
for help[/B]

then after about 5 seconds,

[B]xlib: connection to ":0.0" refused by server
xlib: Invalid MIT-MAGIG-COOKIR-1 key give up.
xinit: unable to connect to X server
cint: No such process (errno3): Server error[/B]

what should i do???

---

### Post by Protex on 2006-02-04
Before 'startx', write in 'sudo /etc/init.d/gdm stop' (I think?). Then try 'startx' again.

---

### Post by CYNY on 2006-02-06
still cant work, i took some pictures of the problem but cant post it, anyone knows how???

---

