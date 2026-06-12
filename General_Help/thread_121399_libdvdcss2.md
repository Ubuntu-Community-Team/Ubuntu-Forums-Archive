---
title: "libdvdcss2"
date: 2006-01-25
forum: General Help
---

### Post by BruschiOnTap on 2006-01-25
When I try to get libdvdcss or libdvdcss2 I get the message 'libdvdcss has no installation candidate'

Meanwhile my media player says I need this to play my DVDs...

---

### Post by tseliot on 2006-01-25
It's proprietary.
Use Automatix, it will install it for you: [ Automatix: Automated Graphical Installer and Tweaker]("http://www.ubuntuforums.org/showthread.php?t=80295")

---

### Post by BruschiOnTap on 2006-01-25
Ok I got automatix but the dpkg command doesn't do anything so it's not actually installed on my system... at any rate, it's not where that thread says it should be (applications-->system tools)

---

### Post by Perfect Storm on 2006-01-25
another way around is to:

```

sudo gedit /etc/apt/sources.list

```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by BruschiOnTap on 2006-01-25
Huzzah!  Success!  Only one other question: how do I get this automatix thing to go?  It says it installs or comes with all sorts of cool capabilities but I don't know how to access them... sorry, I'm very new to linux and need things explained like I'm a 4-year-old

---

### Post by Perfect Storm on 2006-01-25
Depends what you want to install. If you enable universe, multiverse and have PLF, I don't see much need of automatix (my personal opinion).

Now you have PLF enable you can do:

```
sudo apt-get install sun-j2re1.5
```
for java

or 

```
sudo apt-get install w32codecs
```

for playing window format files.

---

