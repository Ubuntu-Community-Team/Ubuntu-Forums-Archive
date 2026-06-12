---
title: "terminal is not working"
date: 2011-04-14
forum: General Help
---

### Post by ashickur.noor on 2011-04-14
Hello every one.

I am using Ubuntu for 9 months. For the first time I have encounter a problem which I have no solution. Because the problem solver is now the problem. I mean In my Ubuntu [SIZE=2]**terminal is not starting.**[/SIZE] What can I do?   

Please help me ASAP.

Thank you

---

### Post by WorMzy on 2011-04-14
Which terminal? gnome-terminal? Try xterm. Press Alt+F2, then run

```
xterm
```

If that launches, try to run gnome-terminal.

```
gnome-terminal
```

If you get an error at this point, post it here.

If neither launches, then press Ctrl+Alt+F1 to switch to a tty. Log in, and run
```
export DISPLAY=:0.0
gnome-terminal
```

Again, post any errors you get at this point.

---

### Post by ashickur.noor on 2011-04-14
I got this error
> gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_alternate_screen_scroll[[IMG]http://img98.imageshack.us/img98/6006/xterm001.png[/IMG]]("http://img98.imageshack.us/i/xterm001.png/")

---

### Post by WorMzy on 2011-04-14
Have you added any custom software sources/installed any third-party packages recently?

There's a few results on google that suggest that this is caused by installing a third-party version of libvte9.

Can you run ```
ldd /usr/bin/gnome-terminal
``` in the xterm window and copy-paste the output here.

---

### Post by ashickur.noor on 2011-04-14
Yes I have Install cairo-dock from debian DVD.
I have attached output of ```
 ldd /usr/bin/gnome-terminal 
```

---

### Post by WorMzy on 2011-04-14
Is there a reason why you installed Debian's package instead of Ubuntu's?

Did the problem start after you installed cairo-dock?

---

### Post by ashickur.noor on 2011-04-14
Yes after installing cairo-dock the problem starts. 
There are some reason to install cairo-dock from debian DVD.

---

### Post by WorMzy on 2011-04-14
The way I see it, you have two choices.

1) Remove the Debian packages and replace them with the Ubuntu equivalents. [Recommended]
or
2) Try installing Debian's version of gnome-terminal

Unfortunately, it may not be just gnome-terminal that's affected, so you may have to install several other applications from the Debian DVD.

What's the reason for using Debian's version of cairo-dock? Have you checked the packages available on [launchpad]("https://launchpad.net/ubuntu/+search?text=cairo-dock") to see if they'd be more suitable?

---

### Post by ashickur.noor on 2011-04-14
Thank you, I will inform Letter after do so.

---

