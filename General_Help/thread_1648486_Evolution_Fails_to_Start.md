---
title: "Evolution Fails to Start"
date: 2010-12-18
forum: General Help
---

### Post by klyndt on 2010-12-18
I just installed Ubuntu 10.04 fresh and was putting my preferences back in for Firefox and MythTV and such when I noticed Evolution wouldn't start. I would click on it and the cursor would change for about 5 seconds and then nothing. I tried uninstalling Evolution (big mistake), but after I got back into the desktop, Evolution still wouldn't start.  I can't seem to find anything around here that deals with this.  Where should I start to debug this?

If you are going to ask me to do some sudo apt-get stuff will you please put the whole command so I don't mess it up!

Thanks,
Klyndt

---

### Post by zpletan on 2010-12-18
What happens when you run 'evolution' (without quotes) from a terminal window?

---

### Post by klyndt on 2010-12-18
On a whim I tried to start evolution from a terminal window. I get this error:
```
(evolution:27357): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.
Aborted

```
so I typed 
sudo evolution
and that seemed to get it working. I'm a little confused why I would need to run evolution with administrator privileges.  So my new question is, where do I need to change the permissions to get this to work like it is supposed to?  I don't have a .evolution folder in my home area.

*Edit*
Glad to see you and I were thinking on the same page.

---

### Post by klyndt on 2010-12-18
So I did a search on permission problems and this link pretty much had the same issues as I.
[http://ubuntuforums.org/showthread.php?t=1640912](http://ubuntuforums.org/showthread.php?t=1640912)

I looked at my home folder and root owned it. So I performed this:
```
sudo chown -R klyndt:klyndt /home/klyndt
```

Evolution starts correctly now.  I'm not sure how my home directory got changed to root since I had not done any sudo stuff up to this point.

---

