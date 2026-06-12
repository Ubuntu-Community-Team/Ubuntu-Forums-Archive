---
title: "How find recursive symbolic link? (dpkg: Too many symbolic links)"
date: 2009-09-03
forum: General Help
---

### Post by poffis on 2009-09-03
I were playing around with symbolic links a week ago, and I seem to have screwed up my system. Now when I try to do an installation with apt-get/dpkg i get the following error:

```
kent@kent-hp-laptop:~$ sudo dpkg --unpack /var/cache/apt/archives/python2.6-dev_2.6.2-0ubuntu1_i386.deb 
dpkg (subprocess): failed to exec rm for cleanup: Too many levels of symbolic links
dpkg: error processing /var/cache/apt/archives/python2.6-dev_2.6.2-0ubuntu1_i386.deb (--unpack):
 subprocess rm cleanup returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-dev_2.6.2-0ubuntu1_i386.deb
```My guess is that I have a symbolic link pointing back at itself. How do I find out exactly where that evildoing symbolic link is, so I can remove it?

---

### Post by mrollings on 2009-09-03
I just did a little test for you. 

```

# Create a symbolic link to 'file' named 'link'
ln -s file link

# Create a non-empty file named 'file'
echo padding > file

# Check the file sizes with ls -s
# should show the file and the link
ls -s *

# remove the file and replace it with a symlink back to the orignal link
rm file
ln -s link file

# Now try to check the file size again
ls -s *

# You will now get the error you are talking about ie:
ls: cannot access file: Too many levels of symbolic links


```

So you can simply use "ls -s" to find the files that have recursive symlinks. So you should try and find the files which you have managed to mess up (can't help you with where you should be looking). But you could check your .bash_history file in your home directory to see what links you previously created.

```
cat ~/.bash_history | grep "ln -s"
```
Should do it.

Hopefully this will help you at least part way!

---

### Post by poffis on 2009-09-03
Thank you! Never occurred to me to look in .bash_history. When I did, I found out that I had managed to create a symbolic link named 'rm' in my /usr/bin which dpkg tried to execute. Almost a whole day spent on this, but a few lessons learned. So I mark it off as a good day anyway.

---

