---
title: "Run basic script without need to input sudo password"
date: 2010-08-19
forum: General Help
---

### Post by inameiname on 2010-08-19
I have a basic script that I have thrown together and have created a launcher for it so I can update my computer with one click:

```

#!/bin/bash

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade && sudo apt-get -y autoclean && sudo apt-get -y autoremove && sudo apt-get -y clean && sudo apt-get -y remove && orphand && sudo deborphan |  xargs sudo apt-get -y remove --purge

```However, since it requires my sudo password when I run it, I must put that in which is an extra step. 

So my question is if there is a way to make the script work either without the need to insert my password, or perhaps to run as root or something. I tried chown-ing it to 'root', but that doesn't work. 

Anybody?

---

### Post by davrosuk on 2010-08-19
My approach would be to run it as a cron job running as root negating the need for sudo.

I'm pretty sure that ubuntu has a method for doing what you've put together automatically (or is that only on the server edition...?) - someone else will know!

edit:
Heres the guide for auto updates :-) 
[https://help.ubuntu.com/9.04/serverguide/C/automatic-updates.html]("https://help.ubuntu.com/9.04/serverguide/C/automatic-updates.html")

---

### Post by inameiname on 2010-08-19
Thanks for the suggestion. I'm not sure how to do a cron job though, as I've never done those before.

Fortunately, I have figured out a solution that seems to work:

sudo gedit /etc/sudoers

...and add the following at the very bottom:

# To automate an update script in the nautilus-scripts folder without need of sudo
%me ALL = NOPASSWD: /home/(my username)/.gnome2/nautilus-scripts/My_Scripts/Update.sh

...and then create a desktop launcher for that very script, and ensure that it starts out with 'sudo':

Command: sudo /home/(my username)/.gnome2/nautilus-scripts/My_Scripts/Update.sh

It works. Only that script, and that script only, is allowed to run without the need for sudo, so I don't have to worry about security issues other than this one script.

---

