---
title: "change command prompt"
date: 2011-09-13
forum: General Help
---

### Post by eddski on 2011-09-13
how do i change the command prompt to include just my current path?

---

### Post by papibe on 2011-09-13
The prompt format is set by the bash variable $PS1.

Try this:
```
$ echo $PS1
```
Could you give an example of how you want your prompt to be displayed?

Regards.

EDIT: here are a couple of guides for the special codes: [this]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html") and [this]("http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html").

---

### Post by nothingspecial on 2011-09-13
type ```
gedit .bashrc
```

Look for a lines like this
```

 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="Red"]w[/COLOR]\$ '
```

Change the lowercase w (in red) to an uppercase W.

Save and close, then in a terminal type

```
. ~/.bashrc
```

---

### Post by kerry_s on 2011-09-13
> **nothingspecial said:**
> type ```
gedit .bashrc
```

Look for a lines like this
```

 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="Red"]w[/COLOR]\$ '
```

Change the lowercase w (in red) to an uppercase W.

Save and close, then in a terminal type

```
. ~/.bashrc
```

In lubuntu it would be leafpad, not gedit.

---

### Post by nothingspecial on 2011-09-13
> **kerry_s said:**
> In lubuntu it would be leafpad, not gedit.

So it would. :)

In any *buntu

```
nano .bashrc
```

Ctrl-O then Enter to save

Ctrl-X to exit.

---

### Post by eddski on 2011-09-14
for papibe's question, i would to display the absolute path, or pwd, can i execute that command in the prompt?

---

### Post by papibe on 2011-09-14
Try this:
```
PS1="\w$  "
```
That would be give you the absolute path, except inside your home, in which it'll use the ~ abbreviation.

Hope it helps,
Regards.

---

### Post by eddski on 2011-09-16
thanks, but what i was looking for is " ${PWD}\$ " not sure if thats good syntax but it works for me

---

