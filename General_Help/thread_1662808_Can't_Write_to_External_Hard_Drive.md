---
title: "Can't Write to External Hard Drive"
date: 2011-01-08
forum: General Help
---

### Post by ron177 on 2011-01-08
I have an external hard drive which I have just formated as ext4. But for some reason I can't write to it. I wonder why? Can anyone help me with this? I can open the external drive in my Ubuntu system but for some reason I can't write anything to it. I can't backup any data. Why is this?

---

### Post by Verbeck on 2011-01-08
try chown-ing the mount point
from a terminal (applications>accessories):
```
sudo chown -R $USER:$USER /path/to/mountpoint
```

---

### Post by ron177 on 2011-01-08
I ran the command you gave me on the terminal and here's the output:

chown: cannot access `/path/to/mountpoint': No such file or directory

how can I chown it now? what do you mean by chowning?

---

### Post by Verbeck on 2011-01-08
you'll need to change the '/path/to/mountpoint' in that command to where the drive is mounted. open the partition from the icon on the desktop or places menu and press ctrl+L to see the location
eg: /media/Data

---

### Post by ron177 on 2011-01-09
Brilliant. 

So I did what you said. Since I have two partitions on that external hd one called "Archive" and the other "Synchronization" I have the following locations:

/media/Synchronization
/media/Archive

So now you're telling me to go back to the Terminal, put in the command line you said earlier and then do what? could you please explain it a little further. 

Appreciatively,

Ron

---

### Post by ron177 on 2011-01-09
So I tried these commands but nothing worked so far:

sudo chown -R $USER:$USER /path/to/media
sudo chown -R $USER:$USER /path/to/media/Archive

---

### Post by coffeecat on 2011-01-09
The paths need to be:

/media/Synchronization
/media/Archive

The commands Verbeck gave you are quite correct but you can simplify them slightly to good effect. In the examples below change 'username' for your login/account name.

```
sudo chown username: /media/Synchronization
sudo chown username: /media/Archive
```By leaving out the recursive -R option you change the ownership of the root of the filesystem so that you can write to it. This is a little-understood feature of Linux filesystems. By using the -R recursive option you change the ownership of all the files already there. Use the command without the -R and you will be able to write to it, and you will still be able to write to it when you next mount it.

The other simplification is that 'username:' - note the trailing colon - in the command sets your default group without you having to type it. But do remember to substitute your user name for 'username'.

---

### Post by ron177 on 2011-01-10
This fixed my problem. You're great! Thanks so much!

---

