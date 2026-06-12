---
title: "Script for Konsole"
date: 2009-08-27
forum: General Help
---

### Post by Intrepid Ibex on 2009-08-27
Hi,

Just wanting to know that what is the correct alternative of Gnome/Gnome Terminal...:
```
gnome-terminal -x bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
``` ... with KDE/Konsole.

---

### Post by Intrepid Ibex on 2009-08-28
bump

---

### Post by nikhilk on 2009-08-28
> **Intrepid Ibex said:**
> Hi,

Just wanting to know that what is the correct alternative of Gnome/Gnome Terminal...:
```
gnome-terminal -x bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
``` ... with KDE/Konsole.

That would be 'konsole'.

But there should be no need to specify gnome-terminal or konsole. Simply executing ```
bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
``` should be sufficient.

---

### Post by Intrepid Ibex on 2009-08-28
Well I tested that and it doesnt work .. argh

---

### Post by Intrepid Ibex on 2009-08-30
anyone? I'd really like to get this to work :-(

---

### Post by nikhilk on 2009-08-31
Could you explain a bit more exactly what it is that you are trying to do?

---

### Post by Intrepid Ibex on 2009-08-31
Huh :-O?

I'm trying to port the script (Gnome/Gnome Terminal):
```
gnome-terminal -x bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
```to KDE/Konsole (the following example doesn't work):
```
konsole bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
```

---

### Post by Johnny B on 2009-08-31
> konsole -e "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
or like nikhilk posted: (do not add konsole to this command)
> bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"

---

### Post by Intrepid Ibex on 2009-09-03
> **Johnny B said:**
> konsole -e "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"> or like nikhilk posted: (do not add konsole to this command)> bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"Well the upper one doesn't work as konsole just opens up (as if I only ran a script 'konsole') and the seccond one isn't a konsole script. :(

---

### Post by nikhilk on 2009-09-04
> **Intrepid Ibex said:**
> Well the upper one doesn't work as konsole just opens up (as if I only ran a script 'konsole') and the seccond one isn't a konsole script. :(

I do not completely understand when you say "konsole script". konsole is just a terminal emulator the real shell beneath is [bash]("http://en.wikipedia.org/wiki/Bash").

So basically you want to run a bash script. To create a bash script with the commands you have previously mentioned create a file with the following contents:
```

#!/bin/bash

sudo apt-get update && sudo apt-get dist-upgrade
read -n1

exit 0

```

Just make sure that the script is made executable and then you should be able to run it from any terminal emulator like this (assuming the file previously created is named apt_upgrade.bash and is present under the Desktop directory)
```

$ cd ~/Desktop
$ ./apt_upgrade.bash

```

---

### Post by Intrepid Ibex on 2009-09-07
Heh, I just ment that I wanted the terminal to be Konsole not Gnome Terminal.

I should probably change my sig back to "please don't think I'm a beginner" as you obviously didn't get that from me.. :/

Also STILL I waanted to create a script that will open konsole and do the command if I double click the file.

---

### Post by Rob_H on 2009-09-07
This worked for me:
```
konsole -e bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
```
You could also just change your default terminal emulator to Konsole. Not sure how to do this in GNOME. In KDE, you can do it through System Settings > Default Applications > Terminal Emulator.

---

### Post by Intrepid Ibex on 2009-09-10
Finally, thanks man, really ;).

Btw. I use Kdemod (arch, not chakra) and also Konsole is always the default in KDE - it won't even help which ever you change the default terminal emulator to (at least) if that's the only command to do what I need it to do.

So here's what I did:
```
konsole -e bash -c "sudo pacman -Syu"
```

---

