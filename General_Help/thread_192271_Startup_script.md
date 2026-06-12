---
title: "Startup script"
date: 2006-06-08
forum: General Help
---

### Post by ashrack on 2006-06-08
I would like the following script to be executed at ubuntu bootup.
```
#! /bin/sh

rm -rf /home/dijaki/ /home/veliko-oko
tar -xvf /var/users/dijaki.tar -C /home/dijaki/
tar -xvf /var/users/brumen.tar -C /home/veliko-oko

```
How would I acomplish this?

Ive tried putting it in /etc/rc2.d 
but nothing happened. And yes the file is executable

---

### Post by christhemonkey on 2006-06-08
You need to add it to boot up scriptsproperly.

First move it to /etc/init.d/

then run a
```
sudo update-rc.d whatyoucalledbootupscript defaults 99 
```

That will make it the last thing to be run in each run level.

---

### Post by xtacocorex on 2006-06-08
You could use a system cron job on reboot:
```
sudo crontab -e
```

In the editor, type the following:
```
@reboot /path/to/shell/script
```

EDIT: I'm going to have to try that init scripts thing proper now that christhemonkey showed us how.

---

### Post by ifokkema on 2006-06-09
[QUOTE=christhemonkey]You need to add it to boot up scriptsproperly.

First move it to /etc/init.d/

then run a
```
sudo update-rc.d whatyoucalledbootupscript defaults 99 
```

That will make it the last thing to be run in each run level.[/QUOTE]

Wouldn't that make the script run 5 times before you got your machine booted? I mean, normal run level is 5. If his script is ran for each run level, these home directories are overwritten 5 times or so. I assume there must be a way to stick in into run level 2 or so.

---

### Post by christhemonkey on 2006-06-09
I believe that ubuntu and other debian based OS only really use a couple of the run levels; 1, startup, 2, multiuser, 6, shutdown and S, special(?!). (but dont quote me on that...)

Read the manpage for more information and ways of making things run at specific run levels:
```
man update-rc.d
```

---

### Post by ashrack on 2006-06-10
[QUOTE=xtacocorex]You could use a system cron job on reboot:
```
sudo crontab -e
```

In the editor, type the following:
```
@reboot /path/to/shell/script
```

EDIT: I'm going to have to try that init scripts thing proper now that christhemonkey showed us how.[/QUOTE]
so far this works great. We will se wednesday when the students will get a hold on this machine

---

### Post by oliwally on 2006-06-11
> I would like the following script to be executed at ubuntu bootup.

I'm trying to do something similar in order to get midi to work on my computer. 
At [this post]("http://ubuntuforums.org/showpost.php?p=568132&postcount=10") it was suggested to run a script at startup to do the following:

```
sudo asfxload [the_path_and_filename_of_the_soundfont]
```

But I have no idea how to write such a scipt (do i just write that line into a text document, editing the path of course?) and where to put that script when I have it. This thread has helped but I'm uncertain which one of the suggestions to use or if they will work for my situation. Please help.

---

### Post by nanotube on 2006-06-11
[QUOTE=oliwally]I'm trying to do something similar in order to get midi to work on my computer. 
At [this post]("http://ubuntuforums.org/showpost.php?p=568132&postcount=10") it was suggested to run a script at startup to do the following:

```
sudo asfxload [the_path_and_filename_of_the_soundfont]
```

But I have no idea how to write such a scipt (do i just write that line into a text document, editing the path of course?) and where to put that script when I have it. This thread has helped but I'm uncertain which one of the suggestions to use or if they will work for my situation. Please help.[/QUOTE]

yes, you basically create a text file with that command (but without the sudo, because startup things run as root already). so your text file contents would be 
```
#!/bin/sh
asfxload [the_path_and_filename_of_the_soundfont]
```

save file to your desktop, then place that file into /etc/init.d with command
```
sudo cp ~/Desktop/yourscriptname /etc/init.d/
```
then chmod to executable with command
```
sudo chmod 755 /etc/init.d/yourscriptname
```

and then run command
```
sudo update-rc.d yourscriptname defaults 99
```

and that should do it.

to learn more about scripting and commandline in general, you can go to the first link in my sig, and find the "other commandline resources" section. :)

---

### Post by oliwally on 2006-06-11
> ...and that should do it.

to learn more about scripting and commandline in general, you can go to the first link in my sig, and find the "other commandline resources" section. 

Awesome!

Thanks so much for your help nanotube.
People on this forum are just great - fast, friendly and helpful advice.

---

