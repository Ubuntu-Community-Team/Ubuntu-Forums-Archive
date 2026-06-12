---
title: "Bash No such file or directory."
date: 2011-08-07
forum: General Help
---

### Post by TDLShow on 2011-08-07
First I press.
Control+Alt+F1

Then.
```
Sudo /etc/init.d/gdm stop
```Which works totally fine.

But when I try and install my Nvidia driver which is a .run file...
```
cd '/home/USERNAMEHERE/Templates/FILENAMEHERE.run'
```...it gives me.
```
bash: cd '/home/USERNAMEHERE/Templates/FILENAMEHERE.run: No such file or directory.
```This is very upsetting. 
I know Linux is case sensitive and I know that damn file exists.

---

### Post by mendhak on 2011-08-07
This may be an amateurish answer, but 'cd' is used to go into a directory.  The .run file would be a binary of some sort, so you probably want to run just this:

> /home/USERNAMEHERE/Templates/FILENAMEHERE.run

to run the file

---

### Post by Matt__ on 2011-08-07
you are trying to cd into the actual file rather than the directory that it is in. remove cd and it will run


//edit: /me sighs, too slow in typing again...like mendhak says

---

### Post by mikewhatever on 2011-08-07
Try this instead:
```
cd /home/USERNAMEHERE/Templates

sudo sh ./FILENAMEHERE.run
```

or

```
sudo sh /home/USERNAMEHERE/Templates/FILENAMEHERE.run
```

---

### Post by CatKiller on 2011-08-07
Installing random stuff downloaded over the Internet is not generally preferable to installing from the repositories. You may have a very good reason for wanting to use the drivers from NVidia's site, but most people don't and only do that because they'd do that in Windows.

---

### Post by mendhak on 2011-08-07
Actually that's a good point.  I followed the instructions on this page to get my Nvidia drivers:

[http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html](http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html)

I had initially tried using the .run file from the NVidia site but it was becoming a series of hurldes.

---

