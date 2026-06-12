---
title: "execute command at startup"
date: 2006-03-12
forum: General Help
---

### Post by steve196 on 2006-03-12
Into which file do you write commands, that you want to be executed at every startup?
Thanks!

---

### Post by Svictor on 2006-03-12
There would be several answers to this. Try using "bum" (install from the repos, through synaptic ar apt-get ...) if you need to configure the scripts that launch before gnome. Otherwise, there is an application in the gnome menus (don't remember the name though ... something about "startup" or "session" in tha "preferences" or "administration" menus I think)

---

### Post by Xian on 2006-03-12
Read this [POST](http://ubuntuforums.org/showpost.php?p=606737) for more information.

---

### Post by steve196 on 2006-03-12
I followed the post, that Xian linked, and rebooted afterwards, but it looks like the two commands were not executed.
I did not use the "sessions" panel, since the two commands I want require root privileges.

---

### Post by Xian on 2006-03-12
Try and execute the script in a terminal...any errors??

---

### Post by steve196 on 2006-03-13
Yes. it executes without any errors.

---

### Post by hw-tph on 2006-03-13
So is your script a Debian init script? I.e. does it implement the start¸stop, restart actions? Did you read /etc/init.d/README? Have you read chapter 9.3 of the Debian Policy Manual?


Håkan

---

### Post by steve196 on 2006-03-13
Nothing like that. Just two commands:
> 
dhcpcd eth0
dhcpcd start eth0

That is the script.
Wow, I thought Linux would have something simple, like autoexec.bat or the startup registry entries in windows. I think, I will start the commands by hand for the time being.

---

### Post by Jason_25 on 2006-03-13
Make a file in /etc/init.d with the commands you want inside.  Then 
```

sudo chmod +x 'name of file'
sudo update-rc.d 'name of file' defaults

```
It should then work on the next restart.

---

### Post by steve196 on 2006-03-13
Thank you!
Now it works. I didn´t know, scripts needed to be executables.

---

### Post by Xian on 2006-03-13
[QUOTE=steve196]Yes. it executes without any errors.[/QUOTE]

How on earth did you execute the script when it wasn't executable?? :-k

---

### Post by dcstar on 2006-03-14
[QUOTE=Xian]How on earth did you execute the script when it wasn't executable?? :-k[/QUOTE]
Lined it up against the wall and shot it??    :confused:      ;)

---

### Post by steve196 on 2006-03-14
> How on earth did you execute the script when it wasn't executable??
sudo sh scriptname

---

### Post by cx2610 on 2006-03-30
How would you UNDO this. I made a file in /etc/init.d called bootcmds, followed this thread, everything works.

But now, I have two things to ask.

1) suppose i don't want this anymore?

2) is it a one time procedure... suppose I want more commands, so i just add them, can i take away old commands. can the file have NO commands?

Thanks a lot,

Reehan

---

### Post by dcstar on 2006-03-30
[QUOTE=cx2610]How would you UNDO this. I made a file in /etc/init.d called bootcmds, followed this thread, everything works.

But now, I have two things to ask.

1) suppose i don't want this anymore?

2) is it a one time procedure... suppose I want more commands, so i just add them, can i take away old commands. can the file have NO commands?

Thanks a lot,

Reehan[/QUOTE]
1) If you don't want it to run, either delete/rename it or remove the links to it.

Anything in /etc/init.d is used by links the various /etc/rc?.d directories.

2) Yes, yes and yes.

---

### Post by cx2610 on 2006-04-04
Okay, now i have a problem.

I have one command in the bootcmds file, namely "torsmo". Did the update-rc.d stuff. Rebooted and no torsmo on my screen. But when I shutdown, it hangs at a certain point and says "torsmo: can't find display". Then continues to shutdown after like 3 seconds. Any insight?

Reehan

---

### Post by dcstar on 2006-04-05
[QUOTE=cx2610]Okay, now i have a problem.

I have one command in the bootcmds file, namely "torsmo". Did the update-rc.d stuff. Rebooted and no torsmo on my screen. But when I shutdown, it hangs at a certain point and says "torsmo: can't find display". Then continues to shutdown after like 3 seconds. Any insight?

Reehan[/QUOTE]
There is still a link to it in rc0.d (the shutdown scripts).

---

### Post by cx2610 on 2006-04-05
Yeah, the link is still there. I don't know if this is the place I should post this but I want to know why it doesn't display torsmo when I boot up. i.e. if I boot up, open a terminal and write ">torsmo", it draws my system stats on the desktop. But I want that done automagically at boot up. Is there something special I have to do to the desktop???

Thanks for all your help folks.

Reehan

---

