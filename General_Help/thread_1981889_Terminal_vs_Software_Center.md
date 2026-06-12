---
title: "Terminal vs Software Center"
date: 2012-05-17
forum: General Help
---

### Post by jantonio2992 on 2012-05-17
Hello,

   First of all, I'm sorry if this has been asked somewhere else, but I didn't find it, and sorry if my English isn't the most correct.

   Secondly this is merely a question and not really an urgent help request :)

   I would like to know if using the software center for installing for example guake is the same as doing something like' ```
apt-get guake
``` '(i don't know if this is the correct name of the package)

Also i would like to know if its possible to keep the normal default ubuntu looks(colours/icons and such), but be able to put icons in the top bar to call software, much like the unity bar but without all that fancy effects.. kinda like xubuntu menus. Loosing the unity bar isn't a big deal i think im usually starting all my programs with terminal command :$, nor i use desktop icons.

My linux experience isn't that much... i guess from reading the above its quite noticeable..

thank you in advance.

---

### Post by forrestcupp on 2012-05-17
Assuming there is a package called 'guake', the correct command to install it would be
```
sudo apt-get install guake
```and that would be exactly like searching for it in the Software Center and installing it. The Software Center is really like a nice graphical front end for apt, with extra features.

As for your 2nd question, you might be better off installing Gnome Classic.
```
sudo apt-get install gnome-session-fallback
```Then you'll have to choose Gnome Classic next time you log in.

---

### Post by Vereinfachen on 2012-05-17
But sometimes the Software-Center doesn't find packages. So instead of installing them via apt-get you can also use Synaptic, a nice Package Management GUI.

---

### Post by oldos2er on 2012-05-17
Both the Software Center and apt-get use the same source file(s), /etc/apt/sources.list and /etc/apt/sources.list.d/*.list ; however using search in Software Center will by default hide any non-application results: [https://wiki.ubuntu.com/SoftwareCenter#Searching](https://wiki.ubuntu.com/SoftwareCenter#Searching)
Synaptic and apt-cache search don't hide any info from the user.

---

### Post by idoitprone on 2012-05-17
> **jantonio2992 said:**
> Hello,

   First of all, I'm sorry if this has been asked somewhere else, but I didn't find it, and sorry if my English isn't the most correct.

   Secondly this is merely a question and not really an urgent help request :)

   I would like to know if using the software center for installing for example guake is the same as doing something like' ```
apt-get guake
``` '(i don't know if this is the correct name of the package)

Also i would like to know if its possible to keep the normal default ubuntu looks(colours/icons and such), but be able to put icons in the top bar to call software, much like the unity bar but without all that fancy effects.. kinda like xubuntu menus. Loosing the unity bar isn't a big deal i think im usually starting all my programs with terminal command :$, nor i use desktop icons.

My linux experience isn't that much... i guess from reading the above its quite noticeable..

thank you in advance.

you should use the synaptic package manager

```
sudo apt-get install synaptic
```

you can run in from the terminal
```
sudo synaptic
```

or search synaptic

---

### Post by forrestcupp on 2012-05-18
> **oldos2er said:**
> Both the Software Center and apt-get use the same source file(s), /etc/apt/sources.list and /etc/apt/sources.list.d/*.list ; however using search in Software Center will by default hide any non-application results: [https://wiki.ubuntu.com/SoftwareCenter#Searching](https://wiki.ubuntu.com/SoftwareCenter#Searching)
Synaptic and apt-cache search don't hide any info from the user.

In my experience, sometimes it hides applicable results, too.

---

### Post by lolpenguin on 2012-05-18
[FONT="Courier New"]aptitude[/FONT] is the recommended method for installing packages in Debian. It is a text-based application, though a highly-unstable GTK+ frontend is being developed. I really prefer synaptic though.

---

### Post by woxuxow on 2012-05-18
For new user to ubuntu software center is the best way to manage packages 
in my opinion apt-get is much better than software center and is as good as synaptic

---

### Post by oldos2er on 2012-05-18
> **lolpenguin said:**
> [FONT="Courier New"]aptitude[/FONT] is the recommended method for installing packages in Debian. It is a text-based application, though a highly-unstable GTK+ frontend is being developed. I really prefer synaptic though.

aptitude has some problems with multiarch ([https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768)), so if you need to install 32-bit programs on your 64-bit install, use apt-get instead.

---

### Post by roelforg on 2012-05-23
Call me old, but, for me, every action that requires a mouse is 10x slower than it's cli counterpart.

---

### Post by zombifier25 on 2012-05-23
> **roelforg said:**
> Call me old, but, for me, every action that requires a mouse is 10x slower than it's cli counterpart.

And I thought I'm the only person... When I want to copy files, unzipping stuffs, I always pop up Guake (a drop down terminal) and do it, instead of the graphical way.

---

### Post by markbl on 2012-05-23
> **Vereinfachen said:**
> But sometimes the Software-Center doesn't find packages. So instead of installing them via apt-get you can also use Synaptic, a nice Package Management GUI.
This is annoying. Does anybody know why ubuntu software center doesn't use the full apt repositories in /etc/apt/sources.list + /etc/apt/sources.list.d/?

For this reason, I just never bother with software center and always use synaptic or aptitude.

---

### Post by MG&amp;TL on 2012-05-23
> **markbl said:**
> This is annoying. Does anybody know why ubuntu software center doesn't use the full apt repositories in /etc/apt/sources.list + /etc/apt/sources.list.d/?

For this reason, I just never bother with software center and always use synaptic or aptitude.

Does your average user want to know about libx, liby, and libz? I doubt it. I think you can turn that on though.

---

