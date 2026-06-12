---
title: "How does the terminal know where to search for binary programs?"
date: 2006-03-17
forum: General Help
---

### Post by Bazon on 2006-03-17
Hello!

I know:
Normaly, when running a program via terminal, the program binary is in /usr/bin

e.g.:
```
$ xmms 
```
--> /usr/bin/xmms is executed.

But i compiled *(I mean: ./configure, make, sudo make install ....)* a program *(patched mplayer)* which was stored in /usr/local/binary

So when I now type 
```
$ mplayer
```
--> /usr/**local**/bin/mplayer is started
and not /usr/bin/mplayer (which also exists, this is the version from Synaptic...)

[b]So my question is:
Why is /usr/local/bin/mplayer started and not /usr/bin/mplayer ?
Is there some file where the path to commands is stored?[/b]


[i](Comment:
This is no problem for me, it is good that way.
But i'd like to understand and be able to control that, e.g. for making such double-installations [i need both versions of mplayer!] possible....)[/i]

Thanks,
Bazon

---

### Post by xrado on 2006-03-17
type

which mplayer

and you will see the real path that is started

see $PATH variable by

echo $PATH

---

### Post by Bazon on 2006-03-17
Thanks, 

but still my question:
***Why*** is tihis one selected and not the other one?

And what does *echo $PATH* tell me?
*(I'm really a Linux newbee....)*

When I type *echo $PATH* I get:
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

My interpretation:
The first mentioned path has higher priority than the later ones, that would explain why /usr/local/mplayer is started and not /usr/bin/mplayer.

Is this correct?

Thanks,
Bazon

---

### Post by Lux Perpetua on 2006-03-17
$PATH is a setting that the shell refers to when you tell it to execute a program. Your particular $PATH lists 8 directories which will be searched for executable programs when you issue a command. The terminal searches the directories listed in the $PATH variable in order, so you are correct, /usr/local/bin is searched before /usr/bin. If you want to use a program that isn't in one of those directories, you have to specify on the command line the full path to the executable program. For example, if the program resides in your home directory, you could run it as ~/(program) or /home/(username)/(program). To use /usr/bin/mplayer instead of /usr/local/bin/mplayer, you can invoke it explicitly as /usr/bin/mplayer. Alternatively, you can actually customize $PATH in your shell initialization script.

---

### Post by Bazon on 2006-03-17
Ah, excellent, now i understand!

Thanks! :D

---

### Post by markthecarp on 2006-03-17
Please also note that /usr/local/mplayer will not be in your path while /usr/local/bin/mplayer will be in your path.

---

### Post by Christmas on 2006-03-17
Hy all,

Great question! I'm a newbie and this was one of my many questions, it's good now that i found out.

---

### Post by IYY on 2006-03-17
If you want to quickly find out which file will be run when you type in a certain command, use the following:

**which <command>**

For example, **which xmms** will print out something like **/usr/bin/xmms**.

---

