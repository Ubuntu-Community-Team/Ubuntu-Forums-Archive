---
title: "Installing gtknetcat: &quot;Your intltool is too old&quot;???"
date: 2011-02-08
forum: General Help
---

### Post by t0p on 2011-02-08
Trying to install gtknetwork (thanks for [the suggestion]("http://ubuntuforums.org/showthread.php?t=1683362"), **Caboose885**).  It isn't in the repos, so I have to go to [Sourceforge.net]("http://sourceforge.net/projects/lxde/files/GtkNetCat%20%28GUI%20for%20netcat%29/GtkNetCat%200.1/") and download the gzipped archive...

So I extract the archive contents, [i]cd/i] into the folder, and run

```
./configure
```

and the *configure* output ends with this error:

```

configure: error: Your intltool is too old.  You need intltool 0.21 or later.

```

But according to Synaptic, I currently have intltool **0.41.1-1**, which *is* later than 0.21.  Right?

Any suggestions? (A link to an intltool .deb would be wonderful... but if not that, maybe someone knows how to get round this problem?

---

### Post by t0p on 2011-02-09
bump

---

### Post by t0p on 2011-02-16
bump

Incidentally, I thought I'd found a workaround.  At [http://sisyphus.ru/en/srpm/Sisyphus/gtknetcat/get](http://sisyphus.ru/en/srpm/Sisyphus/gtknetcat/get), I found a gtknetcat rpm.  I downloaded it, ran alien on it, then used the GDebi package installer to install the resultant deb file.  GDebi now tells me that gtknetcat is now installed.  But I look in the Apps menu and there's no sign.  I type into a terminal

```

gtknetcat

```

and get told there's no such program installed.  I type

```

which gtknetcat

```

and again I'm told there's no such thing.  Likewise,

```

t0p@deimos:~$ apropos gtknetcat
t0p@deimos:~$ apropos netcat
netcat (1)           - arbitrary TCP and UDP connections and listens

```

Can anyone help?  *Pleeeze??*

---

### Post by t0p on 2011-02-18
Another, probably final, "bump".  If I don't get some help soon I'm a-gonna die!  :(

If you can't help with my gtknetcat installation, maybe you *can* advise as to a network "system monitor" for Lubuntu (LXDE).  The basic problem: When I'm using my (Gnome) Ubuntu 10.04 machine, I like the info displayed about network traffic speed etc in "System Monitor".  I'm looking for something that'll do the same thing on my (LXDE) Lubuntu computer.  Suggestions?

---

### Post by t0p on 2011-03-08
Okay, so who wants to take a bash (heh) at explaining *this*???

```

t0p@deimos:~$ gtknetcat
gtknetcat: command not found
t0p@deimos:~$ man gtknetcat
No manual entry for gtknetcat
t0p@deimos:~$ apropos gtknetcat
t0p@deimos:~$ sudo apt-get install gtknetcat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtknetcat is already the newest version.

```

---

### Post by epicbattle on 2011-10-11
Was this ever solved? I'm having the same issue.

---

