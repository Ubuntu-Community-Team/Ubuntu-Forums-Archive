---
title: "NO HDD in Ubuntu"
date: 2011-04-26
forum: General Help
---

### Post by ujjal on 2011-04-26
I am a new user of ubuntu 10.10 . I was using windows XP [installed in c drive] .Now, I have installed Ubuntu 10.10 from boot menu on sda5. When I am starting pc there is no option to select the OS by which i want to start pc. It is redirecting to ubuntu 10.10 by default. And in ubuntu I can't find my files of HDD. My HDD is of 320 GB. I am noticing that [COLOR=Blue]270 GB is free[/COLOR]. IS my drives has been formatted or not? How to regain my all files and folders?

Info may be you required:
When installing there was an option Like "Use entire disk" and i have clicked on it.

Now please give me a solution. there are precious files on HDD.

---

### Post by lisati on 2011-04-26
I hope you made a backup of all your important files: if you chose "use entire disk" then the copy in Windows will have been deleted.

---

### Post by idoitprone on 2011-04-26
when you clicked use entire disk, you deleted windows and installed ubuntu. By writing over the partition that you deleted, you have remove all possibility of data recovery. Sorry that is all i can say. If you want proof [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) run this boot script. It should only show ubuntu

---

### Post by chkneater on 2011-04-26
If you did indeed click on "Use entire disk" by mistake instead of "Install side by side" then you most likely formatted the entire drive by mistake.  I don't know of any info recovery programs myself but I know they exist.  You my get lucky and be able to recover it for a price, but Mr. Hindsight always says "Your problem is you didn't back up your hard drive."

Ubuntu is good though, hope you like it.  If in doubt ask first.

---

### Post by Quackers on 2011-04-26
You could try testdisk
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
or using Herman's howto
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by ujjal on 2011-04-26
OH GOD,
I have no backup. I have lost all of my important things. And now I am half died. Thanks guys.

Okay...
Now, in ubuntu there is no partition I think. how to create that?

---

### Post by idoitprone on 2011-04-26
> **ujjal said:**
> OH GOD,
I have no backup. I have lost all of my important things. And now I am half died. Thanks guys.

Okay...
Now, in ubuntu there is no partition I think. how to create that?


easy way install gparted or use the default disk utility. Next time clonezilla is you friend lol

---

