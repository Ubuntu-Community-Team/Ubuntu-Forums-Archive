---
title: "zombie process: exe waiting ch: do_exit"
date: 2012-01-15
forum: General Help
---

### Post by DouglasAdams on 2012-01-15
help!
please help.
i currently have eleven (yes, 11 !) zombied processes named: exe
under waiting channel it says: do_exit
(i wish it would)
i've tried killing them but no joy.
any ideas please?

---

### Post by Paddy Landau on 2012-01-15
I see no one has answered you, so I'll do my best.

A zombie process is one that has ended, but its parent process has failed to collect information from it. So it just hangs around waiting, but not doing anything. (Google *linux zombie process* for more information.)

If you know its parent process, kill it. You could try the command *pstree* to find its parent.

The easiest way by far to eliminate it if you don't know the parent process is to simply log out and in again (you don't need to reboot unless the process is owned by root).

---

### Post by DouglasAdams on 2012-01-15
i really don't want to logout whenever i have a problem, that's far too windows. i have always been told that Linux is far more controlable, so i would have thought that there should be some way to kill these rabid processes.
i tried pstree, and sudo'd the command too, same result:

% pstree exe
No such user name: exe 

any other thoughts please?

---

### Post by |{urse on 2012-01-15
Oh try killing all wine related stuff.

sudo killall -9 the.exeandanythingwinerelated

---

### Post by DouglasAdams on 2012-01-15
i don't have anything wine running.
synaptic even says that "wine", wine with numbers, wine with tricks, wine with fish, wine with chips ... lots and lots of wines are all NOT even installed.

---

### Post by |{urse on 2012-01-15
Haha, I see, you were using .exe perjoratively, Linux executables dont have an .exe extension so it confused me. 

can you open a terminal and post the output of the command

> top for me?

Wonder if [http://ubuntuforums.org/showthread.php?t=1342711](http://ubuntuforums.org/showthread.php?t=1342711) is the reason..

Are you running chrome or chromium?

---

### Post by DouglasAdams on 2012-01-16
> **|{urse said:**
> 
1)
Haha, I see, you were using .exe perjoratively, Linux executables dont have an .exe extension so it confused me. 
2)
can you open a terminal and post the output of the command

 for me?
3)
Wonder if [http://ubuntuforums.org/showthread.php?t=1342711](http://ubuntuforums.org/showthread.php?t=1342711) is the reason..
4)
Are you running chrome or chromium?
1)
no, nothing to do with ".exe" - but "exe"
i do know that linux doesn't use .exe
2)
the zombied exe processes do not show with top, they are off the screen, so i am attaching a screenshot of a system monitor display sorted by "status"
3)
i had high hopes when i read this post, someone said "uninstall (purged with aptitude) flashplugin-installer" - although i used synaptic to do the uninstall. however, the "exe's" are still there.
4)
chromium (see attached)

---

### Post by Paddy Landau on 2012-01-16
> **DouglasAdams said:**
> % pstree exe
Just *pstree* on its own. Find your "exe" there to discover its parent. Then we can make progress.

> **|{urse said:**
> ... so it confused me.
I'm also a bit confused; I've never seen an application called *exe*.

The thread that |{urse pointed out may be your solution. It looks like a fault with Adobe's Flash. Use this command:
```
sudo apt-get purge flashplugin-installer
```Log out, log in again, and see if they return after viewing YouTube.

---

### Post by DouglasAdams on 2012-01-16
> **Paddy Landau said:**
> 
1)
Just *pstree* on its own. Find your "exe" there to discover its parent. Then we can make progress.

2)
I'm also a bit confused; I've never seen an application called *exe*.

3)
The thread that |{urse pointed out may be your solution. It looks like a fault with Adobe's Flash. Use this command:
```
sudo apt-get purge flashplugin-installer
```Log out, log in again, and see if they return after viewing YouTube.

1)
sorry, i didn't realise.
not sure if this is going work but here goes ...
```
     &#9500;&#9472;chromium-browse&#9472;&#9516;&#9472;chromium-browse&#9472;&#9472;&#9472;{chromium-brows}
     &#9474;                 &#9500;&#9472;chromium-browse&#9472;&#9516;&#9472;npviewer.bin&#9472;&#9472;&#9472;6*[{npviewer.bin}]
     &#9474;                 &#9474;                 &#9492;&#9472;{chromium-brows}
     &#9474;                 &#9500;&#9472;chromium-browse&#9472;&#9516;&#9472;java&#9472;&#9472;&#9472;28*[{java}]
     &#9474;                 &#9474;                 &#9492;&#9472;5*[{chromium-brows}]
     &#9474;                 &#9500;&#9472;chromium-browse&#9472;&#9472;&#9472;2*[{chromium-brows}]
     &#9474;                 &#9500;&#9472;2*[chromium-browse]
     &#9474;                 &#9500;&#9472;chromium-browse&#9472;&#9472;&#9472;10*[{chromium-brows}]
     &#9474;                 &#9500;&#9472;22*[exe]
     &#9474;                 &#9492;&#9472;52*[{chromium-brows}]
     &#9500;&#9472;chromium-browse&#9472;&#9516;&#9472;4*[chromium-browse&#9472;&#9472;&#9472;4*[{chromium-brows}]]
     &#9474;                 &#9492;&#9472;34*[chromium-browse&#9472;&#9472;&#9472;3*[{chromium-brows}]]

```

2)
new to me too

3)
is doing the ```
sudo apt-get purge flashplugin-installer
``` different from doing what i've already done, i.e. uninstall flashplugin-installer using synaptic?

```

$ sudo apt-get purge flashplugin-installer
[sudo] password for ######: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed

```


i would like to point out that i had not been to youtube.

---

### Post by mastablasta on 2012-01-16
is that the whole tree?
You can mark more in terminal (scroll up and down) to copy and apste here than it is on screen you know.
 
> **DouglasAdams said:**
> 1)
 
3)
is doing the ```
sudo apt-get purge flashplugin-installer
``` different from doing what i've already done, i.e. uninstall flashplugin-installer using synaptic?
 

 
yes it is as purge command completelly removes all traces. uninstall could leave leave some config files behind. 
 
[http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html](http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html)

---

### Post by DouglasAdams on 2012-01-16
> **mastablasta said:**
> 
1)
is that the whole tree?
do you need / want the whole tree?

2)
yes it is as purge command completelly removes all traces. uninstall could leave leave some config files behind. 


1)
no, just the part that showed the tree for the exe's
plus the extra chromium since there was two of them.

2)
sorry, i know i said "uninstall", however, i actually did a "mark for complete removal" ... is that the same then?

---

### Post by Paddy Landau on 2012-01-16
> **DouglasAdams said:**
> ... "mark for complete removal" ... is that the same then?
Yes, it is the same.

When you removed flashplugin-installer, did you remember to log out and in again?

I notice that you are using a different version of Chrome from me. What version of Ubuntu are you using (I'm using 11.04)? Did you install standard from the repositories?

Do bear in mind that a zombie process does not take up any resources, so you don't need to panic about it. It could be a bug in Chromium (Google), or it could be a bug in Flash (Adobe).

If nothing else, it will be fixed in a future update.

---

### Post by |{urse on 2012-01-17
Excellent, is the death star complete though? lol

Yeah, I wonder who's swell idea it was to name a program "exe".

---

