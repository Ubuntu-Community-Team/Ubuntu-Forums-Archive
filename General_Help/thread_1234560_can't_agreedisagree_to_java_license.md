---
title: "can't agree/disagree to java license"
date: 2009-08-08
forum: General Help
---

### Post by gregapan on 2009-08-08
After requesting and downloading a java install on a terminal, I got the following, and ONLY the following:

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                      &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)             &#8593; 
 &#9474;                                                                      &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)      &#9618; 
 &#9474;                                                                      &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA        &#9618; 
 &#9474; PLATFORM STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO  &#9618; 
 &#9474; YOU ONLY UPON THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS         &#9618; 
 &#9474; CONTAINED IN THIS LICENSE AGREEMENT (THE "AGREEMENT").  PLEASE READ  &#9618; 
 &#9474; THE AGREEMENT CAREFULLY.  BY INSTALLING, USING, OR DISTRIBUTING      &#9618; 
 &#9474; THIS SOFTWARE, YOU ACCEPT ALL OF THE TERMS OF THE AGREEMENT.         &#9618; 
 &#9474;                                                                      &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in       &#9618; 
 &#9474; binary                                                               &#9618; 
 &#9474;     form, any other machine readable materials including, but not    &#8595; 
 &#9474;                                                                        
 &#9474;                                <Ok>  


There is no more to the window, no place to type a command, no way to read the whole agreement, nor to select Y/N or OK, or anything. 

What do I do?

---

### Post by mthalis on 2009-08-08
Are you install .bin package? I install bin file, in my situation after press several enter button I got **ok** message.

---

### Post by emeraldgirl08 on 2009-08-08
Have you tried pressing the TAB button?

---

### Post by gregapan on 2009-08-08
emeraldgirl, thanks

I'm just wondering how users are supposed to know that TAB does magical things in ubuntu.

such things are not usually left to the user's guessing skills

---

### Post by geirha on 2009-08-08
If you install with one of the graphical apt frontends, like add/remove or Synaptic, a gnome window will pop up, where you can point and click to agree to the terms. If you install with one of the console apt frontends, like aptitude or apt-get, the default is to use dialog, which is the one you saw.

You can however tell apt-get/aptitude to use a different debconf frontend by setting the DEBIAN_FRONTEND environment variable.

```
sudo DEBIAN_FRONTEND=gnome apt-get install sun-java6-jre
```

See [http://manpages.ubuntu.com/manpages/jaunty/en/man7/debconf.7.html](http://manpages.ubuntu.com/manpages/jaunty/en/man7/debconf.7.html) for more info.

---

### Post by 3rdalbum on 2009-08-08
> **gregapan said:**
> emeraldgirl, thanks

I'm just wondering how users are supposed to know that TAB does magical things in ubuntu.

such things are not usually left to the user's guessing skills

The idea is that if you're installing packages from the command-line, then you're probably administering a server and will know about the Tab key from other Curses-based programs.

If you're a desktop user you would be using Synaptic or some other GUI frontend, in which case you'll get a proper GUI dialog.

---

### Post by slakkie on 2009-08-08
I always hit q, since it is either less or more as a pager. Then you get the option to hit y/n.

---

### Post by starcannon on 2009-08-08
I just install using synaptic, and get a nice little mouse click accept button.

---

### Post by CatKiller on 2009-08-08
> **gregapan said:**
>  I'm just wondering how users are supposed to know that TAB does magical things in ubuntu.

such things are not usually left to the user's guessing skills

It does "magical" things in **every** operating system. The fact that you don't know this can hardly be laid at Ubuntu's door.

As starcannon points out, if you use Synaptic you get the kind of dialogue that you may be more familiar with.

---

### Post by dcstar on 2009-08-08
> **geirha said:**
> If you install with one of the graphical apt frontends, like add/remove or Synaptic, a gnome window will pop up, where you can point and click to agree to the terms. If you install with one of the console apt frontends, like aptitude or apt-get, the default is to use dialog, which is the one you saw.

You can however tell apt-get/aptitude to use a different debconf frontend by setting the DEBIAN_FRONTEND environment variable.

```
sudo DEBIAN_FRONTEND=gnome apt-get install sun-java6-jre
```

See [http://manpages.ubuntu.com/manpages/jaunty/en/man7/debconf.7.html](http://manpages.ubuntu.com/manpages/jaunty/en/man7/debconf.7.html) for more info.

```
sude dpkg-reconfigure debconf
```

---

### Post by gregapan on 2009-08-09
i  disagree, catkiller.
When tab does things in other OS, YOU CAN ALSO USE YOUR MOUSE.

---

### Post by CatKiller on 2009-08-09
> **gregapan said:**
> i  disagree, catkiller.
When tab does things in other OS, YOU CAN ALSO USE YOUR MOUSE.

Not always. The mouse isn't always available. When you're doing things in the Windows equivalent of Terminal (I think they call it a Console, although I haven't used Windows in quite some time so I can't remember for sure), you can't use the mouse either. Your lack of knowledge about how to interact with a keyboard-based interface is not Ubuntu's fault. But you've learned how now, so you won't have that problem again.

---

