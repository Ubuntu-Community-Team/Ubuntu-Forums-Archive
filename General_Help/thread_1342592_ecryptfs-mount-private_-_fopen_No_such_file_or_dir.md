---
title: "ecryptfs-mount-private - fopen: No such file or directory"
date: 2009-11-30
forum: General Help
---

### Post by harry71194 on 2009-11-30
Hi, my server is acting weird. My home directory is empty, and only with README.txt. I follow it, I get an error.

> h@harryy:~$ ls
README.txt <thought to self, "oh crap">

h@harryy:~$ cat README.txt 
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

h@harryy:~$ sudo ecryptfs-mount-private
Enter your login passphrase:<typed it in>
Inserted auth tok with sig [**edited out, in case it's private**] into the user session keyring
fopen: No such file or directory

h@harryy:~$ ls
README.txt


Where are my files?! :| I need my /home directory back! :(

---

### Post by fluffman86 on 2009-11-30
Don't sudo.  You don't want to open root's home (which isn't encrypted), you want your own.

---

### Post by harry71194 on 2009-11-30
Not using sudo, it just ENDS.

h@harryy:~$ ecryptfs-mount-private
h@harryy:~$ ls
README.txt


Also, my files are still there and I suppose unlocked, as I can access the files that are stored in my home directory, symlinked to /var/www, off HTTP..

---

### Post by fluffman86 on 2009-11-30
cd /
ecryptfs-mount-private
cd ~

You have to leave your ~/ and come back

---

### Post by harry71194 on 2009-11-30
Awesome, worked, thanks.

---

### Post by new_tolinux on 2009-12-22
> **harry71194 said:**
> Hi, my server is acting weird. My home directory is empty, and only with README.txt. I follow it, I get an error.

Same problem here. I already figured out how to re-mount it, but I now have a problem.
Since about a week it also dismounts while sabnzbdplus is running, with sabnzbd ofcourse producing errors about not being able to write.

How do I prevent this? Never had this problem before.

Edit:
It seems that keeping a terminal open in the ~ folder solves the problem. Although any more permanent suggestions are very welcome.

---

### Post by jackgrump on 2010-01-06
Hey - newbie question, although this thread is listed as solved:

Following these instructions (and any others I can find), absolutely nothing happens with the command ecryptfs-mount-private, whether in my home folder, the .Private folder, after cd /, or in any other location. How the heck do you use this command?

---

