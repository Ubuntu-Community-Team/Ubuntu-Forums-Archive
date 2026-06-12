---
title: "Kill process script at logout"
date: 2011-08-20
forum: General Help
---

### Post by liquid150 on 2011-08-20
I need to add a script that kills cairo dock every time i log out. I've tried various things but I don't seem to have any clue how to do it. Big time newbie here, so keep it clear and concise if you can.

Thanks in advance.

---

### Post by dave01945 on 2011-08-20
you just need a script that kill's the PID of the dock and i believe that script needs to be called from /etc/gdm/postsession/default

if you put this in /etc/gdm/postsession/default it should kill it i haven;t got cairo-dock so can't try it here

```
kill -9 $(pidof cairo-dock)
```

to enter that in there just type and make sure you enter it above ```
exit 0
```

```
sudo nano /etc/gdm/PostSession/default
```

then ctrl-o to save and ctrl-x to exit

---

### Post by liquid150 on 2011-08-20
> **dave01945 said:**
> you just need a script that kill's the PID of the dock and i believe that script needs to be called from /etc/gdm/postsession/default

PID? How do I get the script in that directory? How do I get it to call from there?

Like I said, I am a big-time newbie.

---

### Post by dave01945 on 2011-08-20
hi edited my original post with more instructions

hope it helps

edit: you may need to change gdm to kdm just realised your on kubuntu

---

### Post by liquid150 on 2011-08-20
Do I create the script in gedit? I tried putting a killall script i made in gedit into a root folder, but it didn't let me (maybe because I wasn't using sudo in the terminal, and i don't know how?).

---

### Post by dave01945 on 2011-08-20
it will be easier to run the commands in terminal if you want to use gedit just run 

```
kdesu gedit /etc/kdm/PostSession/Default
```

then enter this command in there above the exit 0

```
kill -9 $(pidof cairo-dock)
```

this should work but i am using ubuntu not kubuntu so can't verify it

---

### Post by liquid150 on 2011-08-20
How would i do it, step by step, if i wanted to ignore gedit and just do it in terminal?

the help is greatly appreciated!!

---

### Post by dave01945 on 2011-08-20
ok your firdt step would be to open terminal and enter

```
sudo nano /etc/kdm/PostSession/Default
```

that should open a file similar to this

```
#!/bin/sh


exit 0
```

then you want to edit it too look like this

```
#!/bin/sh

**kill -9 $(pidof cairo-dock)**

exit 0
```

note the bit in bold is **all** i have added if there is more in there **do not** change it

then you press *ctrl-O* to save the file then *ctrl-x* to exit the editor

try this if you have anymore trouble just reply and i will try to help

---

### Post by liquid150 on 2011-08-20
It opened a file in terminal, with nothing in it at all. So I copied everything in your file, but when i hit ctrl-O it asked where to save, i hit enter and it said there is no such file, and didn't let me go any further.

---

### Post by dave01945 on 2011-08-21
did you copy the command or type it in cause if the file wasn't there it should have created it but if you missed some of the capital letters in the file path that would give you that error

does your terminal complete words when you press [tab] if so try typing it n like this

```
sudo nano /etc/kdm/Po**[tab]**S**[tab]**/De**[tab]**
```

---

### Post by liquid150 on 2011-08-21
I typed it with all the capitals. I'm not finding a file like the one you mentioned yet just manually clicking through root. I see stuff like /etc/kde4/kdm/Xsession though.

My shutdown scripts might be in a different place?

---

### Post by dave01945 on 2011-08-21
is there a **postsession** folder in the */etc/kde4/kdm/* directory i'm not on kde so that 's not on my system

---

### Post by liquid150 on 2011-08-21
No, there are just a series of script programs called Xreset, Xsession, Xstartup, Xsetup, and Xwilling.

---

### Post by dave01945 on 2011-08-21
ok can you tell me what it say's when you type

```
echo $SHELL
```

and is there a file in your home called .bash_logout the dot indicates it is a hidden file but in the terminal type

```
ls -a
```

and it will show all files

--edit--

don't think that will work in your home directory type

```
cd .kde
ls -a 
```

---

### Post by liquid150 on 2011-08-21
> **dave01945 said:**
> ok can you tell me what it say's when you type

```
echo $SHELL
```
It says /bin/bash

> and is there a file in your home called .bash_logout the dot indicates it is a hidden file but in the terminal type

```
ls -a
```

and it will show all files

--edit--

don't think that will work in your home directory type

```
cd .kde
ls -a 
```

here you go
```
liquid150@liquid150-FK562AA-ABA-a6614f:~/.kde$ ls -a
.                                   share
..                                  socket-liquid150-FK562AA-ABA-a6614f
Autostart                           tmp-liquid150-FK562AA-ABA-a6614f
cache-liquid150-FK562AA-ABA-a6614f
liquid150@liquid150-FK562AA-ABA-a6614f:~/.kde$ 
```

---

### Post by dave01945 on 2011-08-21
ok according to what i found you need to be in the .kde directory 
 *cd .kde* from home then when in there use these commands

```
mkdir shutdown
cd shutdown
nano myscript  ## this will open the text editor
kill -9 $(pidof cairo-dock)
*ctrl-o to save*
*ctrl-x to exit*
chmod +x myscript
```

that should work again haven't been able to test it because ubuntu uses gdm/postsession

hopefully this will work :D

---

### Post by liquid150 on 2011-08-21
It doesn't look like I had any luck. All the commands went through fine, saved fine, etc. I restarted to see if cairo-dock got killed when I restarted.

Nope, still have two instances of cairo-dock running in processes. Maybe change the script to be killall? I have successfully rebooted and gotten only one instance of cairo-dock, but I had to killall manually and reboot. If I reboot without using killall, I get two overlapping instances of the process and it looks kinda messed up when I use the dock with two overlapping instances.

edit: tried the same steps and used a killall command. That didn't work either. Doesn't look like my system is running the script. Probably need to find out where the shutdown scripts are...doing some research but so far no luck.

---

### Post by dave01945 on 2011-08-21
yeah i can't seem to find any other place to add scripts to run at logout there is one other place you can try it didn't work on my system but might be different on yours it's a file called 

.bash_logout in your home directory it only worked on mine when i loged out of the tty (ctrl-alt-F1-6) it may be worth a try it might work on on kde

you can also add a script to /etc/init.d/ and they can be called when the computer goes for shutdown but it won't work if you only logout

think you put the script in that directory then sym link it to /etc/rc6.d/ for reboot and /etc/rc0.d/ for shutdown

---

### Post by liquid150 on 2011-08-21
> **dave01945 said:**
> 
you can also add a script to /etc/init.d/ and they can be called when the computer goes for shutdown but it won't work if you only logout

I tried doing that before, actually, because this is what was said in my research (believe me, I tried to figure this out on my own pretty bad). Problem is, I don't know how to add a script to that folder! Of course, being a newbie, I wrote the script and saved it in Documents, then tried to use the GUI to plug it in to that directory. It told me I didn't have privileges to do so.

How would I get the script in there?

Also, I am currently looking at another option. KDE System Options has a GUI style script and program addition tool to run on Startup, Pre-startup, and Shutdown. However, after adding it several times I can't seem to get it to work. If that works out, I'll make sure to post how I did it.

---

### Post by liquid150 on 2011-08-21
Okay, a little update. I got the script into init.d, and it worked, but my desktop widgets were showing in the foreground in front of my browser. No good!!

Now when I am creating the script in init.d, it's not coming up as an executable. What am I doing wrong, there?

---

### Post by dave01945 on 2011-08-21
after creating the script in init.d you will need to make it executable by using the command

```
sudo chmod +x scriptname
``` 

the chmod command changes the mode of a file or directory the +x adds executable to it

for the script to be run automatically it needs to have a symbolic link in one of the /etc/rc#.d/ directories the # is a number between 0 and 6 these numbers are the different runlevels 0 is the shutdown runlevel and 6 is for reboot

the symbolic link also needs to be pre=fixed with either K or S and a number K scripts are run before S scripts and then they are run in numerical order

so to make the sym link you would run

```
sudo ln -s /etc/init.d/scriptname /etc/rc0.d/K20script name
```

and then do the same for /etc/rc6.d also if you look through the directories there are a few README files that might help

---

### Post by liquid150 on 2011-08-21
And BAM, that did it, at least I think it has. I've only done one reboot so far, but I've only got one instance of cairo dock running this time.

Here's what I did:
1. Navigated to init.d.
```
cd /etc/init.d
```
2. Created new script called killcairo.sh.
```
sudo nano killcairo.sh
```
3. Wrote script to kill all instances of Cairo Dock.
```
sudo killall cairo-dock
```
4. Saved with ctrl-o. Exit with ctrl-x.
5. Make the script executable.
```
sudo chmod +x killcairo.sh
```
6. Add to Shutdown call.
```
sudo ln -s /etc/init.d/scriptname /etc/rc0.d/K20killcairo.sh
```
7. Add to reboot call.
```
sudo ln -s /etc/init.d/scriptname /etc/rc6.d/K20killcairo.sh
```
8. Open System Settings GUI, navigate to "Startup and Shutdown."
9. Click "Add Script." Click the browse button on the right of the new window, navigate to /etc/init.d and select "killcairo.sh." Have "Create as symlink" checked.
10. The script is added to the "Script File" menu. Utilize drop down menu in "Run on" column to change to run on "Shutdown."

I am not 100% positive the last 3 steps are necessary, but it worked after all that. I am going to reboot again to double check.

---

### Post by dave01945 on 2011-08-21
good glad it's working hopefully it's all good after your next reboot i'm sure it will be though

:P

---

### Post by liquid150 on 2011-08-21
I think messing with the system settings to see if skipping them would work broke my setup. I would like to just start all over. Is there any way to remove the links to the Shutdown and restart calls?

---

### Post by liquid150 on 2011-08-21
Well, drat...I've removed everything and replaced everything twice now and it's not working. Maybe it wasn't working the first time and I got lucky? Kindof at a loss...I think I had it and maybe I'm missing something...

---

### Post by liquid150 on 2011-08-21
Any more input on this issue? I can't seem to remember if I did get it to work, or if it was just a fluke. :(

---

### Post by dave01945 on 2011-08-22
can't think of anything else to try just yet there all the commands i can find to run scripts a shutdown

maybe you can try investigate why 2 instances are created as maybe it is being started twice

---

### Post by liquid150 on 2011-08-23
Fixed it. I had to start over from scratch, and come up with a new name for the script file. I performed the exact same steps outlined above, but instead of calling it "killcairo.sh" i called it "kilcairo.sh." Not sure why removing the old stuff didn't work, but I'm not complaining.

---

