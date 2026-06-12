---
title: "Three (hopefully simple) new user questions:"
date: 2006-03-26
forum: General Help
---

### Post by Nrbelex on 2006-03-26
Hi, I'm fairly new to Ubuntu and I have three quick questions:

1. I tried to share a folder by right clicking and selecting "share folder" and then the Samba package was installed. However, Windows on my other computer still does not recognize the folders. I can't find a how-to guide for Samba on this version of Ubuntu...

2. I tried to download the BZtanks package but when I click on the icon under games, nothing happens. I also downloaded the server package in an attempt to fix it but don't know if that will help...

3. I downloaded some airplane game package and by navigating through usr -> games, I was able to launch it but it was not under applications -> games. Why is that and how can I fix it?

Thanks!

~ Brett

---

### Post by Henry Rayker on 2006-03-26
Let me take a stab at #3

In order to add files to the applications menu, you need to go to applications -> system tools -> applications menu editor

next, click games in the left pane and under the right hand pane, click new entry

next, you need to know the name of the executable (I'm assuming you do, because you found it in usr->games) enter this in the command field. enter the name of whatever you want to add, as well as a comment, if you want.

now for the part that fooled me for the longest ](*,) 
you need to find the icon that corresponds to the program. I don't know an easy way to do this. you could use places->search for files... and try to find a .png file (at least mine was .png) and use this for the icon.

I hope that helps you out.

As for 1 and 2, I'm not 100% sure. I'm still new to ubuntu and non-windows OSes, myself.

---

### Post by Nrbelex on 2006-03-26
Thanks! That solved #3. Does that process need to occurr often? Still need help with 1 & 2...

Thanks!

~ Brett

---

### Post by Trab on 2006-03-26
no, it only happens with packages that arnt always configured for either Gnome, Ubuntu, or just poorly packaged...
sometimes u have to restart ur panels to see them tho, after reinstalling...
just type
```

killall gnome-panel

```

for #2 try running the program in a terminal, and output the erros/issues here...
#1 im sure there is a breezy howto for samaba....
check the breezy guide page (found around the forums in ppls signatures im sure... i cant find a link right now, sorry!)
or google for Samba Breezy Ubuntu

GL!
-Trab

---

### Post by Nrbelex on 2006-03-26
[QUOTE=Trab]for #2 try running the program in a terminal, and output the erros/issues here...[/QUOTE]

How do I launch a program from the terminal? And having found the how-tos on Samba, I gave up.

Thanks

~ Brett

---

### Post by Kyle- on 2006-03-26
Generally, to launch a program in the terminal, you just type the name of the program.  For example, to open AbiWord, you open a console and type
```
abiword
```
That's it!

---

### Post by Zimmer on 2006-03-26
There are many ways to configure Samba depending on your needs.
Have a look here for my thread regarding creating Samba users..

[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950) reply #5
and here for links to sharing issues..
[http://ubuntuforums.org/showthread.php?t=133100](http://ubuntuforums.org/showthread.php?t=133100) reply #4

Hope this helps...

---

### Post by Nrbelex on 2006-03-26
The Samba thing wasn't critical so I'll check those out, but unless its really easy, I'm just gonna live without it. The BZflag issue is strange through. When I tried to run it through the terminal, I'm told:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Could not set Video Mode: Couldn't find matching GLX visual.
Error creating window - Exiting
```

Thanks for the help!

~ Brett

---

### Post by syntek on 2006-03-26
it looks to me like you dont have 3D acceleration running under X. what type of video card is in the machine?

---

### Post by Nrbelex on 2006-03-26
[QUOTE=syntek]it looks to me like you dont have 3D acceleration running under X. what type of video card is in the machine?[/QUOTE]

Haha - video card... haha...

Ummm... this is a 199X Pentium II which I added a little bit of RAM to to get Ubuntu running. It's actually surprisingly snappy but I guess I'll have to take a raincheck on games like that. Thanks!

~ Brett

---

### Post by Henry Rayker on 2006-03-27
yesss. I had my first assist in this thread (too bad I'm a little late in realizing it)...glad I could help

---

### Post by Petarded on 2006-03-27
What game was it if you don't mind me asking?

---

### Post by akiro.yamamoto on 2006-03-27
[quote=Petarded]What game was it if you don't mind me asking?[/quote]

bzFlag apparently :)

---

### Post by Petarded on 2006-03-27
[QUOTE=akiro.yamamoto]bzFlag apparently :)[/QUOTE]

Don't know how in the heck I missed that:confused:. Bah, it's getting late that's my excuse, I need sleep.

:-({|= <-- Let me add one of these, I just saw it and had to use it.

Thanks by the way.

---

