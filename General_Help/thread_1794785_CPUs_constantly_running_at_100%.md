---
title: "CPUs constantly running at 100%"
date: 2011-07-01
forum: General Help
---

### Post by bravo sierra echo on 2011-07-01
Kubuntu Natty Narwhal, 2 x 3ghz processors, 1.5gig RAM.

All day today, both my processors have been running at 100%, with the result that the desktop is running unbelievably slowly.  Looking at System Monitor, it doesn't show any processes running which would be causing this - it's just the usual.  I've tried quitting everything that's running - still no effect.

Any ideas what might be causing this?  Or any alternatives to the System Monitor which might give me a better clue as to what's going on?

Thanks in advance.

---

### Post by andrewthomas on 2011-07-01
> **bravo sierra echo said:**
> Kubuntu Natty Narwhal, 2 x 3ghz processors, 1.5gig RAM.

All day today, both my processors have been running at 100%, with the result that the desktop is running unbelievably slowly.  Looking at System Monitor, it doesn't show any processes running which would be causing this - it's just the usual.  I've tried quitting everything that's running - still no effect.

Any ideas what might be causing this?  Or any alternatives to the System Monitor which might give me a better clue as to what's going on?

Thanks in advance.
It could be nepomuk, akonadi & strigi indexing your home directory, consuming mass amounts of RAM and disk space.

---

### Post by bravo sierra echo on 2011-07-01
Strigi was my first thought too, but suspending file indexing or quitting altogether makes no difference at all :(

---

### Post by bravo sierra echo on 2011-07-02
Bump :)

Maybe someone can recommend an alternative to System Monitor, which might allow me to see what process is doing this?

---

### Post by ankspo71 on 2011-07-02
Hi,
Try opening the terminal (Konsole) and running the command 'top'. Top will be much more lightweight and it shows quite a bit more details.

Another nice terminal based system monitor is htop, but you would probably need to install it first.

---

### Post by wildmanne39 on 2011-07-02
+1 for top.

---

### Post by d3v1150m471c on 2011-07-02
```

man top
top

# -OR-
ps aux

```

---

### Post by elianto on 2011-07-02
[SIZE=4][SIZE=1]I have just finished to write to another post and I noticed you probably having the same problem I got[/SIZE][B]
If your disk start behaving crazy on kde startup[/B][/SIZE]
and never ends doing who knows what eating all the memory slowing the interface and bringing your computer to knees [COLOR=Red]no worries[/COLOR] it's **[SIZE=2]akonadi[/SIZE]**.
I have this bug since 10.4 and I think it's triggered when, for some  rare circumstance, kde got  killed in the middle.
The workaround I found it's pretty [COLOR=Magenta]painless[/COLOR][COLOR=Black] : before login switch to a terminal (ctrl+alt+f1) login, rm -rf .config/akonadi[/COLOR] then login as normal (ctrl+alt+f7)
I wonder why this bug it's still here!

btw for checking diskio try **iotop** not top.

---

### Post by bravo sierra echo on 2011-07-02
Elianto wins the thread!

Thank you so much.

---

