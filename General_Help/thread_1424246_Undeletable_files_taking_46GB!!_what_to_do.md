---
title: "Undeletable files taking 46GB!! what to do??"
date: 2010-03-07
forum: General Help
---

### Post by Muhammad Mustafa on 2010-03-07
I have Ubuntu 9.10 installed using wupi inside windows
I just found about these files now, tried every possible way to delete the, including terminal commands mentioned here with no luck at all
Take a look at these files in the screen shot here:
[http://img717.imageshack.us/img717/4169/badfiles.png](http://img717.imageshack.us/img717/4169/badfiles.png)
they are totally un renamable or deletable, I tried even to login to windows and use unloaker and other utilities with no success at all
Any help here is very appreciated
Thanks

---

### Post by Ex-windows on 2010-03-07
Are these on the ubuntu side or windows side ??? What about changing permissions?  I had a similar situation and was able to use the terminal to change the permissions and them move to trash. Sorry I cant offer more help

---

### Post by Muhammad Mustafa on 2010-03-07
> **Ex-windows said:**
> Are these on the ubuntu side or windows side ??? What about changing permissions?  I had a similar situation and was able to use the terminal to change the permissions and them move to trash. Sorry I cant offer more help

The problem exist in both sides, ub and win
I can't change permissions as well and files names are not readable in the terminal, so I can't do anything with files in terminal, I just tried to completely delete the containing folder but failed to do so
any suggestion people?

---

### Post by lakersforce on 2010-03-07
Are the undeletable file on Ubuntu or Windows (aka where they there before you installed ubuntu?)

If so I would suggest, albeit it might be dangerous, to boot the livecd, mount your partition and delete the files.

Undeletable files are a sign of faulty disk or an (if we are talking about Windows) infected system.

---

### Post by 2hot6ft2 on 2010-03-07
They're shown as programs. Kinda a weird location 1 1 1 1 1. If you want to delete them you can do this at your own risk.
In nautilus (the file browser) click on Edit > Preferences then the Behaviour tab.
Select Enable Include a delete command that bypasses trash (the last option at the very bottom). Then
In  a Terminal
Applications > Accessories > Terminal
```
gksu nautilus
```
browse to the files and select them or the folder containing them, right click and select Delete.

That should PERMANENTLY delete them. Then close the file browser (nautilus), you don't want to be browsing around as root.

---

### Post by Muhammad Mustafa on 2010-03-09
Thanks a lot for your help guys, I really appreciate it

> **2hot6ft2 said:**
> They're shown as programs. Kinda a weird location 1 1 1 1 1. If you want to delete them you can do this at your own risk.
In nautilus (the file browser) click on Edit > Preferences then the Behaviour tab.
Select Enable Include a delete command that bypasses trash (the last option at the very bottom). Then
In  a Terminal
Applications > Accessories > Terminal
```
gksu nautilus
```browse to the files and select them or the folder containing them, right click and select Delete.

That should PERMANENTLY delete them. Then close the file browser (nautilus), you don't want to be browsing around as root.

I did exactly what you suggested here, when tried to right-click and delete, there's no delete option there! so, I just hit the delete key and got the delete confirmation message, agreed to it and this too failed to delete these files
See this image for the error message I received:
[http://img687.imageshack.us/img687/1654/undel.png](http://img687.imageshack.us/img687/1654/undel.png)

So, any other suggestions here??

---

### Post by cpressland on 2010-03-09
Looks like it could be a dodgy filesystem in my opinion. So if you've tried using 'sudo rm' in terminal and you've also tried the same method on a LiveCD the best bet would be to backup all essential files and repartition / format the drive. This is classic NTFS phail!

---

### Post by denver on 2010-03-09
That looks like a really bad file system problem. Run a filesystem check on the "LIFE" volume. Either that or the filenames are written in some strange character set (im betting file system corruption though).

If it's a ext3/4 or a Linux file system of any kind, you can unmount it and then run:

```
fsck -a /dev/sdX
```

where sdX is the "LIFE volume.

If the volume is ext2/3/4 you should use:

```
e2fsck -p /dev/sdX 
```

If its a windows filesystem, try the windows utility for checking filesystems. Can't remember what its called though (its been 5 years since i touched a windows machine).

Best of luck to you!

---

### Post by cpressland on 2010-03-09
chkdsk / scandisk :P

---

### Post by denver on 2010-03-09
> **cpressland said:**
> chkdsk / scandisk :P

RIGHT! that's the one!

thanks cpressland!

---

### Post by Muhammad Mustafa on 2010-03-31
Thanks a lot guys for your help, I really appreciate each word here
For anyone ran into a similar problem, the solution is below, don't waste your time :D
I tried everything and all failed to solve anything, so, in such cases, do your self a favor and format it :(

> **cpressland said:**
> Looks like it could be a dodgy filesystem in my opinion. So if you've tried using 'sudo rm' in terminal and you've also tried the same method on a LiveCD the best bet would be to backup all essential files and repartition / format the drive. This is classic NTFS phail!

---

### Post by Dayofswords on 2010-03-31
> **Muhammad Mustafa said:**
> Thanks a lot guys for your help, I really appreciate each word here
For anyone ran into a similar problem, the solution is below, don't waste your time :D
I tried everything and all failed to solve anything, so, in such cases, do your self a favor and format it :(

wubi really should be used just for trying, so after a while, something went wrong

dont get me wrong, wubi is good, just not as good as ubuntu have its own disk area

---

