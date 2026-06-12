---
title: "How to execute a command line in a shell script"
date: 2012-01-22
forum: General Help
---

### Post by sixteenornumber on 2012-01-22
I'm in the process of writing a script in c-shell that will execute the following command.
[B]
*rsync -zav --log-file=/home/earth/log/back_up_logs/rsync-music-$(date +%Y-%m-%d).log --delete-after /media/pool1/Music/ /media/pool-ext1/Music/*[/B]

the command itself works just fine but i cant figure out how to execute command from within a script. I've been searching around and found something about 

***echo $PATH >> </usr/bin/rsync...>***

but that doesn't work.  any ideas?

---

### Post by davethewave83 on 2012-01-22
> **sixteenornumber said:**
> I'm in the process of writing a script in c-shell that will execute the following command.
[B]
*rsync -zav --log-file=/home/earth/log/back_up_logs/rsync-music-$(date +%Y-%m-%d).log --delete-after /media/pool1/Music/ /media/pool-ext1/Music/*[/B]

the command itself works just fine but i cant figure out how to execute command from within a script. I've been searching around and found something about 

***echo $PATH >> </usr/bin/rsync...>***

but that doesn't work.  any ideas?

Paste that into a new empty file, right click the file, click properties, permissions and make it executable. When you execute the file by double clicking it, then it should run the command.

---

### Post by lechien73 on 2012-01-22
If the script is in c-shell, then I'd create an empty text file, and add:

```
#!/bin/csh

rsync -zav --log-file=/home/earth/log/back_up_logs/rsync-music-$(date +%Y-%m-%d).log --delete-after /media/pool1/Music/ /media/pool-ext1/Music/
```

Then, as davethewave83 says right click on the file, select Properties and make it executable.

Do you want the paths supplied to rsync to change, or will they always be the same?

---

### Post by sixteenornumber on 2012-01-22
edit

---

### Post by sixteenornumber on 2012-01-22
> **lechien73 said:**
> If the script is in c-shell, then I'd create an empty text file, and add:

```
#!/bin/csh

rsync -zav --log-file=/home/earth/log/back_up_logs/rsync-music-$(date +%Y-%m-%d).log --delete-after /media/pool1/Music/ /media/pool-ext1/Music/
```Then, as davethewave83 says right click on the file, select Properties and make it executable.

Do you want the paths supplied to rsync to change, or will they always be the same?


i see what you did there! :)

the paths are going to stay the same but that is something i was thinking about.  I guess i could `touch` a file with the path then remove the file when the shell ends.  would that work?

---

### Post by sixteenornumber on 2012-01-22
wait, im still not following..

I have an empty file that reads,

[B][I]#!/bin/csh

rsync -zav --log-file=/home/earth/log/back_up_logs/rsync-music-$(date +%Y-%m-%d).log --delete-after /media/pool1/Music/ /media/pool-ext1/Music/[/I][/B]

csh is reading the ...$(date... as a variable.  It's not running

---

### Post by sixteenornumber on 2012-01-22
:::solved:::

I had to tell the shell to access the command line.  to do this, i opened a terminal and used the command,
[B][I]
echo $PATH[/I][/B]

the output was, 
***/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games***

i copied that line and pasted it into the 2nd line of my shell so that it looks like the following,

[B][I]#!/bin/csh 
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games[/I][/B]

---

### Post by lechien73 on 2012-01-22
Great...well done :D

If you get chance, could you use the **Thread Tools** menu at the top of the page, and mark the issue as [SOLVED]?

Thanks

---

### Post by sixteenornumber on 2012-01-22
> **lechien73 said:**
> 
If you get chance, could you use the **Thread Tools** menu at the top of the page, and mark the issue as [SOLVED]?

Thanks


I was wondering how to do that, thanks

---

