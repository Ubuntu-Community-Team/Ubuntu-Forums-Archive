---
title: "change default python"
date: 2009-09-30
forum: General Help
---

### Post by anonmars on 2009-09-30
Hello,

I am on a system that I don't have root or sudo so I can't change anything system-wide. 

The system has an older version of Python so I installed a newer version in my home directory:
~/myprogs/python-2.6/

However, whenever I type 'python' on the command line it is pointing at the old version.

I added ~/myprogs/python-2.6/bin to my PATH environment variable *before* everything else but typing 'python' still refers to the old version.

How do I fix this?

Thanks.

---

### Post by jkysam on 2009-09-30
I posted about this yesterday... Anyway here is the bottom line:

On my machine I have two versions of python:

```
~$ ls -l /usr/bin/ | grep python
-rwxr-xr-x  1 root   root       7835 2009-03-09 11:42 dh_python
lrwxrwxrwx  1 root   root         23 2009-06-28 12:34 pdb2.5 -> ../lib/python2.5/pdb.py
lrwxrwxrwx  1 root   root         23 2009-06-12 14:59 pdb2.6 -> ../lib/python2.6/pdb.py
lrwxrwxrwx  1 root   root          9 2009-06-12 14:59 python -> python2.6
-rwxr-xr-x  1 root   root    1177204 2009-04-04 15:13 python2.5
-rwxr-xr-x  1 root   root    2268568 2009-04-18 22:53 python2.6
lrwxrwxrwx  1 root   root         29 2009-06-12 14:59 pyversions -> ../share/python/pyversions.py

```

Note that python is linked to python2.6.
If I want to change the version that is associated with python I would simply remove the current python link:

```
rm /usr/bin/python
```


And add a new link:
```
ln -s /usr/bin/python2.5  /usr/bin/python
```

I'm not sure if you will be able to remove the python simlink without sudo...

---

### Post by Bachstelze on 2009-09-30
Or in one step: sudo ln -snf python2.5 python

---

### Post by anonmars on 2009-09-30
Thanks for the quick replies, but from my first sentence:  

"I am on a system that I don't have root or sudo so I can't change anything system-wide."

---

### Post by jkysam on 2009-09-30
> Or in one step: sudo ln -snf python2.5 python 	
Took note of that. Def a better way of doing it.

---

### Post by diesch on 2009-09-30
What do ```
echo $PATH 
``` and ```
which -a python
``` print?

---

### Post by diesch on 2009-09-30
@[jkysam]("http://ubuntuforums.org/member.php?u=920624"): Be careful with that, some program may expect /usr/bin/python to be 2.6 and may not work with 2.5.

---

### Post by anonmars on 2009-09-30
> **diesch said:**
> What do ```
echo $PATH 
```

/home/myuser/myprogs/python-2.6/bin:blahblah:/usr/bin:blahblah

 > **diesch said:**
> ```
which -a python
``` print?

/usr/bin/python

---

### Post by diesch on 2009-09-30
Which shell are you using? Some shells, like zsh, require you to  run "rehash" before they recognize new programs.

---

### Post by anonmars on 2009-09-30
> **diesch said:**
> Which shell are you using? Some shells, like zsh, require you to  run "rehash" before they recognize new programs.
csh

I think I fixed it, I used a more bash-like syntax for setting the path instead of:

set path = (/blah $path) 

Thanks!

---

