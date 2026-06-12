---
title: "Is backup on shutdown possible?"
date: 2011-05-18
forum: General Help
---

### Post by eddie3000 on 2011-05-18
Hi there everyone. I have read a few posts about making backups and scheduling backups. I have installed grsync, and it seems to be a very good program. I have also read about using cron for scheduling backups and that. At the moment I think I have it set to do incremental backups of a given folder. But I would like it to backup that given folder every time I shut down the PC instead of at a fixed time. Is this possible?

---

### Post by eddie3000 on 2011-05-18
Nobody?
What I would like is for grsync to backup my data when I choose to shutdown the computer and to shutdown when it's finished. Is that possible?

---

### Post by dragonfly41 on 2011-05-18
Curious .. would this work?

in Grsync > extra options > execute this command after rsync

shut down command .... $ sudo shutdown -h now

[http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/](http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/)

[http://linuxservertutorials.blogspot.com/2009/03/how-to-power-off-ubuntu-server-with.html](http://linuxservertutorials.blogspot.com/2009/03/how-to-power-off-ubuntu-server-with.html)

---

### Post by eddie3000 on 2011-05-18
Ah! It's so simple it makes one look silly. So instead of pressing the shutdown icon I run grsync and that's it I suppose. I think it'll work, I'll try it right away. Thank you Dragonfly.

---

### Post by eddie3000 on 2011-05-18
:(No, that didn't work. It says: 

".........*** Launching AFTER command:
sudo shutdown -h now
sudo: no tty present and no askpass program specified."

---

### Post by Cfhs_1 on 2011-05-18
Just type up a simple script that will run Grsync from the command line, then the shut down command. Shouldn't be too terribly complicated, I'd write ot for you, but I've never used grsync before. Give me some time, and I'll go check it out.

---

### Post by dragonfly41 on 2011-05-18
I should have tested it first .. seems that Grsync must be launched with root privileges .. **[COLOR=DimGray][/COLOR]**

then the shutdown command works.  I've just tried it.

The command is simply    ..... **[COLOR=DimGray]shutdown -h now[/COLOR]**

You can test first in File > Simulation .. and I guess export session.

---

### Post by eddie3000 on 2011-05-18
Yes, but it asks for the sudo password when you run it, which is logical. But it'd be nice just to double click something like a shutdown button/icon and do it without bothering you any more.

---

### Post by Cfhs_1 on 2011-05-18
> **eddie3000 said:**
> Yes, but it asks for the sudo password when you run it, which is logical. But it'd be nice just to double click something like a shutdown button/icon and do it without bothering you any more.

Which is where a nice script would come in. Set it up to run rsync (grsync's CLI command) and shutdown. then give it a power icon, and pin it to your panel.

May I ask, where are you backing up to? A file server on your LAN, an external HD, another partition on your internal HD, or what?

---

### Post by dragonfly41 on 2011-05-18
I've played around with a simple script which can call on grsync-batch (which I've just found here ..
 [http://linux.die.net/man/1/grsync-batch](http://linux.die.net/man/1/grsync-batch) .. )
where several sessions of grsync might want to be run before shutdown.

Run **[COLOR=Gray]sudo man grsync-batch[/COLOR]** in terminal to see it ..

```

#!/bin/bash
echo "backup followed by a shutdown"
sleep 5

# grsync-batch session-name(s) .. see man

sudo grsync-batch default
sudo shutdown -h now

```

---

### Post by Cfhs_1 on 2011-05-18
> **dragonfly41 said:**
> I've played around with a simple script which can call on grsync-batch (which I've just found here ..
 [http://linux.die.net/man/1/grsync-batch](http://linux.die.net/man/1/grsync-batch) .. )
where several sessions of grsync might want to be run before shutdown.

Run **[COLOR=Gray]sudo man grsync-batch[/COLOR]** in terminal to see it ..

```

#!/bin/bash
echo "backup followed by a shutdown"
sleep 5

# grsync-batch session-name(s) .. see man

sudo grsync-batch default
sudo shutdown -h now

```

I've literally just finished writing my script too. (Took like 5 mins to write and test) It will basically copy everything from one place to another excluding files that already exist in the destination and then shutdown without requiring the user to enter a password. I guess you already got it covered though. It was still fun to write it. :p

---

### Post by eddie3000 on 2011-05-19
Well that didn't work for me. What am I doing wrong?

In an attempt to learn what I am actually doing I started making a simple sript just to reboot by double clicking an app launcher on the desktop. Well, it still asks for the sudo password to reboot. The same happens if I try sudo shutdown -h now. If I remove the "sudo" in the script, it doesn't work. Why? What am I doing wrong?:confused:

---

### Post by dragonfly41 on 2011-05-19
If you still want to use the Grsync GUI it allows multiple sessions to be setup.

The grsync sessions are located in /home/myusername/.grsync/grsync.ini

you will need to view hidden files to see this.

grsync-batch simply refers to this config file.

you can echo comments between sessions run to track progress ..

```

#!/bin/bash
echo "backup in 5 seconds .. followed by a shutdown"
sleep 5

# grsync-batch session-name

sudo grsync-batch default

echo "finished backup of 'default' session .. now shutting down in 5 seconds"
sleep 5

sudo shutdown -h now

```
Alternatively .. as you are now trying .. you can write a bash script which uses rsync .. without the grsync GUI.

---

### Post by eddie3000 on 2011-05-19
```

#!/bin/bash
echo "data backup followed by a shutdown"

sudo pkexec rsync -r -t -p -o -g -v --progress --delete --ignore-existing -b -i -s /home/user/DATA /media/BACKUPDISK

echo "finished backup of DATA folder .. now shutting down in 1 second"
sleep 1

sudo shutdown -h now

```I still get asked for sudo password when I click the launcher. Is there a way for it not to do that?

---

### Post by dragonfly41 on 2011-05-19
This thread discusses same issue ...

[http://ubuntuforums.org/showthread.php?t=1668405](http://ubuntuforums.org/showthread.php?t=1668405)

---

### Post by eddie3000 on 2011-05-19
Yes, great thread. Thank you very much, it's exactly what I was looking for, I think....
I have learned the power of scripts, great little things. Wow!:guitar:

---

### Post by eddie3000 on 2011-05-20
I wanted an "Backup and shutdown" icon on the desktop that wouldn't ask for root password, and I did it. Thanks to the thread linked above by Dragonfly and a bit more googling around. Many thanks to Cfhs_1 too.

It's a two step process:

1) Edit /etc/sudoers so that anybody the command "shutdown" doesn't require entering a password, by adding this at the end: 

```
ALL ALL=NOPASSWD: /sbin/shutdown
```2) Create a script that first runs rsync and then does a shutdown, and link it to a launcher where ever you want it.

```
#!/bin/bash
echo "Backing up data..."

rsync -r -t -p -o -g -v --progress --delete --ignore-existing -b -i -s /home/user/DATAFOLDER /media/USBBACKUPDISK

echo "Finished backing up. The computer should be shutting down in a couple seconds...."
sleep 2

sudo shutdown -h now
```But I have a question. :-k Does removing the password for the shutdown command pose a risk? Can somebody from the outside (internet) cause my system to shutdown with this?

---

### Post by ianc1 on 2011-05-23
> **eddie3000 said:**
> But I have a question. :-k Does removing the password for the shutdown command pose a risk? Can somebody from the outside (internet) cause my system to shutdown with this?

I wouldn't mind knowing the answer to that question as well.  If anyone knows please post.

---

### Post by eddie3000 on 2011-05-24
I moved over to the security forum and this is what I got:

[http://ubuntuforums.org/showthread.php?t=1763951](http://ubuntuforums.org/showthread.php?t=1763951)

It's not much, but it makes me feel a bit better. Though it's a little irrational on my part. :D

---

### Post by nothingspecial on 2011-05-24
Aslong as all your users have good passwords then your a safe as you can be. If some one can log on to your computer remotely there are far worse things they can do than shut it down.

---

### Post by ianc1 on 2011-05-24
Thanks Eddie3000 and nothingspecial.

Also thanks for the tip (in your signature) for DuckDuckGo which I've recently adopted as my search engine I was however unaware of the ability to target ubunuforums with the !ubuntuf.

Thanks again.

---

