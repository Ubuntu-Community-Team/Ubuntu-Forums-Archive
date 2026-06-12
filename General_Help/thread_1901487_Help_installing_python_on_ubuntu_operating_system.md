---
title: "Help installing python on ubuntu operating system"
date: 2011-12-28
forum: General Help
---

### Post by warriorboxerdog on 2011-12-28
Ok went to python and down loaded the newest version. For the life of me I cant figure out how to install it. I tried a how to video on you tube with no luck. The file is saved under downloads.  I am completely new to umbuntu so assume I know nothing and give me a step by step on how to install this and other programs downloaded from the web. Thanks for your help in advance

---

### Post by sohmc on 2011-12-28
Have you tried just installing python via apt-get:

```
sudo apt-get install python
```

If you're trying to install this from source, you'll have to compile it.  For new linux users, I wouldn't recommend it unless you have patience and willingness to learn by failing.  

I don't say this condescendingly.  Just took me several days to figure out how to build a package from scratch.  Heck, even now, I rarely build from source unless I really have to.

---

### Post by oldos2er on 2011-12-28
Python is already installed on Ubuntu because there are many apps dependent upon it. Attempting to upgrade python to a newer version may break these apps.

Which version of Ubuntu are you running?

Edit: I would also urge you *not* to download software from anywhere on the internet, but to use the repositories.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by tariquex on 2011-12-29
A word of caution, python 3.x is not backward compatible and ubuntu uses python 2.x. Applications are heavily dependent on python, so make sure you do not override the default system python. Install and run python 3.x in a sandbox environment.

---

### Post by d3v1150m471c on 2011-12-29
"python 3.x is not backward compatible". Because BC isn't really important to any serious developments. Well, either that or there's no such thing as a serious python developer.

---

### Post by sohmc on 2011-12-29
> **oldos2er said:**
> I would also urge you *not* to download software from anywhere on the internet, but to use the repositories.

I don't want to take this off-topic but why would you say this?  Software from the internet is what Linux essentially is.  All the repositories have is software from the internet, packaged especially for Ubuntu.

I would say not to download software from the internet unless you know what you are doing.

---

### Post by lukeiamyourfather on 2011-12-29
Don't install Python from source (the one you downloaded from the Python site) unless you have a good reason for doing so because it can botch up things that rely on Python. If you want to use Python 3 instead of Python 2 you can install it from the repositories.

```
sudo apt-get install python3
```

I think that's right, but I don't have Ubuntu in front of me to check. It will install it along side of Python 2. The command 'python' will use Python 2 which comes with Ubuntu and the command 'python3' will be Python 3.

---

### Post by oldos2er on 2011-12-29
> **sohmc said:**
> I don't want to take this off-topic but why would you say this?  Software from the internet is what Linux essentially is.  All the repositories have is software from the internet, packaged especially for Ubuntu.

I would say not to download software from the internet unless you know what you are doing.

Maybe I should've said don't download from random web sites instead of "from the internet". I geared my comment toward someone new to Linux.

---

### Post by sohmc on 2012-01-03
> **lukeiamyourfather said:**
> Don't install Python from source (the one you downloaded from the Python site) unless you have a good reason for doing so because it can botch up things that rely on Python.

This I agree with!  That's why you should know what you're doing before compiling it yourself.  I know I've had too many issues trying to run several different versions of a particular package, and I consider myself an expert.

> **oldos2er said:**
> Maybe I should've said don't download from random web sites instead of "from the internet". I geared my comment toward someone new to Linux.

I think this is much better.  I would recommend brand new "wet behind the ears" linux users use apt-get or yum or whatever brand your distro uses.

---

### Post by oldos2er on 2012-01-03
> **sohmc said:**
> I think this is much better.  I would recommend brand new "wet behind the ears" linux users use apt-get or yum or whatever brand your distro uses.

I believe that's what I said in post #3.  :)

---

