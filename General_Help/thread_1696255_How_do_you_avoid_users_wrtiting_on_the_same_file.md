---
title: "How do you avoid users wrtiting on the same file?"
date: 2011-02-27
forum: General Help
---

### Post by userubunt on 2011-02-27
Is it possible to forbid that more then one user open the same file in rw mode?
In windows when you open a file that another user is using, there's ad advise and you have to open it in read only mode

I installed ubuntu 10.04 desktop edition on 3 pc (there is not a server-client architecture). I installed samba.
(and smbfs)

put the strings:
[name]
comment = ...
path = /...
guest ok = yes
read only = no
create mask = 0777
directory mask =0777

Computers that access to that directory do (on boot, with root privileges)
mount -t smbfs -o username="user",password="pass" //192.168.0.12/name /mnt/cartelladimontaggio

But if two users access to the same file, both are authorized writing on it! So changes made by one are lost when the other save.

How is it possibile to avoid this?

---

### Post by userubunt on 2011-02-28
Can someone help?

---

### Post by dcstar on 2011-03-01
> **userubunt said:**
> Can someone help?

[http://www.samba.org/samba/docs/using_samba/ch08.html](http://www.samba.org/samba/docs/using_samba/ch08.html)

Have a read of the Locks section, you may want to use the **Strict Locking** option.

---

### Post by userubunt on 2011-04-05
I tryed what you told me but it does not work.
I understood that:
1)that's a problem of "file locking" or at least advisory locking
2)Kernel linux has a mandatory locking available with option "mand" in "mount" function, but this does not work how i need: you can access the file for reading and you have no advise so if the one who put a lock modify the file and than close it you are not aware of anything and you can overwrite
3)Another solution should be using a sccs but this seems to be projected for other scope, not for locking an open file. It seems to me that this wouldn't work.
4)then you have the function flock(int file, int operation), but you have to invoke it from a script or a code. That would be very difficult to modify all programs that access data file for inserting flock every time they use the open function.

How is it possible that nobody knows how to avoid this problem? 
No one use 2-3 pc on a network, peer to peer, like always happen with windows? Solving this problem is mandatory for this kind of use, it's so strange that lacks an accessible solution

---

### Post by userubunt on 2011-04-14
Solved:

the situation you have in a windows intranet can be achived downloading openoffice.org

gnumeric do not have file locking. Lotus simphony has but i didn't find the way to activate it under ubuntu.

So install openoffice
sudo gedit /etc/openoffice/soffice.sh
There is an option "file locking = auto", you put "file locking = yes"
And that's it.

Surely openoffice must be the only application that opens your files, and you can not control for example txt files but that's the same situation you have in windows

For options in samba there is the page linked by dcstar

Bye

---

