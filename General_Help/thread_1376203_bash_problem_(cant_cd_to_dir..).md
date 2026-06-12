---
title: "bash problem (cant cd to dir..)"
date: 2010-01-08
forum: General Help
---

### Post by sofamensch on 2010-01-08
i am clueless, no idea with google and forum.

i tried to write a little bash script, that runs some programms.
its okay to run programs with ./program .
but since some programms love to be run from their main directory, i tried to cd there.
I always get "cant cd to xyz".

I tried all, absolute paths, relative paths, the dirs absolutely exist, there are no " " empty signs within the name.
also "cd .." gives me "can't cd to .."

thanks in advance

---

### Post by falconindy on 2010-01-08
It would help greatly if you were to post the script and any other relevant commands in their entirety.

---

### Post by manosx on 2010-01-08
/path/to/.program ?

---

### Post by warfacegod on 2010-01-08
sudo cd /path?

---

### Post by lostinxlation on 2010-01-09
What's the permission of xyz ? Execution permission must be on to get into the dir.

---

### Post by sofamensch on 2010-01-09
> **warfacegod said:**
> sudo cd /path?
User has no sudo rights. But its inside his homefolder-

I set the +x permission to the dir, no difference.
I even set the permission to 777.

I minimized the script to this for now:


```

#!/bin/bash
cd "~/srcds/left4dead2"
screen -A -m -d -S l4d2_legal ./srcds_run

```

i also tried
cd "/home/gameserver/srcds/left4dead2"
cd "/srcds/left4dead2"

```

gameserver@sofaserver:~$ cd srcds/left4dead2
gameserver@sofaserver:~/srcds/left4dead2$ cd ../..
gameserver@sofaserver:~$ sh startservers.sh
cd: 2: can't cd to ~/srcds/left4dead2
: not founds.sh: 4:

```

---

### Post by falconindy on 2010-01-09
Get rid of the quotes. If you want to quote the path (which you don't need to in this case), use $HOME in place of the ~.

```

 [haruko@quake ~]$ cd "~/dev/dwm"
bash: cd: ~/dev/dwm: No such file or directory
 [haruko@quake ~]$ cd ~/dev/dwm
 [haruko@quake ~/dev/dwm]$ 
```

---

### Post by sofamensch on 2010-01-09
Nope thats not it.
I tried without ""; with (and without) $Home ..

Everything works, but not when i write it into an .sh file and try to run it.

Additional info: i am logged in from an ssh console. (But i dont think that matters)

---

### Post by zanetu on 2010-01-09
> **sofamensch said:**
> Nope thats not it.
I tried without ""; with (and without) $Home ..

Everything works, but not when i write it into an .sh file and try to run it.

Additional info: i am logged in from an ssh console. (But i dont think that matters)

Try running your script with "." (source command) rather than "sh".
Reference:
[http://forums.macosxhints.com/showthread.php?t=37697](http://forums.macosxhints.com/showthread.php?t=37697)

---

### Post by falconindy on 2010-01-10
> ```
gameserver@sofaserver:~$ cd srcds/left4dead2
gameserver@sofaserver:~/srcds/left4dead2$ cd ../..
gameserver@sofaserver:~$ sh startservers.sh
[B]cd: 2: can't cd to ~/srcds/left4dead2
: not founds.sh: 4:[/B]
```
Just noticed that there's a stray newline character in there. Is there a reason you can't post the script in its entirety? The problem is purely syntactic.

---

