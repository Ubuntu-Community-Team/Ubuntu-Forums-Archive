---
title: "Hard Link vs Symbolic Link"
date: 2011-08-10
forum: General Help
---

### Post by &#1084;&#1086;&#1081;ste&#1103; on 2011-08-10
Hey,

I was wondering anyone can explain to me the difference between a hard-link and symbolic link. I am going over TLCL-09.12.pdf (The linux command Line) and am having trouble understanding that when I delete a file that I have created a hard-link and symbolic link to, I get an error message saying no such file exists when using the "less" command on the symbolic link, yet the hard-link will open the file.

example:
sudo mkdir playground
cd playground
sudo mkdir dir1 dir2
sudo cp /etc/passwd .
sudo ln passwd fun1
sudo ln -s /home/user/playground/passwd dir1/fun2
sudo rm passwd
less fun1 (file opens)
less /home/user/playground/dir1/fun2 (no such file exists)

---

### Post by robgraves on 2011-08-10
[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)

---

### Post by Bachstelze on 2011-08-10
A hard link lets you create another name for the same file. Both are equivalent, this is why when you delete any one of the two "names", you can still access the file from the other one.

A symbolic link is like a "forwarding address". When you try to access a symlink link (in this case, dir1/fun2), the OS basically says "the file you are looking for is /home/user/playground/passwd", and then whatever program is trying to access the file will try to access /home/user/playground/passwd instead. If that file does not exist, the access will fail (you say that the link is "broken").

---

### Post by &#1084;&#1086;&#1081;ste&#1103; on 2011-08-10
Ok,

So when i copy a file from one directory to another is linux creating a hard-link to the same inode of the original file?

---

### Post by haresear on 2011-08-10
> **&#1084 said:**
> Ok,

So when i copy a file from one directory to another is linux creating a hard-link to the same inode of the original file?

Not normally. Copy (cp) will create a new file with the same contents (unless you use the -l option). See "man cp".

---

### Post by &#1084;&#1086;&#1081;ste&#1103; on 2011-08-10
Alright, Thanks guys.

Did not mean to ask stupid questions, just trying to figure things out.

---

