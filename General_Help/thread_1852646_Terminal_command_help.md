---
title: "Terminal command help"
date: 2011-09-30
forum: General Help
---

### Post by spiky001 on 2011-09-30
I want to start terminal, from terminal with a command  so I can ssh into server. I can run from 1 terminal gnome-terminal and a terminal starts, if I add ```
gnome-terminal ssh -p 10000 spiky@10.42.43.1
``` I get  ```
Failed to parse arguments: Unknown option -p
``` also I want ```
gnome-terminal -X -p 10000 spiky@10.42.43.1
``` return is ```
Failed to parse arguments: Unknown option -X
``` Any advice ultimatly I want to put it in a script.

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-30
Did you try putting the command you're trying to run (ssh) and its parameters in quotes?
Such as:
```
gnome-terminal "ssh -p 10000 spiky@10.42.43.1"
```

I'm going out on a limb here, I haven't actually tested this...

---

### Post by lavajumper on 2011-09-30
I think this is what he's looking for:

```
gnome-terminal -e "ssh -p 10000 spiky@10.42.43.1"
```

also, in these instances 'man' is your best friend.

```
man gnome-terminal
```

---

### Post by spiky001 on 2011-09-30
No it launches the terminal but i,m at normal prompt  I,d like it to start  ```
spiky@spiky-toshiba:~$ssh -p 10000 spiky@10.42.43.1
``` or even better ```
spiky@10.42.43.1's password:
```

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-30
Please construct your phrases in such a fashion that they are readable by mere human beings :)

---

### Post by spiky001 on 2011-09-30
perfect lavajumper thks for help

---

### Post by WasMeHere on 2011-09-30
I have cut the following text from *man xterm* (the origin of gnome-terminal)

> -e program [ arguments ... ]
               This option specifies the program (and its command  line  argu&#8208;
               ments)  to be run in the xterm window.  It also sets the window
               title and icon name to be the basename  of  the  program  being
               executed  if  neither  -T nor -n are given on the command line.
               This must be the last option on the command line.
 [FONT="Courier New"]xterm -e program arg1 arg2 ...[/FONT] 
Try ```
xterm -e ssh -p 10000 spiky@10.42.43.1
```

---

### Post by lavajumper on 2011-09-30
This worked on mine

```
gnome-terminal -x ssh -p 22 lavajumper@xxx.xxx.xxx.xxx
```

Note that the '-x' is lower case.

Also remember that when the command returns, the terminal window will close, so in the case of any kind of error, the new spawned terminal will not give you time to view the error message.

---

### Post by spiky001 on 2011-09-30
The -x gives an error on the new terminal but if I run with the -e option the new terminal works fine??

---

### Post by spiky001 on 2011-09-30
Olle Wiklund I did try that a few times but it failed, Just copied yours It worked must of made a mistake before but thks for helping  Just checked history i put [codr]xterm -e gnome-terminal ssh xxxxx[/code] if I left out gnome terminal it would of worked.

---

### Post by WasMeHere on 2011-09-30
> **spiky001 said:**
> Olle Wiklund I did try that a few times but it failed, Just copied yours It worked must of made a mistake before but thks for helping  Just checked history i put [codr]xterm -e [COLOR="Red"][s]gnome-terminal[/s][/COLOR] ssh xxxxx[/code] if I left out gnome terminal it would of worked.
Use xterm instead of gnome-terminal! Do not enter gnome-terminal into your xterm command string! I have tried the xterm command myself, and this works for me and it's really basic and standard and should work for everybody: ```
 xterm -e ssh olle@192.168.0.2
```

---

