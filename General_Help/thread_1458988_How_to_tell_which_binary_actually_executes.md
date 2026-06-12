---
title: "How to tell which binary actually executes?"
date: 2010-04-20
forum: General Help
---

### Post by stair314 on 2010-04-20
Is there a command that can tell me which binary actually executes for some program name? "whereis" seems to do something different. 

Specifically, I am trying to hunt down and kill a python 2.6 installation that just won't die.

ia3n@kaylee:~% python -V
Python 2.6.5
ia3n@kaylee:~% whereis python
python: /usr/bin/python /usr/bin/python2.5 /usr/bin/python2.4 /usr/bin/python2.5-config /usr/lib/python2.5 /usr/lib/python2.4 /usr/lib/python2.2 /usr/local/bin/python /usr/include/python2.4 /usr/share/man/man1/python.1.gz

whereis just seems to be returning anything with "python" in its name, but I want to know which binary thinks it is python 2.6.5. (By the way, I've tried all the above manually, and it isn't any of them)

---

### Post by spillin_dylan on 2010-04-20
I think you may need this...?

```
which python
```

---

### Post by tgalati4 on 2010-04-20
I didn't think Hardy came with Python 2.6.5.  Jaunty is currently using 2.6.2.  So yes, installing a newer version of python than what your distro was built with can cause problems.  I just checked my Hardy server and it has Python 2.5.2 installed.

So, I would say breakage is in order.

And you get to keep both pieces.

---

### Post by Yellow Pasque on 2010-04-20
/usr/bin/python or /usr/local/bin/python get my vote, most likely the latter.
```
file /usr/local/bin/python
```

---

### Post by dcstar on 2010-04-21
> **stair314 said:**
> Is there a command that can tell me which binary actually executes for some program name? "whereis" seems to do something different. 

Specifically, I am trying to hunt down and kill a python 2.6 installation that just won't die.

ia3n@kaylee:~% python -V
Python 2.6.5
ia3n@kaylee:~% whereis python
python: /usr/bin/python /usr/bin/python2.5 /usr/bin/python2.4 /usr/bin/python2.5-config /usr/lib/python2.5 /usr/lib/python2.4 /usr/lib/python2.2 /usr/local/bin/python /usr/include/python2.4 /usr/share/man/man1/python.1.gz

whereis just seems to be returning anything with "python" in its name, but I want to know which binary thinks it is python 2.6.5. (By the way, I've tried all the above manually, and it isn't any of them)
This will show you what path order is searched to find any executable file, the first one found will be run:
```
echo $PATH
```
Chances are /usr/bin/python is a link to one of the other files listed.

---

### Post by srs5694 on 2010-04-21
There's merit to all the responses in this thread, but spillin_dylan's suggestion of "which" most directly answers the question. Type "man which" for details about what it does.

---

### Post by tgalati4 on 2010-04-21
which which

---

