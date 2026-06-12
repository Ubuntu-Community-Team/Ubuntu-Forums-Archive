---
title: "How to start Slim ?"
date: 2009-11-15
forum: General Help
---

### Post by Somme on 2009-11-15
As simple as that - how do I start/use Slim ? I mean, after installing it, I still don't see it on boot .. Any ideas ?

---

### Post by howefield on 2009-11-15
Try here...

[http://ubuntu-lxde.wikidot.com/slim](http://ubuntu-lxde.wikidot.com/slim)

---

### Post by Somme on 2009-11-15
> **howefield said:**
> Try here...

[http://ubuntu-lxde.wikidot.com/slim](http://ubuntu-lxde.wikidot.com/slim)

It didn't worked ( and I don't see the point of the duplicate startlxde entry ).
[COLOR=Gray]** I'm on Openbox ..[/COLOR]

---

### Post by ajgreeny on 2009-11-15
There's a typo in that link which says :-
> and created a text file ~/..xinitrc with the contents *exec startlxde*
The name of the file should only have one dot, ie .xinitrc, not ..xinitrc.

Rename the file you made if you used two dots.

---

### Post by Somme on 2009-11-15
> **ajgreeny said:**
> There's a typo in that link which says :-

The name of the file should only have one dot, ie .xinitrc, not ..xinitrc.

Rename the file you made if you used two dots.

I know ( I've been doing minimal setups for the past year or so ). Anyway, I still can't figure this out .. Who stole my /etc/rc.conf ? :roll:
Also, if we are talking about .xinitrc, shouldn't it be called only by the startx command ?

---

### Post by ajgreeny on 2009-11-15
> Who stole my /etc/rc.conf ?
See [http://ubuntuforums.org/showthread.php?t=946682](http://ubuntuforums.org/showthread.php?t=946682) about that.  It's almost unique to Arch.

---

### Post by Somme on 2009-11-15
> **ajgreeny said:**
> See [http://ubuntuforums.org/showthread.php?t=946682](http://ubuntuforums.org/showthread.php?t=946682) about that.  It's almost unique to Arch.

Umh, yeah - ok. I saw the rc.local and even tried to edit it, but hell, it's just a collection of something I can't understand.
How would I add/remove applications/daemons that should run on boot ( boot .. login .. desktop ) ?

---

### Post by ajgreeny on 2009-11-15
In 9.04 you can add them to /etc/init.d as shell scripts, and that usually works, but other than that I'm not sure.

---

### Post by falconindy on 2009-11-15
> **Somme said:**
> Anyway, I still can't figure this out .. Who stole my /etc/rc.conf ? :roll:?
I'm holding your /etc/inittab for ransom, too, until I get my cat back.

*shakes fist*

---

