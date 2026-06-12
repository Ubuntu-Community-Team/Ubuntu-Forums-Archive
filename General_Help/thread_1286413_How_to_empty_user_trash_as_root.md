---
title: "How to empty user trash as root"
date: 2009-10-08
forum: General Help
---

### Post by gareththomasnz on 2009-10-08
I had a bunch of stuff that would not delete from my trash as it had been deleted from flash drives etc

I logged in as root & cold not see those files in the trash.

LUCKY: I found this solution on another forum...

sudo rm -rf /home/username/.local/share/Trash/ 

Now my trash is finally empty after weeks

---

### Post by DReeves922 on 2009-10-09
I've got a few gigs worth of old backup files and stuff from portable drives that I can't get out of my trash.  The above command didn't do anything. :-/

Anyone else have an idea?

---

### Post by jeremyswalker on 2009-10-09
> **DReeves922 said:**
> I've got a few gigs worth of old backup files and stuff from portable drives that I can't get out of my trash.  The above command didn't do anything. :-/

Anyone else have an idea?

What was the output when you tried the command above?

---

### Post by drs305 on 2009-10-09
> **DReeves922 said:**
> I've got a few gigs worth of old backup files and stuff from portable drives that I can't get out of my trash.  The above command didn't do anything. :-/

Anyone else have an idea?

Are you running an older version of Ubuntu (pre-Hardy)? The trash location used to be in a different folder. 

Also, is it possible the trash is in a folder called .Trash-0 on a non-linux filesystem?

I wrote a guide about finding and deleting Trash that may give you some insights on the issue (even if your drive isn't full):

[ How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by sleepitoff on 2009-10-09
I've had this problem before in Ubuntu and I always just ran sudo nautilus from the terminal, emptied the trash, then closed nautilus.

---

### Post by DReeves922 on 2009-10-10
Using 9.04.

this is what I get with the command:
```

dan@Main-Linux:~$ sudo rm -rf /home/username/.local/share/Trash/ 
[sudo] password for dan: 
dan@Main-Linux:~$ 

```
Trash is all still there.


I've also tried going through gksudo nautilus then browsing to:
/home/username/.local/share/Trash/ 
/root/.local/share/trash
  
Just clicking on TRASH under nautlius says "Sorry, could not display all the contents of "trash": operation not supported."

---

### Post by jeremyswalker on 2009-10-10
You are replacing "username" in "/home/**username**/.local/share/Trash/" with *your* user name, aren't you?

---

### Post by DReeves922 on 2009-10-10
Of course :)

---

### Post by jeremyswalker on 2009-10-10
Just had to check. :-k

---

### Post by DReeves922 on 2009-10-14
Hrm, loaded the drive in KNoppix and deleted everything with no problems.  Go figure. :P

---

### Post by gareththomasnz on 2010-03-26
I must have needed this half a dozen times already - every time I come to this thread to remember it.

---

### Post by amulet on 2010-04-22
After hunting for a solution to empty my trash folder, I found that this worked a treat in Karmic.

cd ~/.local/share/Trash/files
rm -rf *

:)

---

### Post by gareththomasnz on 2011-04-26
sudo rm -rf ~/.local/share/Trash

---

