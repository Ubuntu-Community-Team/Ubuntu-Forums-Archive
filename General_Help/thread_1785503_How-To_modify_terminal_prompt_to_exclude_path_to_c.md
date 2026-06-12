---
title: "How-To modify terminal prompt to exclude path to current working directory"
date: 2011-06-18
forum: General Help
---

### Post by GeoffreyBernardo on 2011-06-18
By default, the terminal prompt looks like this:

[COLOR=SeaGreen]**geoffrey@ubuntu:~$**[/COLOR]

It always shows the path to the current working directory, e.g. if I change to my Documents directory, it will look like this:

**[COLOR=SeaGreen]geoffrey@ubuntu:~/Documents$[/COLOR]**

and it can be quite long if I go to a subdirectory which is several levels below the home directory.

How can I modify the terminal's settings so that the prompt is only a sigils:

[COLOR=SeaGreen]**$**[/COLOR]

leaving me with more space for commands. The path to the current working directory could stil be seen in the title bar of the terminal window.

---

### Post by AlphaLexman on 2011-06-18
```
ps1="\$ "
```
**EDIT:** The ps should be in CAPS, I can't get it to save that way for some reason!
> PS1="\$ "

---

### Post by GeoffreyBernardo on 2011-06-18
Thanks, man.

That works perfectly, except that the path is not updated in the title bar, but that is fine.

What does PS1 stand for?

---

### Post by AlphaLexman on 2011-06-18
> **GeoffreyBernardo said:**
> What does PS1 stand for?

**P**rompt **S**tring, level one. There are 4 levels total.

---

### Post by nothingspecial on 2011-06-18
You can change this permanently in your .bashrc

I happen to like knowing the name of the directory I am in at the prompt as I often work without X (no titles to tell me where I am).

```
nano .bashrc
```

Look for a line like this


```
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="Red"]w[/COLOR]\$ '
```

Change the lowercase w for an upper case W, so
```

 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="Lime"]W[/COLOR]\$ '
```

Press Ctrl-O to save (then Enter)

then Ctrl-X to exit

then

```
. ~/.bashrc
```

---

