---
title: "Kernel Panic"
date: 2012-09-08
forum: General Help
---

### Post by draucia on 2012-09-08
I've tried installing skype from the .deb file from skype.com and from the ubuntu software center, but whenever I launch it, I get a kernel panic. I don't think this is caused by skype itself, but probably something related to the sound driver?

I'm running ubuntu 12.04.1 64-bit. I can post any information needed.


Btw, I'm not sure of this would fit in the multimedia section or not, but since this is more of a system problem then a multimedia problem, I posted it here.

---

### Post by idoitprone on 2012-09-08
> **draucia said:**
> I've tried installing skype from the .deb file from skype.com and from the ubuntu software center, but whenever I launch it, I get a kernel panic. I don't think this is caused by skype itself, but probably something related to the sound driver?

I'm running ubuntu 12.04.1 64-bit. I can post any information needed.


Btw, I'm not sure of this would fit in the multimedia section or not, but since this is more of a system problem then a multimedia problem, I posted it here.

kernel panic could mean alot of things. We kidda need a log

```
dmesg > dump.txt
```

attach the dump.txt to the forums

or you can post it to pastebin it
```

sudo apt-get install pastebinit

dmesg | pastebinit
```

and post the link

---

### Post by draucia on 2012-09-08
[http://paste.ubuntu.com/1193722/]("http://paste.ubuntu.com/1193722/")

---

### Post by idoitprone on 2012-09-09
> **draucia said:**
> [http://paste.ubuntu.com/1193722/](http://paste.ubuntu.com/1193722/)


i dont think the dmesg log is showing the log before you turn on the computer

look through /var/log/

and post the dmesg.log files there

---

### Post by draucia on 2012-09-09
dmesg: 

[http://paste.ubuntu.com/1194503/]("http://paste.ubuntu.com/1194503/")

dmesg.0:

[http://paste.ubuntu.com/1194505/]("http://paste.ubuntu.com/1194505/")

dmesg.1.gz:

[http://paste.ubuntu.com/1194506/]("http://paste.ubuntu.com/1194506/")

dmesg.2.gz:

[http://paste.ubuntu.com/1194512/]("http://paste.ubuntu.com/1194512/")

dmesg.3.gz:

[http://paste.ubuntu.com/1194513/]("http://paste.ubuntu.com/1194513/")

dmesg.4.gz:

[http://paste.ubuntu.com/1194515/]("http://paste.ubuntu.com/1194515/")

I know that's a lot. :/ Can you tell me what I should be looking for in dmesg files? I can look too.

---

### Post by idoitprone on 2012-09-09
> **draucia said:**
> dmesg: 

[http://paste.ubuntu.com/1194503/](http://paste.ubuntu.com/1194503/)

dmesg.0:

[http://paste.ubuntu.com/1194505/](http://paste.ubuntu.com/1194505/)

dmesg.1.gz:

[http://paste.ubuntu.com/1194506/](http://paste.ubuntu.com/1194506/)

dmesg.2.gz:

[http://paste.ubuntu.com/1194512/](http://paste.ubuntu.com/1194512/)

dmesg.3.gz:

[http://paste.ubuntu.com/1194513/](http://paste.ubuntu.com/1194513/)

dmesg.4.gz:

[http://paste.ubuntu.com/1194515/](http://paste.ubuntu.com/1194515/)

I know that's a lot. :/ Can you tell me what I should be looking for in dmesg files? I can look too.

basically, the log right before the kernel panic. It the text that dumped on the black screen when it panic.

i dont see anything unusal.

Try to reproduce the panic again and give us the log.

It should show on the black screen

here is the example

[http://www.youtube.com/watch?v=oPVGIxugeQM](http://www.youtube.com/watch?v=oPVGIxugeQM)

the last line is important

that is usually the offending device. I am surprise that it kernel panic. No application should crash the kernel

---

### Post by draucia on 2012-09-09
> **idoitprone said:**
> basically, the log right before the kernel panic. It the text that dumped on the black screen when it panic.

i dont see anything unusal.

Try to reproduce the panic again and give us the log.

It should show on the black screen

here is the example

[http://www.youtube.com/watch?v=oPVGIxugeQM](http://www.youtube.com/watch?v=oPVGIxugeQM)

the last line is important

that is usually the offending device. I am surprise that it kernel panic. No application should crash the kernel

You want the text on black when I get the kernel panic, right? Or you want me to check dmesg or something after I get a kernel panic?

EDIT: I've tried to reproduce the panic, but it doesn't seem to work. This time, whenever I open skype, my whole computer just freezes (at the point where you accept or unaccept their ToS).

---

### Post by idoitprone on 2012-09-09
> **draucia said:**
> You want the text on black when I get the kernel panic, right? Or you want me to check dmesg or something after I get a kernel panic?

EDIT: I've tried to reproduce the panic, but it doesn't seem to work. This time, whenever I open skype, my whole computer just freezes (at the point where you accept or unaccept their ToS).

hmmm [http://askubuntu.com/questions/110917/skype-causes-ubuntu-to-freeze](http://askubuntu.com/questions/110917/skype-causes-ubuntu-to-freeze)

open terminal and check top

open skype and watch the memory needs grow

they said it has a memory leak

---

### Post by draucia on 2012-09-09
> **idoitprone said:**
> hmmm [http://askubuntu.com/questions/110917/skype-causes-ubuntu-to-freeze](http://askubuntu.com/questions/110917/skype-causes-ubuntu-to-freeze)

open terminal and check top

open skype and watch the memory needs grow

they said it has a memory leak

Thanks for helping, but I've decided to remove ubuntu on this desktop. I love it and I've been using it for years on my laptop, but on this desktop it has a mid-high end graphics card (Radeon HD 6870) and the performance with fglrx or the default driver isn't very good. I hope AMD can work on their drivers to increase performance to match that of windows driver performance.

---

### Post by idoitprone on 2012-09-12
> **draucia said:**
> Thanks for helping, but I've decided to remove ubuntu on this desktop. I love it and I've been using it for years on my laptop, but on this desktop it has a mid-high end graphics card (Radeon HD 6870) and the performance with fglrx or the default driver isn't very good. I hope AMD can work on their drivers to increase performance to match that of windows driver performance.

 it will take awhile.  It might take another 3 years before people stop getting angry

---

### Post by draucia on 2012-09-20
> **idoitprone said:**
> it will take awhile.  It might take another 3 years before people stop getting angry

I gave it another go on this desktop and messed around with a few amd and compiz settings and I get decent FPS in games I've tried. But then I remembered I still have this skype problem...

Could I get some more help on this problem?

What I've tried:

Skype .deb file from skype.com
Skype install from repos.
Skype dynamic and static download (sorta like "portable" skype) from skype.com
Installing ia32-libs (for static and dynamic skype)

But my computer still freezes when running skype. It doesn't always have a kernel panic, but it freezes (or sometimes has a kernel panic).

I can post any logs needed, here are my specs (if it helps in anyway?)

i3-2100
Radeon HD 6870 (Sapphire)
Ubuntu 12.04.1 64 bit
8GB RAM
Gigabyte B75M-D3V

Any help is appreciated, I really want to use Ubuntu as my main desktop OS but I can't because of this skype issue.

---

### Post by idoitprone on 2012-09-21
> **draucia said:**
> I gave it another go on this desktop and messed around with a few amd and compiz settings and I get decent FPS in games I've tried. But then I remembered I still have this skype problem...

Could I get some more help on this problem?

What I've tried:

Skype .deb file from skype.com
Skype install from repos.
Skype dynamic and static download (sorta like "portable" skype) from skype.com
Installing ia32-libs (for static and dynamic skype)

But my computer still freezes when running skype. It doesn't always have a kernel panic, but it freezes (or sometimes has a kernel panic).

I can post any logs needed, here are my specs (if it helps in anyway?)

i3-2100
Radeon HD 6870 (Sapphire)
Ubuntu 12.04.1 64 bit
8GB RAM
Gigabyte B75M-D3V

Any help is appreciated, I really want to use Ubuntu as my main desktop OS but I can't because of this skype issue.

I am looking at the fix and I am not liking itt

```

cd /usr/lib32

sudo chmod a-r libpulsecore-1.0.so 
```[http://askubuntu.com/questions/33773/what-to-do-when-skype-freezes-silently](http://askubuntu.com/questions/33773/what-to-do-when-skype-freezes-silently)

please remember any changes you made to the system. If an issue arise then you will know where to look

---

### Post by draucia on 2012-09-21
> **idoitprone said:**
> I am looking at the fix and I am not liking itt

```

cd /usr/lib32

sudo chmod a-r libpulsecore-1.0.so 
```[http://askubuntu.com/questions/33773/what-to-do-when-skype-freezes-silently](http://askubuntu.com/questions/33773/what-to-do-when-skype-freezes-silently)

please remember any changes you made to the system. If an issue arise then you will know where to look

> jason@jason:/usr/lib32$ 
chmod: cannot access `libpulsecore-1.0.so': No such file or directory

Also tried:

```
jason@jason:/usr/lib32$ sudo chmod a-r libpulse.so.0.13.4 libpulse-simple.so.0.0.3 libpulsecommon-1.0.so
chmod: cannot access `libpulse.so.0.13.4': No such file or directory
chmod: cannot access `libpulse-simple.so.0.0.3': No such file or directory
chmod: cannot access `libpulsecommon-1.0.so': No such file or directory
```

Why don't I even have these libraries?

EDIT

Ok so I tried the following steps:

```


sudo apt-get purge skype
sudo apt-get purge skype-bin
sudo apt-get autoremove

```

And did sudo dpkg -i skype..deb and I got this:

```


jason@jason:~/Downloads$ sudo dpkg -i skype-ubuntu_4.0.0.8-1_amd64.deb 
(Reading database ... 206150 files and directories currently installed.)
Unpacking skype (from skype-ubuntu_4.0.0.8-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on lib32stdc++6 (>= 4.1.1-21); however:
  Package lib32stdc++6 is not installed.
 skype depends on lib32asound2 (>> 1.0.14); however:
  Package lib32asound2 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 skype

```

could that be the problem?

---

### Post by idoitprone on 2012-09-21
> **draucia said:**
> Also tried:

```
jason@jason:/usr/lib32$ sudo chmod a-r libpulse.so.0.13.4 libpulse-simple.so.0.0.3 libpulsecommon-1.0.so
chmod: cannot access `libpulse.so.0.13.4': No such file or directory
chmod: cannot access `libpulse-simple.so.0.0.3': No such file or directory
chmod: cannot access `libpulsecommon-1.0.so': No such file or directory
```Why don't I even have these libraries?

they are 32 bit pulseaudio libraries

I dont really know how you configured your ia32 lib install.

That fix on the link was posted so it avoid pulse.

---

### Post by draucia on 2012-09-21
> **idoitprone said:**
> they are 32 bit pulseaudio libraries

I dont really know how you configured your ia32 lib install.

That fix on the link was posted so it avoid pulse.

I just installed ia32-libraries from synaptic. Uninstalling them donesn't help either. Could you look at my previous post? I think this might be a problem with the actual installation of skype. Look at the error I got.

---

### Post by draucia on 2012-09-23
Does anybody know why this is happening? Should I look into filing a bug report? I haven't done it before.

---

### Post by draucia on 2012-09-29
I'm still having this problem.. anybody have any idea to whats going on? Is it my fault or is it skype?

---

