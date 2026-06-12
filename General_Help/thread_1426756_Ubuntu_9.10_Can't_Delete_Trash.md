---
title: "Ubuntu 9.10 Can't Delete Trash"
date: 2010-03-10
forum: General Help
---

### Post by Anokel on 2010-03-10
For some reason I am unable to empty the trash. It seemed to be working fine then all of a sudden it just stopped. Not sure what I did to create this problem.

I was trying to figure out a way to empty the trash and I now have another problem.

I was following these instructions 

> Using Andrea Francia trash-cli package is very helpful :
 sudo empty-trash empty your trash with any permission problem whereas

sudo su
empty-trash

 empties **root** trash !
I installed Trash-cli package and now my trash wont do anything. Before it was giving me an error saying can't delete trash fail or whatever. Now it does nothing.

So I was wondering how to remove trash-cli package and how to also delete all the trash in the bin.

Thanks guys.:popcorn:

---

### Post by drs305 on 2010-03-10
*trash-cli* is in synaptic, so if that is how you installed it you should be able to remove it via synaptic as well. 

From the command line, you should be able to remove APT-installed packages with:
```
sudo apt-get purge trash-cli
```

Here is a link on "Trash" that may help you empty all your Trash bins:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by rogue_0111 on 2010-03-10
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1335180](http://ubuntuforums.org/showthread.php?t=1335180)

or

[http://superuser.com/questions/111222/how-do-i-empty-the-trash-in-ubuntu-9-10](http://superuser.com/questions/111222/how-do-i-empty-the-trash-in-ubuntu-9-10)

or 

[http://ubuntuguide.net/empty-ubuntu-gnome-trash-in-command-line](http://ubuntuguide.net/empty-ubuntu-gnome-trash-in-command-line)

---

