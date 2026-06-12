---
title: "chmod : command not found"
date: 2012-04-23
forum: General Help
---

### Post by srinathr on 2012-04-23
Hi,

when i run chmod a+x filename, its showing
chmod: command not found

some suggested, it happens because of path settings...
 
echo $PATH
/home/usrp3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

But path is fine...even in /bin folder where chmod resides ....its showing command not found...

Can somebody help me out ??

---

### Post by matt_symes on 2012-04-23
Hi

Open a terminal and type these commands. Post back the results.

```
sudo updatedb && locate chmod
```

What does this return ?
```

whereis chmod
```

and this

```
ls -l /bin/chmod
```

If you use the full path, does it work ?

```
/bin/chmod a+x filename
```

Kind regards

---

### Post by srinathr on 2012-04-23
Thank you.
its working with full path....





regards

Sreenath Kambala

---

### Post by matt_symes on 2012-04-23
Hi

That's quite odd and would point to a path problem somehow.

Open a terminal and copy and past this into the terminal

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games chmod a+x filename
```Change filename as required. Post back the output from the terminal by copying and pasting from the terminal into your next post.

I want to see the entire output of that command. Does it work ?

Kind regards

---

### Post by AlexanderDGreat on 2013-02-16
Thanks. It's working like a cute little puppy.

---

