---
title: "bug with find or ls?"
date: 2009-07-07
forum: General Help
---

### Post by PGScooter on 2009-07-07
In my opinion, the filename in the following situation should either not be listed by "ls" or it should be found by "find." Which is it? Or is there a reason that this unexpected behaviour occurs?

Thanks

```

root@system76-pc:/home/xinwei/bugreport# ls -l
total 4
d---r--r-- 2 root root 4096 2009-07-05 13:27 protected
root@system76-pc:/home/xinwei/bugreport# ls -l protected
total 0
-rw-r--r-- 1 xinwei xinwei 0 2009-07-05 13:27 canttouchthis
root@system76-pc:/home/xinwei/bugreport# exit
xinwei@system76-pc:~/bugreport$ ls -l protected/
ls: cannot access protected/canttouchthis: Permission denied
total 0
-????????? ? ? ? ?                ? canttouchthis
xinwei@system76-pc:~/bugreport$ find ./ -name canttouchthis
xinwei@system76-pc:~/bugreport$ sudo !!
sudo find ./ -name canttouchthis
./protected/canttouchthis
xinwei@system76-pc:~/bugreport$ 

```

---

### Post by jenkinbr on 2009-07-07
> **PGScooter said:**
> In my opinion, the filename in the following situation should either not be listed by "ls" or it should be found by "find." Which is it? Or is there a reason that this unexpected behaviour occurs?

Thanks

```

root@system76-pc:/home/xinwei/bugreport# ls -l
total 4
d---r--r-- 2 root root 4096 2009-07-05 13:27 protected
root@system76-pc:/home/xinwei/bugreport# ls -l protected
total 0
-rw-r--r-- 1 xinwei xinwei 0 2009-07-05 13:27 canttouchthis
root@system76-pc:/home/xinwei/bugreport# exit
xinwei@system76-pc:~/bugreport$ ls -l protected/
ls: cannot access protected/[COLOR="Red"]canttouchthis[/COLOR]: Permission denied
total 0
[COLOR="Red"]-????????? ? ? ? ?                ? canttouchthis[/COLOR]
xinwei@system76-pc:~/bugreport$ find ./ -name canttouchthis
xinwei@system76-pc:~/bugreport$ sudo !!
sudo find ./ -name canttouchthis
./protected/canttouchthis
xinwei@system76-pc:~/bugreport$ 

```
That is some very odd behavior ideed - How can you read a directory that doesn't have execute settings as a normal user?  The bits in red in the modified quote (all I did was add some color) are the most concerning.



I tried doing this, setting the same perissions as you have, and I get:

```
jenkinbr@jenkinbr:~$ sudo -i
root@jenkinbr:~# cd ~jenkinbr/
root@jenkinbr:/home/jenkinbr# ls -l | grep testdir
d---r--r--  2 jenkinbr jenkinbr      4096 2009-07-06 23:51 testdir
root@jenkinbr:/home/jenkinbr# cd testdir
root@jenkinbr:/home/jenkinbr/testdir# ls -l
total 0
-rw-r--r-- 1 jenkinbr jenkinbr 0 2009-07-06 23:51 cantseethis
root@jenkinbr:/home/jenkinbr/testdir# exit
logout
jenkinbr@jenkinbr:~$ ls -l | grep testdir
d---r--r--  2 jenkinbr jenkinbr      4096 2009-07-06 23:51 testdir
jenkinbr@jenkinbr:~$ ls -l testdir
ls: cannot open directory testdir: Permission denied
jenkinbr@jenkinbr:~$ find ./ -name cantseethis
find: `./testdir': Permission denied
jenkinbr@jenkinbr:~$ sudo !!
sudo find ./ -name cantseethis
./testdir/cantseethis
jenkinbr@jenkinbr:~$ 
```

This is clearly how it should behave, so I don't have that problem.

---

### Post by jpeddicord on 2009-07-07
> **jenkinbr said:**
> This is clearly how it should behave, so I don't have that problem.
Looks like your directory you created is owned by you, and not root as it is in PGScooter's example.


> **PGScooter said:**
> In my opinion, the filename in the following situation should either not be listed by "ls" or it should be found by "find." Which is it? Or is there a reason that this unexpected behaviour occurs?

Thanks

```

root@system76-pc:/home/xinwei/bugreport# ls -l
total 4
d---r--r-- 2 root root 4096 2009-07-05 13:27 protected
root@system76-pc:/home/xinwei/bugreport# ls -l protected
total 0
-rw-r--r-- 1 xinwei xinwei 0 2009-07-05 13:27 canttouchthis
root@system76-pc:/home/xinwei/bugreport# exit
xinwei@system76-pc:~/bugreport$ ls -l protected/
ls: cannot access protected/canttouchthis: Permission denied
total 0
-????????? ? ? ? ?                ? canttouchthis
xinwei@system76-pc:~/bugreport$ find ./ -name canttouchthis
xinwei@system76-pc:~/bugreport$ sudo !!
sudo find ./ -name canttouchthis
./protected/canttouchthis
xinwei@system76-pc:~/bugreport$ 

```

I believe this is due to the permissions you have set on the protected directory. You have read, but not execute. ls is able to see that there are files in the protected directory because you have the read permission set, but it cannot figure out the details of the files themselves because it cannot traverse the directory to see the them. Did that make sense? I'm sort of confusing myself. ):P

Not sure why find will refuse to list it, probably because it has to have the proper permissions to be able to show it.

---

### Post by jenkinbr on 2009-07-07
> **jacobmp92 said:**
> Looks like your directory you created is owned by you, and not root as it is in PGScooter's example.




I believe this is due to the permissions you have set on the protected directory. You have read, but not execute. ls is able to see that there are files in the protected directory because you have the read permission set, but it cannot figure out the details of the files themselves because it cannot traverse the directory to see the them. Did that make sense? I'm sort of confusing myself. ):P

Not sure why find will refuse to list it, probably because it has to have the proper permissions to be able to show it.
Good catch, heres my update:

```
jenkinbr@jenkinbr:~$ sudo chown root:root testdir
jenkinbr@jenkinbr:~$ ls -l | grep testdir
d---r--r--  2 root     root          4096 2009-07-06 23:51 testdir
jenkinbr@jenkinbr:~$ ls -l testdir
ls: cannot access testdir/cantseethis: Permission denied
total 0
-????????? ? ? ? ?                ? cantseethis
jenkinbr@jenkinbr:~$ 

```

So I do have that problem....very curious....

I still shouldn't be able to read the directory listing, though, I don't think?

---

### Post by PGScooter on 2009-07-07
well, I guess that's good if you don't have that problem!

I am using Jaunty 64-bit.

I just sent an email to the address in the man page. I will post back if I get a response.

Thanks for testing it out jenkinbr

---

### Post by jpeddicord on 2009-07-07
> **jenkinbr said:**
> Good catch, heres my update:

```
jenkinbr@jenkinbr:~$ sudo chown root:root testdir
jenkinbr@jenkinbr:~$ ls -l | grep testdir
d---r--r--  2 root     root          4096 2009-07-06 23:51 testdir
jenkinbr@jenkinbr:~$ ls -l testdir
ls: cannot access testdir/cantseethis: Permission denied
total 0
-????????? ? ? ? ?                ? cantseethis
jenkinbr@jenkinbr:~$ 

```

So I do have that problem....very curious....

I still shouldn't be able to read the directory listing, though, I don't think?

Things go wacko like that when r isn't paired with x on directories. Read gives you the ability to glance at the directory's contents, Execute lets you enter the directory and see a little more infomation. For general cases, they go hand in hand.

For example, you should be able to do a plain `ls testdir` (no -l) and it will just show "cantseethis." It just can't fetch the file attributes that the -l flag wants.

---

### Post by PGScooter on 2009-07-07
(last post was written without seeing previous two).

jacobmp,

thanks for the reply. That does make sense. I thought about that to, and read through the man page for find and could not find anything about that. They did have other stuff relating to permissions, but from what I understand, those are extra restrictions you can add if you choose and I did not see anything about defaults.

---

### Post by jpeddicord on 2009-07-07
> **PGScooter said:**
> well, I guess that's good if you don't have that problem!

I am using Jaunty 64-bit.

I just sent an email to the address in the man page. I will post back if I get a response.

Thanks for testing it out jenkinbr

If you sent it to [email]bug-coreutils@gnu.org[/email] (or -findutils as I see in the manpage) you probably won't get a response -- it's filesystem behavior, and doesn't have anything to do with the utilities themselves.

If it really was a bug, we'd probably have seen some kernel security releases pretty quickly. ;)

---

### Post by jenkinbr on 2009-07-07
> **jacobmp92 said:**
> Things go wacko like that when r isn't paired with x on directories. Read gives you the ability to glance at the directory's contents, Execute lets you enter the directory and see a little more infomation. For general cases, they go hand in hand.

For example, you should be able to do a plain `ls testdir` (no -l) and it will just show "cantseethis." It just can't fetch the file attributes that the -l flag wants.
I actually get a permission error, too, but it still displays the file.

It's still ok though, as I chmod everything to 000 if I don't want it to be seen by anyone besideds root (yes, I know encryption is a better option, but I don't work for the government, so I'm not really concerned)

```
jenkinbr@jenkinbr:~$ ls testdir
ls: cannot access testdir/cantseethis: Permission denied
cantseethis
jenkinbr@jenkinbr:~$ 

```

---

### Post by PGScooter on 2009-07-07
> **jacobmp92 said:**
> If you sent it to [email]bug-coreutils@gnu.org[/email] (or -findutils as I see in the manpage) you probably won't get a response -- it's filesystem behavior, and doesn't have anything to do with the utilities themselves.

If it really was a bug, we'd probably have seen some kernel security releases pretty quickly. ;)

OK, so should I just forget about it? I agree that ls is not at fault. But I think that find should be able to list the filename.

---

