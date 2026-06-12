---
title: "Shockwave Flash problem..."
date: 2010-06-21
forum: General Help
---

### Post by acron1 on 2010-06-21
Hi all,

After the last Flash update I get frequent stream freezes... in addition if I right click on the Flash window I get an immediate video freeze (sound plays on):

[[IMG=http://img708.imageshack.us/img708/6626/mozilla3.png][/IMG]](http://img708.imageshack.us/i/mozilla3.png/)


Here is some important info:

[[IMG]http://img180.imageshack.us/img180/3063/mozilla2.png[/IMG]](http://img180.imageshack.us/i/mozilla2.png/)

[[IMG]http://img375.imageshack.us/img375/3979/mozilla.png[/IMG]](http://img375.imageshack.us/i/mozilla.png/)

Every time Flash freezes if I terminate npviewer.bin I can restart flash again...:

[[IMG]http://img80.imageshack.us/img80/6716/systeml.png[/IMG]](http://img80.imageshack.us/i/systeml.png/)

Thanks for looking.

---

### Post by acron1 on 2010-06-22
No one with any ideas?

---

### Post by lovinglinux on 2010-06-22
I'm not sure this will help your particular problem, but it won't hurt. It is used to fix the problem with unresponsive flash buttons.

First:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

Also see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by acron1 on 2010-06-22
> **lovinglinux said:**
> I'm not sure this will help your particular problem, but it won't hurt. It is used to fix the problem with unresponsive flash buttons.

First:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

Also see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Thanks lovinglinux but thats was added to my npviewer sometime ago... so no joy there... I just checked my desktop PC also running Ubuntu 10.04 and it also exhibits the same behavior (freezing if I right click on the flash window while playing)... can some one else try and see if this is a bug...
BTW... both laptop and desktop are running the 64 bit of lucid.

Thanks.

---

### Post by lovinglinux on 2010-06-22
> **acron1 said:**
> Thanks lovinglinux but thats was added to my npviewer sometime ago... so no joy there... I just checked my desktop PC also running Ubuntu 10.04 and it also exhibits the same behavior (freezing if I right click on the flash window while playing)... can some one else try and see if this is a bug...
BTW... both laptop and desktop are running the 64 bit of lucid.

Thanks.

Try to create a new profile and see if that helps.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by acron1 on 2010-06-22
Apparently this is a known bug:

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/592492](https://bugs.launchpad.net/ubuntu/+s...er/+bug/592492)

---

### Post by acron1 on 2010-06-23
I installed Minefield 3.7 last night and it seems to have solved the problem of right clicking, but still from time to time the stream freezes midway and I have to double click on the progress bar to get it going again...

---

