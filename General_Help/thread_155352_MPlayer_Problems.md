---
title: "MPlayer Problems"
date: 2006-04-04
forum: General Help
---

### Post by Gracye on 2006-04-04
I want to install MPlayer but I can't.  I get this when I do it in Terminal:

> 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mpalyer
grace@ubuntu:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is a virtual package provided by:
  mplayer-nogui 1:1.0-pre7cvs20050716-0.1ubuntu9.1
  mplayer-k6 1:1.0-pre7cvs20050716-0.1ubuntu9.1
  mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9.1
  mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9.1
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
You should explicitly select one to install.
E: Package mplayer has no installation candidate


 And in Add Applications: 
> 
This program is not currently installable. It should be available in the "multiverse" section of the repository. Enable that section in the **Repositories** dialog in the **Settings** menu to install it.


I've enabled the section and it still isn't working.  Is there a way to enable it through terminal?

---

### Post by akiro.yamamoto on 2006-04-04
What it is really saying is that you should specify which version to install.
For example
```

sudo apt-get install mplayer-386

```
Should install the one most likely to work on any IBM clone system.
I would recommend that you use Synaptic for your package installation needs, it is very easy to search for and install your packages there.
Or you can try the Add Application Dialog
I hope this tip helps. ;)

---

### Post by Gracye on 2006-04-05
Thank you very much! It's installing now :)

---

