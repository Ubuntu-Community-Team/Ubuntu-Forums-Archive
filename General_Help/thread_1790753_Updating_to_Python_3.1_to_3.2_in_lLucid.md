---
title: "Updating to Python 3.1 to 3.2 in lLucid"
date: 2011-06-25
forum: General Help
---

### Post by Spiritof76 on 2011-06-25
I have 2 netbooks, one desk top and a server on my home network. I would like to have all my machines running the same version of Python. The Lucid machine repositories seem stuck at 2.6x and 3.1x ... I want them to be 2.7x and 3.2  so that I am consistant. 

Is there a way to upgrade the repositories for Python without having to upgrade the whole system? 

I sure would appreciate any help with this.

---

### Post by Spiritof76 on 2011-06-26
Didn't get much responce. I finally did find some help on [another forum]("http://www.dbaportal.eu/?q=node/196").

In the terminal I typed in these instructions:
```


$ mkdir python
$ cd python
$ mkdir python32
$ mkdir python27
$ cd python32
$ wget http://www.python.org/ftp/python/3.2/Python-3.2.tgz
$ tar xvzf Python-3.2.tgz
$ cd Python-3.2
$ ./configure --prefix=/opt/python3.2
$ make
$ sudo make install
$ sudo ln -s /opt/python3.2/bin/python3.2 /usr/bin/python32
$ sudo ln -s /opt/python3.2/bin/idle3.2 /usr/bin/idle-python3.2

$ cd ~/python27
$ wget http://www.python.org/ftp/python/2.7/Python-2.7.tgz
$ tar xvzf Python-2.7.tgz
$ cd ython-3.2
$ ./configure --prefix=/opt/python2.7
$ make
$ sudo make install
$ sudo ln -s /opt/python2.7/bin/python2.7 /usr/bin/python2.7
$ sudo ln -s /opt/python2.7/bin/idle /usr/bin/idle2.7


```

Set up the menus from system | preferences ! main menu
This is the first time I ever installed from sourced code. It seems as though I should have been able to do this from a repository, but I couldn't find out how.

---

### Post by oldfred on 2011-06-26
In my usr/bin my python link is the python2.6. I would not change that as many system files depend on the version installed. 

But I also have a python3 link to python3.1. I think you could change that to pyrthon3.2 and not create huge issues. Then you use python3 in all your programs and it will link to the newest version installed.

---

### Post by Spiritof76 on 2011-06-26
the links used here did not change the default behavior. 
```

$ python
$ python3

```

Still works the way they always did, and call up python 2.6 and 3.1
 respectively.
to use the newer versions one would call python32 or python27

---

