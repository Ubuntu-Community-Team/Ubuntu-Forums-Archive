---
title: "Nautilus &quot;Open Terminal Here&quot; doesn't work"
date: 2010-08-31
forum: General Help
---

### Post by Cephi on 2010-08-31
I installed nautilus-open-terminal, and now the option "Open in Terminal" does show up in the context menu for me in Nautilus, and clicking it does open a terminal.  But it just opens to the home directory, every time, same as if I'd opened a terminal in the ordinary way.

I've tried to look for solutions to this, but I can't find anyone that even has the same problem.  Other people complaining about it all seem to be saying that a terminal doesn't even open for them, which is not the case for me.

I'm at a loss. Ideas would be appreciated.

Running Karmic, a brand new install.

---

### Post by coffeecat on 2010-08-31
Here in Lucid, it works just fine. If I open a terminal from a home Nautilus, I get the prompt:

```
coffeecat@amd4-Lucid:~$ 
```... which is correct. But if I navigate to the /etc/grub.d folder in Nautilus and open a terminal, I get:

```
coffeecat@amd4-Lucid:/etc/grub.d$ 
```... which is also correct.

Perhaps there's a bug in the Karmic version. If I get time later today, I'll boot into Karmic, install the open-terminal package, and see what I get.

---

### Post by Cephi on 2010-08-31
Well, I found the problem, but I still don't know how to fix it.  The "--working-directory" option doesn't work for me in opening a terminal.  That is, the command: 

```
gnome-terminal --working-directory="$DIR"
```

doesn't work.  When I use this command, typing it myself in a terminal, it opens another terminal to the home directory.  It completely ignores the option, no matter what I fill in for $DIR.  I have no idea why this isn't working.

---

### Post by inameiname on 2010-08-31
Perhaps reinstalling it might fix the issue.

sudo aptitude purge nautilus-open-terminal && sudo aptitude install nautilus-open-terminal

---

### Post by coffeecat on 2010-08-31
> **Cephi said:**
> Well, I found the problem, but I still don't know how to fix it.  The "--working-directory" option doesn't work for me in opening a terminal.  That is, the command: 

```
gnome-terminal --working-directory="$DIR"
```

I'm in Karmic now. Nautilus-open-terminal is working just as it did in Lucid - which is OK. And the gnome-terminal command with the --working-directory option works for me as well. Sorry I can't be of more help.

---

### Post by dankrusi on 2011-03-16
Have you tried looking at ~/.bashrc and making sure there are no custom commands in there overriding the cd to the dir...?

---

