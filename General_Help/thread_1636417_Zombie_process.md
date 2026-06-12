---
title: "Zombie process"
date: 2010-12-03
forum: General Help
---

### Post by nomko on 2010-12-03
Yesterday evening i've noticed that i have a zombie process called EXE. It's not using any memory, i can't kill it (in terminal sudo kill # (#=process no) ) and when i try to get some more info (right click on the process and select last option) my whole system freezes.
 
I don't know which program this process belongs to or to find out which application uses it and how to kill it. 
 
Anybody who has a suggestion??
Many thanks!!

---

### Post by KiLaHuRtZ on 2010-12-03
Try...

```
sudo kill -9 [PID]
```

---

### Post by nomko on 2010-12-03
> **KiLaHuRtZ said:**
> Try...

```
sudo kill -9 [PID]
```

Doesn't work :(
any other solution??

---

### Post by lykeion on 2010-12-03
EXE sounds like a windows executable. Do you run any Windows application via wine?
If so try to kill the wine process to kill the EXE process.
You can find wine processes on command-line using ps:
```
ps aux|grep wine
```
And the PID is the second nr after username, kill it forcefully with:
```
kill -9 PID
```

---

### Post by KiLaHuRtZ on 2010-12-03
You can also try pstree and find the parent PID and try to kill that.  Just don't try and kill init, or you will be rebooting.

```
pstree -p
```

---

### Post by nomko on 2010-12-04
> **lykeion said:**
> EXE sounds like a windows executable. Do you run any Windows application via wine?
If so try to kill the wine process to kill the EXE process.
You can find wine processes on command-line using ps:
```
ps aux|grep wine
```And the PID is the second nr after username, kill it forcefully with:
```
kill -9 PID
```

If i wanted to use Windows tools under Ubuntu, I  would really stay with Windows, so: no! 
I don't use Windows tools under Ubuntu with Wine.

The command i'm gonna try later!

And the command kill -9 [PID] didn't work which i already meantioned!

---

### Post by smo0th on 2010-12-04
if your ps aux|grep wine shows a status D then it's waiting for IO, something happened like a disconnected drive and if it doesn't come back you will need to reboot.

---

### Post by nomko on 2010-12-04
> **smo0th said:**
> if your ps aux|grep wine shows a status D then it's waiting for IO, something happened like a disconnected drive and if it doesn't come back you will need to reboot.

This is what i get
nomko     1910  0.0  0.0   3692  1144 pts/0    S+   19:25   0:00 grep --color=auto wine


But i don't us Wine. If i want to use Windows tools, i would've installed Windows instead of Ubuntu ;-)

---

### Post by smo0th on 2010-12-04
lol my fault on misunderstooding lines xD

what does ps ax |grep EXE shows up?

---

### Post by nomko on 2010-12-05
I get this:

[I]nomko@nomko-desktop:~$ ps ax |grep EXE
 2554 pts/0    S+     0:00 grep --color=auto E[/I]

Don't know what this means....

---

### Post by lykeion on 2010-12-05
The ps command list current processes, and piping it through grep will filter the results, 
so looking at your output there is no process with the name EXE running on your system (except the ps command you just entered). 
Note that in Linux files and names are case sensitive, so you might find it by grepping "exe" instead of "EXE".

Where did you actually see this EXE process? Was it in System Monitor? If so, could you attach a screenshot of it (Alt+PrintScreen)?

---

### Post by mcduck on 2010-12-05
A single zombie shouldn't be a problem and you usually only need to worry if you are seeing lots of them (they are usually just IDs in the process table, so unless you are running into some max process limit they don't cause any problems).

But anyway, you can't kill a zombie process directly, it's already dead. Instead you need to find it's parent process and kill that instead.

(That much we can learn form any zombie horror movie/game. It's useless to waste time fighting individual zombies, you have to find the crazy scientist who's raising the dead to streets. :D)

[http://www.linuxsa.org.au/tips/zombies.html]("http://www.linuxsa.org.au/tips/zombies.html")

---

### Post by lykeion on 2010-12-05
mcduck is very right about zombie processes, but I sensed that OP was a bit nervous about an unknown process and wanted to find out what it was.

And regarding "real" zombies, shouldn't it be possible to kill it if you destroy their brain? [http://zombie.wikia.com/wiki/How_To_Kill_Zombies](http://zombie.wikia.com/wiki/How_To_Kill_Zombies)

---

### Post by mcduck on 2010-12-05
> **lykeion said:**
> 
And regarding "real" zombies, shouldn't it be possible to kill it if you destroy their brain? [http://zombie.wikia.com/wiki/How_To_Kill_Zombies](http://zombie.wikia.com/wiki/How_To_Kill_Zombies)
yep, but the rest of the horde will still come to get you. Zombies are only dangerous as large groups so killing individual ones wouldn't help much as long as the crazy guy keeps on raising more of them. :D

Besides, decapitation works for most common zombie types zombies, but I've definitely ran into ones that crawl towards you even without a head. Mad scientists aren't the most reliable type of personality and when such people make experiments all kinds of unexpected results can happen.

---

### Post by WebNuLL on 2010-12-05
You must kill "partent" process to kill zombie process.

---

### Post by nomko on 2010-12-05
> **lykeion said:**
> The ps command list current processes, and piping it through grep will filter the results, 
so looking at your output there is no process with the name EXE running on your system (except the ps command you just entered). 
Note that in Linux files and names are case sensitive, so you might find it by grepping "exe" instead of "EXE".

Where did you actually see this EXE process? Was it in System Monitor? If so, could you attach a screenshot of it (Alt+PrintScreen)?

Here's the screenshot: [IMG]http://img12.imageshack.us/img12/3323/systeemmonitor051220100.png[/IMG]

---

### Post by mcduck on 2010-12-05
Open the View menu and enable "Show Dependencies", that should help you find the parent process.

You might have to also set it to show all processes instead of just your own (although if the parent process isn't your own but belongs to root, you probably don't want to kill it just because of a single zombie)

---

### Post by lykeion on 2010-12-05
The "exe" process might be related to Chrome/Flash plugin:
[http://www.google.com/support/forum/p/Chrome/thread?tid=3fbf25d62f51677e&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=3fbf25d62f51677e&hl=en)
[http://ubuntuforums.org/showthread.php?t=1351948](http://ubuntuforums.org/showthread.php?t=1351948)
[http://ubuntuforums.org/showthread.php?t=1396654](http://ubuntuforums.org/showthread.php?t=1396654)

---

### Post by nomko on 2010-12-05
> **lykeion said:**
> The "exe" process might be related to Chrome/Flash plugin:
[http://www.google.com/support/forum/p/Chrome/thread?tid=3fbf25d62f51677e&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=3fbf25d62f51677e&hl=en)
[http://ubuntuforums.org/showthread.php?t=1351948](http://ubuntuforums.org/showthread.php?t=1351948)
[http://ubuntuforums.org/showthread.php?t=1396654](http://ubuntuforums.org/showthread.php?t=1396654)

I'll never gonna use Chrome or Chromium for the reason to me Chrome/Chromium doesn't feel complete. That's no issue here.

---

### Post by nomko on 2010-12-05
> **mcduck said:**
> Open the View menu and enable "Show Dependencies", that should help you find the parent process.

You might have to also set it to show all processes instead of just your own (although if the parent process isn't your own but belongs to root, you probably don't want to kill it just because of a single zombie)


For som reason the exe (zombie) is now shown directly under Nautilus. Why should Nautilus have a zombie process??

[http://img404.imageshack.us/img404/2640/selectie0512201008.png](http://img404.imageshack.us/img404/2640/selectie0512201008.png)

---

### Post by lykeion on 2010-12-05
Hard to say, you should read the link about zombie processes provided by mcduck.
And like other posters have mentioned, kill the parent process to get rid of the zombie process:
```
killall nautilus
```

---

### Post by smo0th on 2010-12-05
means there's no 'EXE' process running, to see if there's a zombie process running type 

ps ax |grep Z

you should see something like 

2956 ?        Z      0:00 /usr/sbin/apache2 -k start

then you should type sudo kill -9 2956

---

### Post by nomko on 2010-12-06
> **smo0th said:**
> means there's no 'EXE' process running, to see if there's a zombie process running type 
 
ps ax |grep Z
 
you should see something like 
 
2956 ? Z 0:00 /usr/sbin/apache2 -k start
 
then you should type sudo kill -9 2956
 
Like i mentioned before, the command sudo kill -9 [PID] doesn't work.
I'll try the option to kill Nautilus and see what's happening then.

---

### Post by wojox on 2010-12-06
Are you having any problems with Flash?

Run:

```
ps aux | grep exe | grep -v grep
```

C# uses .exe file extensions.

---

### Post by nomko on 2010-12-06
> **wojox said:**
> Are you having any problems with Flash?

Run:

```
ps aux | grep exe | grep -v grep
```C# uses .exe file extensions.

This is what i get:

[I]nomko@nomko-desktop:~$ ps aux | grep exe | grep -v grep
nomko     1527  0.0  0.0   7276  3308 ?        S    19:27   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
nomko     1538  0.0  0.0      0     0 ?        Z    19:27   0:00 [exe] <defunct>
nomko@nomko-desktop:~$ 
[/I]

---

### Post by nomko on 2010-12-06
> **lykeion said:**
> Hard to say, you should read the link about zombie processes provided by mcduck.
And like other posters have mentioned, kill the parent process to get rid of the zombie process:
```
killall nautilus
```

Didn't work. The exe process comes back after killing the nautilus process.

---

### Post by wojox on 2010-12-07
> **nomko said:**
> Didn't work. The exe process comes back after killing the nautilus process.

Are you using Nautilus Elementary?

---

### Post by nomko on 2010-12-07
This is what's been installed for nautilus:

nautilus
nautilus-data
nautilus-dropbox
nautilus-image-converter
nautilus-open-terminal
nautilus-sendto
nautilus-share

---

