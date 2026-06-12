---
title: "terminal dosn'n work after configru .bashrc file"
date: 2010-08-25
forum: General Help
---

### Post by justniik on 2010-08-25
hi!! frnds this is justniik,
today i'm configru cakephp...in ubuntu 10.4 ...
& configuring ".bashrc" file but after configuration ...
my terminal dosn't work ......shome some 
error-

bash: export: `/var/www/cakephp/console:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games': not a valid identifier
root@justniik-laptop:~# gedit .bashrc
bash: gedit: No such file or directory

dosn't work any command in terminal.....plz help
wat can i do??

---

### Post by inameiname on 2010-08-25
I suggest just putting your .bashrc folder back to the way it was. I'm guessing you just tweaked the .bashrc in your home folder. There is also another one in your root folder. Perhaps you can just copy and paste that one to your home folder to restore the original and get it working. Then you can continue to put on and tweak it to however you like.

---

### Post by silverglade00 on 2010-08-25
Boot from a live CD and edit the file in there. I would move that "/var/www/cakephp/console:" part to the end of that line. You can also type in "/usr/bin/gedit .bashrc" to get it working.

---

### Post by inameiname on 2010-08-25
I thought about just saying, do this:

sudo cp /root/.bashrc /home/(your username)/.bashrc && sudo chown -R (your username) /.bashrc

...but then I realized he couldn't do that without being in the terminal. Although, could in the root terminal.

---

