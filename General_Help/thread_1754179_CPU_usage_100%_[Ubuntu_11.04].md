---
title: "CPU usage 100% [Ubuntu 11.04]"
date: 2011-05-09
forum: General Help
---

### Post by Nichijou on 2011-05-09
[LEFT]Hi folks! I've a problem while I'm doing some stuff like watching videos, or playing games with wine or **** like that, my PC starts to lagg or I cant play... Because,when i do that things my CPU usage begins to fly (100%), and then is when I ask myself: 
> Whats happening?????
I've found a thread about this same problem but I cant understand it (here is is)
[http://ubuntuforums.org/showthread.php?t=329988](http://ubuntuforums.org/showthread.php?t=329988)
What can i do????? :confused:
Greetings,
N.

[/LEFT]

---

### Post by K_45 on 2011-05-09
What are you system specs? Laptop? PC?

Open a terminal and enter top, without opening any programs, then open a program and what happens to your CPU usage?

---

### Post by Nichijou on 2011-05-09
Its a Packard Bell MZ375; and only when I open System Monitor without another program is at 60% usage approx.

---

### Post by K_45 on 2011-05-09
Type

```
free
```

into the terminal, how much memory do you have?

---

### Post by Nichijou on 2011-05-09
>              total       used       free     shared    buffers     cached
Mem:        894344     740240     154104          0      62432     344028
-/+ buffers/cache:     333780     560564
Swap:       914428          0     914428

Thats it::

---

### Post by K_45 on 2011-05-09
You have enough hardware to run Natty, does your laptop heat up noticeably? Did you clean install Ubuntu 11.04?

---

### Post by Nichijou on 2011-05-09
ehmm nope  but check this thread[ http://ubuntuforums.org/showthread.php?t=329988]("http://ubuntuforums.org/showthread.php?t=329988")

---

### Post by K_45 on 2011-05-09
I'm fairly sure that that bug has been fixed in 4 years. Are you using any proprietary drivers: ?

```
gksu jockey
```

---

### Post by timZZ on 2011-05-09
Are you using wireless Internet?

---

### Post by Nichijou on 2011-05-09
What can i do whit this?
```
gksu jockey
```

And yes I'm connected via wireless

---

### Post by squee on 2011-06-02
Bump. I also have this issue and it is quite annoying. The CPU usage drops to normal levels when the screen is maximized.

Any ideas? Need to know anything? Laptop is in the sig below. And it was a fresh install.

---

### Post by squee on 2011-06-02
And as an interesting addon to this. When the non-full screen VLC window is partially (>1/3) off the current desktop, the CPU usage returns to just above normal.

---

### Post by adisos on 2011-08-08
I've founded solution for my high cpu usage - i kill captmon2 procces which was created by CAPT driver. I use printer LBP2900.
Sorry for my bad english.

---

