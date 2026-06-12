---
title: "Terminal Help"
date: 2009-07-25
forum: General Help
---

### Post by conradin on 2009-07-25
Hi all, 
Im sort of embarrassed to ask, this is a total newbie question. Mainly Im not certian ow to ask, and probably just unable to find the solution via searching, by virtue of this. 

I want to know how to return to the terminal after launchingind a program. For example, lets say I type:
[code]
sudo gedit /etc/fstab
[code]

I'm editing fstab, and it has just occurred to me, I want to launch some other program like gparted. Oh, but wait my terminal window is unavailable. Sure, I can, open another, but lets say I don't want to do that, ow can I keep whatever program Ive opened via the terminal open, and return to using the terminal?

---

### Post by synapsys on 2009-07-25
Easy... add & to the end of any command to leave terminal open.

```
sudo gedit /etc/fstab &
```

This will run gedit in the background and let you continue to use the terminal as you wish.

---

### Post by qamelian on 2009-07-25
Follow the first command with a space and the "&" character and enclose the whole command in parentheses, so:
```
(gksu gedit /etc/fstab &)
```

---

### Post by wojox on 2009-07-25
Why would you run gparted while editing fstab?

---

### Post by CatKiller on 2009-07-25
Don't use sudo for graphical applications. Use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") instead.

---

### Post by Bartender on 2009-07-25
Catkiller -
I've seen this mentioned a hundred times, but still don't get it.  aysiu's explanation isn't doing it for me either.

How does one know when to use gksudo?  There must be some trick to remember.  Using the term graphical or non-graphical doesn't mean anything to me, and probly doesn't make sense to a lot of others either...

---

### Post by CatKiller on 2009-07-25
> **Bartender said:**
> Catkiller -
I've seen this mentioned a hundred times, but still don't get it.  aysiu's explanation isn't doing it for me either.

How does one know when to use gksudo?  There must be some trick to remember.  Using the term graphical or non-graphical doesn't mean anything to me, and probly doesn't make sense to a lot of others either...

It's quite simple. The command-line is text based. Anything that runs in the terminal window is text based. Anything that opens a new window to do stuff, generally involving icons to interact with, is not text based. This is a graphical application.

Strictly speaking, the problem is with the permissions on configuration files created by those applications. sudo runs with root permissions, but uses the user's Home folder environment. gksudo runs with root permissions, but uses root's Home folder environment. These are both perfectly fine until you run an application as root that also creates configuration files in the user's Home directory, at which point those configuration files will be owned by root and inaccessible to the user &#8212; even though they are in the user's Home directory &#8212; and so those applications will no longer run for that user. The programs that exhibit this behaviour are generally graphical ones; text based programs do not normally create these files.

You may have seen this mentioned a hundred times but the problem, and the distinction between the two classes of application, have also been explained many times.

---

### Post by oldos2er on 2009-07-25
You can also open another tab in the same terminal window; File, Open tab.

---

### Post by conradin on 2009-07-26
> **wojox said:**
> Why would you run gparted while editing fstab?

It was just an example.
Thank you all, my question is answered!

---

