---
title: "Using unison upon shutdown / restart / start"
date: 2009-09-15
forum: General Help
---

### Post by peshom on 2009-09-15
Hello everyone!

I am new to Ubunto (and Linux) in general so bear with me please.

I have a laptop and a desktop. I am the only user on both. I followed this tutorial ([http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082)) to set up openssh server and successfully made it to the point where I could just type "ssh hostname" and it logs me into the other machine without prompting for a password.

Both machines are on a home network and as far as I understand this method is pretty secure for connecting to a machine on a local network (and in general I think)... Anyway... What I am trying to do is use unison to sync parts of my home directory.

I have made it to the point where I have unison setup and there is a working profile. I am able to run unison both from the terminal and from it's GTK and everything works as intended.

Since I am mostly working at home, but switch places here I work, because I like changing my environment once in a while most of the changes done to small files. 

What I would like to do is have ubuntu execute a script every time I start, shutdown, or restart my laptop a command is run that will sync the home folders between the two computers.

Here is the code from the relevant files.

Unison profile:

**Desktop.prf (location: /home/.unison)**

```

### ROOT SYNC PATHS ###

# first folder is my home directory on this laptop
root = /home/petarm/

# second directory is my desktop's home folder over SSH
root = ssh://petarm@petarm-desktop//home/petarm/


### SSH Settings ###

# setting up SSH to use compression
rshargs = -C

### PATHS TO SYNCHRONIZE ###

# only sync bookmarks for firefox
path = .mozilla/firefox/petarm.default/bookmarks.html

# Personal Folders
path = Desktop/
path = Documents/
path = Music/


### IGNORE RULES ###

#ignore = Path .mozilla/firefox/petarm.default/Cache

```

And this is the script that I have in **/etc/init.d** folder:

**sync-on-shutdown-restart (location: /etc/init.d)**

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          
# Required-Start:    
# Required-Stop:
# Default-Start:     1 6
# Default-Stop:
# Short-Description: Syncing the Home directories between this Laptop and the Desktop
### END INIT INFO
gnome-terminal -e "unison Desktop -batch -auto"

```

I have created symlinks created in **/etc/rc1.d** and **/etc/rc6.d**. Both of the symlinks are named **S10sync-on-shutdown-restart**. This is the smallest **S**** in **/etc/rc1.d** and the onlything smaller in **/etc/rc6.d** is named **S01linux-restricted-modules-common**. The only restricted drives on my laptop are for my modem and they are not even enabled.

I used this thread ([http://ubuntuforums.org/showpost.php?p=4247684&postcount=187](http://ubuntuforums.org/showpost.php?p=4247684&postcount=187)) to learn about the **init.d** and **rc*.d** folders.

I am not sure what I am doing worng, because if I run "unison Desktop -batch -auto" in the terminal, it equecutes everything properly. I also have created an executable file with the same command and regardles of whethere I "Run" it or "Run in Terminal" it works as expected.

As far as I understand it this should run the script as my computer Starts entereing runlevel 1 or 6. I am also aware that even if these were set up correctly, it will ONLY sync on shutdown or restart, but NOT on start. That's ok. Ultimately I want to make it do that as well, but for now I will be content with making the shutdowr / restart sync work.

I should also mention that if I try to run the command OR the executable file as a cron job, it doesn't start. This is what my "crontab -l" output:

```

0 23 * * * /home/petarm/sync-laptop-desktop.txt # JOB_ID_2

```

I set up the cron job with gnome-schedule.

I am also not converned with setting up the desktop to do that, because I always turn the desktop on first and turn it off last and eveything that I change will get updated on the laptop when I boot it (the laptop).

Thanks so much in advance!

---

### Post by peshom on 2009-09-15
bump

---

### Post by peshom on 2009-09-15
bump

---

### Post by peshom on 2009-09-17
bump

---

### Post by dragonne on 2009-11-02
Not sure if you've found your solution, but in the interests of completeness, as this posting appears high in google for unison.

Your problem is here > gnome-terminal -e "unison Desktop -batch -auto"

The script in your init.d directory executes outside of X, so outside of any graphical environment.  
gnome-terminal is a graphical terminal emulator, and so it will fail when run outside of X.
To fix it change the line :-

gnome-terminal -e "unison Desktop -batch -auto"

to 

unison Desktop -batch -auto

Hope you've found a solution before this.

David.


> **peshom said:**
> Hello everyone!

I am new to Ubunto (and Linux) in general so bear with me please.

I have a laptop and a desktop. I am the only user on both. I followed this tutorial ([http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082)) to set up openssh server and successfully made it to the point where I could just type "ssh hostname" and it logs me into the other machine without prompting for a password.

Both machines are on a home network and as far as I understand this method is pretty secure for connecting to a machine on a local network (and in general I think)... Anyway... What I am trying to do is use unison to sync parts of my home directory.

I have made it to the point where I have unison setup and there is a working profile. I am able to run unison both from the terminal and from it's GTK and everything works as intended.

Since I am mostly working at home, but switch places here I work, because I like changing my environment once in a while most of the changes done to small files. 

What I would like to do is have ubuntu execute a script every time I start, shutdown, or restart my laptop a command is run that will sync the home folders between the two computers.

Here is the code from the relevant files.

Unison profile:

**Desktop.prf (location: /home/.unison)**

```

### ROOT SYNC PATHS ###

# first folder is my home directory on this laptop
root = /home/petarm/

# second directory is my desktop's home folder over SSH
root = ssh://petarm@petarm-desktop//home/petarm/


### SSH Settings ###

# setting up SSH to use compression
rshargs = -C

### PATHS TO SYNCHRONIZE ###

# only sync bookmarks for firefox
path = .mozilla/firefox/petarm.default/bookmarks.html

# Personal Folders
path = Desktop/
path = Documents/
path = Music/


### IGNORE RULES ###

#ignore = Path .mozilla/firefox/petarm.default/Cache

```And this is the script that I have in **/etc/init.d** folder:

**sync-on-shutdown-restart (location: /etc/init.d)**

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          
# Required-Start:    
# Required-Stop:
# Default-Start:     1 6
# Default-Stop:
# Short-Description: Syncing the Home directories between this Laptop and the Desktop
### END INIT INFO
gnome-terminal -e "unison Desktop -batch -auto"

```I have created symlinks created in **/etc/rc1.d** and **/etc/rc6.d**. Both of the symlinks are named **S10sync-on-shutdown-restart**. This is the smallest **S**** in **/etc/rc1.d** and the onlything smaller in **/etc/rc6.d** is named **S01linux-restricted-modules-common**. The only restricted drives on my laptop are for my modem and they are not even enabled.

I used this thread ([http://ubuntuforums.org/showpost.php?p=4247684&postcount=187](http://ubuntuforums.org/showpost.php?p=4247684&postcount=187)) to learn about the **init.d** and **rc*.d** folders.

I am not sure what I am doing worng, because if I run "unison Desktop -batch -auto" in the terminal, it equecutes everything properly. I also have created an executable file with the same command and regardles of whethere I "Run" it or "Run in Terminal" it works as expected.

As far as I understand it this should run the script as my computer Starts entereing runlevel 1 or 6. I am also aware that even if these were set up correctly, it will ONLY sync on shutdown or restart, but NOT on start. That's ok. Ultimately I want to make it do that as well, but for now I will be content with making the shutdowr / restart sync work.

I should also mention that if I try to run the command OR the executable file as a cron job, it doesn't start. This is what my "crontab -l" output:

```

0 23 * * * /home/petarm/sync-laptop-desktop.txt # JOB_ID_2

```I set up the cron job with gnome-schedule.

I am also not converned with setting up the desktop to do that, because I always turn the desktop on first and turn it off last and eveything that I change will get updated on the laptop when I boot it (the laptop).

Thanks so much in advance!

---

