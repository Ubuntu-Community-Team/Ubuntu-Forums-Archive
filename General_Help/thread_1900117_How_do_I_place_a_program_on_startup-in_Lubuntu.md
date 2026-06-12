---
title: "How do I place a program on startup-in Lubuntu"
date: 2011-12-25
forum: General Help
---

### Post by pretty_whistle on 2011-12-25
I placed the icons to the programs here but it failed:

> Pull up file manager, hit CTRL H to show hidden folders.  Then went to .config>autostartIs there something I'm missing?  Why has this failed?

:confused:

---

### Post by pretty_whistle on 2011-12-25
It worked when I did it on ubuntu 11.04 and ubuntu 11.10.

---

### Post by Rodney9 on 2011-12-25
See here - [http://goo.gl/i3OAW](http://goo.gl/i3OAW)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by pretty_whistle on 2011-12-25
> **Rodney9 said:**
> See here - [http://goo.gl/i3OAW](http://goo.gl/i3OAW)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR=Blue]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney
The directions to the how-to went way over my head...being the noob that I am, so I failed at trying (the 1st link you gave I mean).

---

### Post by fdrake on 2011-12-25
what's the application (name) you need to autostart?

my_app=the name of you application

```
cp `which my_app` /home/jorid/.config/my_app 
```
copy it in the terminal and change the name!

---

### Post by pretty_whistle on 2011-12-25
> **fdrake said:**
> what's the application (name) you need to autostart?

my_app=the name of you application

```
cp `which my_app` /home/jorid/.config/my_app 
```
copy it in the terminal and change the name!
I tried that.  Failed message in LXTerminal.

---

### Post by pretty_whistle on 2011-12-25
I'm trying to autostart Thunderbird Mail, FWIW.

---

### Post by pretty_whistle on 2011-12-26
Anyone?

---

### Post by pretty_whistle on 2011-12-26
In post #1 I described how I put something on autostart.  I had just gone done doing that very thing-it took my aMSN but not the Thunderbird.

Because it won't take Thunderbird but _*did*_ take aMSN, I'm betting it's the program itself which explains this and *not* the method to put something on autostart.

I'll skip it then since Thunderbird itself is the issue.

Thanks for everyones help nonetheless. :)

---

