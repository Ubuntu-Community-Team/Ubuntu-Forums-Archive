---
title: "Change bash output colors"
date: 2009-11-05
forum: General Help
---

### Post by nerdopolis on 2009-11-05
Hi. I  have a script file that when it runs a few commands within that script file, I want to change the color of the output of the commands. Is there any way to do that with an environment variable or something? 

Thanks.

---

### Post by falconindy on 2009-11-05
Throw this into the header of your script and refer to them as ${B} or ${W}, etc. Any time you use them in an echo statement, you'll need to use the -e flag with echo and you cannot use single quotes or else they won't be parsed properly. End each line using a color with ${N} to make sure you reset the color and prevent it from "bleeding" into other lines.
```
#Colors! Lots of colors!
 # regular colors
  N="\e[0m"	  # no color
  K="\e[0;30m"    # black
  R="\e[0;31m"    # red
  G="\e[0;32m"    # green
  Y="\e[0;33m"    # yellow
  B="\e[0;34m"    # blue
  M="\e[0;35m"    # magenta
  C="\e[0;36m"    # cyan
  W="\e[0;37m"    # white
 
 # emphasized (bolded) colors
  EMK="\e[1;30m"
  EMR="\e[1;31m"
  EMG="\e[1;32m"
  EMY="\e[1;33m"
  EMB="\e[1;34m"
  EMM="\e[1;35m"
  EMC="\e[1;36m"
  EMW="\e[1;37m"
 
 # background colors
  BGK="\e[40m"
  BGR="\e[41m"
  BGG="\e[42m"
  BGY="\e[43m"
  BGB="\e[44m"
  BGM="\e[45m"
  BGC="\e[46m"
  BGW="\e[47m"
```

---

### Post by nerdopolis on 2009-11-05
Is there any way to set the color output for a whole group of other commands? For instance I call apt-get at a certain point and I want to change the color of the text output from that command.

---

### Post by falconindy on 2009-11-05
Not likely. apt-get is a compiled binary that sets its own parameters. You would have to override the color pallette in gnome-terminal or use a terminal with more customization like urxvt.

---

### Post by nerdopolis on 2009-11-16
Found it. You don't do it through bash, I found that you have to use echo into the device itself.

This echos it into the current tty. (or pty which is what all graphical terminal programs use)

echo -en \\033[33m\\033[8] > $(tty) for red 
echo -en \\033[34m\\033[8] > $(tty)  for blue
(notice only the number in the center changed)

and a color table is here

[http://corz.org/public/linux/usr/local/bin/color.sh](http://corz.org/public/linux/usr/local/bin/color.sh)

---

