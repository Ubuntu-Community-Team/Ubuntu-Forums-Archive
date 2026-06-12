---
title: "undeletable file - file forever :-)"
date: 2011-03-28
forum: General Help
---

### Post by kapetr on 2011-03-28
How to reproduce the problem.

- user hugo creates file
- sudo chown root:hugo file
- sudo chattr +i file
-> no one can modify/delete the file (that's OK)
- sudo chattr -i file

-> ?! still no one can modify/delete the file ?!

If the same is done at not chowned file, than after clear of "i" chattr the file is accessable/deletable normally.

What is happened ?

--kapetr

---

### Post by mcduck on 2011-03-28
> **kapetr said:**
> How to reproduce the problem.

- user hugo creates file
- sudo chown root:hugo file
- sudo chattr +i file
-> no one can modify/delete the file (that's OK)
- sudo chattr -i file

-> ?! still no one can modify/delete the file ?!

If the same is done at not chowned file, than after clear of "i" chattr the file is accessable/deletable normally.

What is happened ?

--kapetr
what are that file's other permissions? Did you try deleting it as root/with sudo, or only as a normal user?

If you only tried deleting it as normal user "hugo" and the file doesn't actually have write permissions for group or others, it only makes sense you can't delete it. It belongs to root. ;)

---

### Post by sisco311 on 2011-03-28
> **mcduck said:**
> 
If you only tried deleting it as normal user "hugo" and the file doesn't actually have write permissions for group or others, it only makes sense you can't delete it. It belongs to root. ;)

That's a common misconception.

You can delete a file from a directory if you have write permission on the directory and execute permission on the directory, its parent directory and all ancestor directories up to and including "/".

If the sticky bit is also set on the directory, then only the owner of the file, the owner of the directory and of course root will be able to delete that file.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by kapetr on 2011-03-28
As I wrote **no one** then I had mean no one. Root inclusive.

On DIR is no sticky bit - and even if would - root (owner) can not delete the file too.

BTW - try it yourself - in your enviroment.
--kapetr

---

### Post by Spyderkid on 2011-03-28
go into the command line and type *_sudo su_* and press enter then you will become superuser (root). then cd to the folder which has your "un-deletable file" in and run...

```

rm FILENAME

```

BANG! and file file is gone :)



(post a reply if it works (or doesn't))

---

### Post by kapetr on 2011-03-28
I have try to reproduce this "bug" again. 
Without success.

(FYI: before sending of 1. of this post I have try it more times on different files)

But now ... (after some restarts ...)

I can delete this file now as user hugo (and root of course too).

My conclusion: it was probably temporary fault in file system/kernel/...

BTW - Do you thing, there is a difference between sudo x and sudo su -> x ?

--kapetr

---

### Post by WorMzy on 2011-03-28
> **kapetr said:**
> I have try to reproduce this "bug" again. 
Without success.

(FYI: before sending of 1. of this post I have try it more times on different files)

But now ... (after some restarts ...)

I can delete this file now as user hugo (and root of course too).

My conclusion: it was probably temporary fault in file system/kernel/...

BTW - Do you thing, there is a difference between sudo x and sudo su -> x ?

--kapetr

Yes. "sudo x" uses your current shell to execute x, which means that all the shell variables are custom-tailored for your user. "sudo -i" (or "sudo su") creates a new shell and populates it with root's variables.

For example, run the following as your user:
```
echo $USERNAME
```
$USERNAME is a shell variable which contains the name of the person who owns the shell, so it should output your username.

Now do the same, but use sudo
```
sudo echo $USERNAME
```
You should get the exact same output, even though you were running "echo" as root.

Now use sudo -i, and re-run the echo command.
```
sudo -i
echo $USERNAME
```
"root" should be output, since a new shell was created and is owned by root.

This generally doesn't make that much difference, but it's the reason why you should never run graphical applications with "sudo", and should use "gksu" or "gksudo" instead.


Another small difference is that "sudo -i" can use shell commands, like cd.

```
sudo cd /root
```
will tell you that the cd command wasn't found (because it's a shell command, not an executable)
```
sudo -i
cd /root
```

---

### Post by mcduck on 2011-03-28
> **kapetr said:**
> 

BTW - Do you thing, there is a difference between sudo x and sudo su -> x ?

--kapetr
Yes, but nothing that should make any difference here.

..although one difference is that the sudo one is fine to use, while you actually shouldn't use "sudo su" at all. The correct command to open a root session in shell is "sudo -i".

"sudo su" or "sudo -s" will not load root user's shell environment, and instead keeps on using your user's environment. Which can in some cases result in your user's files becoming overwritten with root's permissions and other inconvenient problems like that...

Here's a nice post about the differences between these commands: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

---

