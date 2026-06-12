---
title: "How to close rhythmbox?"
date: 2010-10-11
forum: General Help
---

### Post by pushkin22 on 2010-10-11
With 10.10 rhythmbox is integrated in the sound applet, but how can I close it without going to the file menu?

---

### Post by gyussz on 2010-10-11
> **pushkin22 said:**
> With 10.10 rhythmbox is integrated in the sound applet, but how can I close it without going to the file menu?

I don't think you can close it using the applet, but if you really don't want the file menu, try ALT + F2 then the ' killall Rhythmbox ' command, (you can do the same in terminal ofc).

---

### Post by efflandt on 2010-10-11
It is not around until you open rhythmbox.  Once you close it, it does seem to hang around.  But when I tried to kill it, it said there was no such process and it was no longer there.  So maybe it goes way by itself awhile after being closed.

Note that kill -1 is same as kill -HUP which means "hang up" (like hang up the phone) which is a gentle way to kill processes.

**ps aux | grep rhythm**
efflandt  2191 11.4  1.0 737188 81884 ?        Sl   20:32   0:01 rhythmbox
efflandt  2214  0.0  0.0  11332   876 pts/0    R+   20:32   0:00 grep --color=auto rhythm

**kill -1 2191**
bash: kill: (2191) - No such process

**ps aux | grep rhythm**
efflandt  2217  0.0  0.0  11332   876 pts/0    S+   20:34   0:00 grep --color=auto rhythm

---

### Post by _outlawed_ on 2010-10-11
> **pushkin22 said:**
> With 10.10 rhythmbox is integrated in the sound applet, but how can I close it without going to the file menu?

Are you talking about the indicator icon for it?

---

### Post by WRDN on 2010-10-11
efflandt has provided an excellent array of commands that can be used and combined.
I would also like to add "killall", which can be used to kill a process by name. The argument, "-9" can be used to forcibly close the program, useful if it has crashed. An example:

```
killall rhythmbox -9
```

---

### Post by FahadMKS on 2010-10-11
The Simplest way to do it is to just click on the Music option on the RythmBox and select Quit and the process will be stopped.

If you have just closed the Application, it will hang around, if so you may check for an icon next to the volume icon on the top task bar >> left click on that icon and then select Quit to end the process.

---

### Post by pushkin22 on 2010-10-13
> **_outlawed_ said:**
> Are you talking about the indicator icon for it?

There is no more indicator icon for it, now rhythmbox is integrated in the sound applet/indicator.

> **FahadMKS said:**
> The Simplest way to do it is to just click on the Music option on the RythmBox and select Quit and the process will be stopped.

If you have just closed the Application, it will hang around, if so you may check for an icon next to the volume icon on the top task bar >> left click on that icon and then select Quit to end the process.

This is what I meant with going to the file menu (ok, it is actually no file menu but a music menu :)). And this way to close rhythmbox is a little inconvenient.
I think they should put a small close button to the sound applet.

---

### Post by trazart on 2010-10-14
I think it should do what it's doing when you minimize it, but when you close the window you really mean that you want to close it.

Anyway, the fastest way to close it is pressing Control+Q.

---

### Post by pushkin22 on 2010-10-15
I found something, you can configure the old icon over a plugin. The icon plugin is activated out of the box, but it is hidden, you can set it as always visible in the plugin settings, than you will have the old rhythmbox icon with the old menu.

---

### Post by tiggsy on 2010-10-15
click the icon in the panel and select Quit from the dropdown

---

### Post by benerickson1 on 2010-10-16
I'm wondering the same thing and I don't understand this design.  When I want to close an application, I click the close button with the X.  Am I missing something?  What is the benefit of the close button NOT closing?

---

### Post by Darkhorse85 on 2010-10-20
I don't get it either! In lucid i deactivated the applet all together, but cant for the life of me remember how i did it. If you minimize it and goes to the icon thats cool, but why would you press the X on the window not to close it?. This laptop is for my sister, just thinking about explaining to her why she has to close a program **TWICE** makes my head hurt. 

Anyway to make the X button actually close rhythmbox?

---

### Post by stinkeye on 2010-10-20
I've found that in maverick hitting the close button while it is playing
hides the window but if nothing is playing it will quit rhythmbox.

---

### Post by jumi5 on 2010-11-03
If you want rhythmbox to actually close when you press the x then go to edit>plugins>untick power manager.

---

### Post by hydrotemplar on 2010-11-19
Is that the only way to fix it?  I would like to keep the prevention of suspending while I'm playing music...

---

