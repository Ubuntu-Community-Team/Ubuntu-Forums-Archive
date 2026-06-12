---
title: "Vim 7.3 on ubuntu with python"
date: 2010-11-11
forum: General Help
---

### Post by NateSoares on 2010-11-11
I know that this isn't really an Ubuntu question, but I'm wondering if anybody can help. I'm trying to compile Vim 7.3 with python support. Initially, I had trouble specifying the config file because Vim couldn't seem to handle python2.7 config files. I installed python2.4 and told vim to use that instead, and now vim configures and makes correctly, and still doesn't have python support. I'd really appreciate any help I could get.

Here's the command I'm using to compile:


make clean && ./configure --with-features=huge --enable-pythoninterp && make && sudo make install


Which has the output found here:

[http://pastebin.com/dfWNPVpW](http://pastebin.com/dfWNPVpW)

But running vim and "echo has('python')" says that vim still doesn't have python. I must be doing something stupid. Can somebody help?

---

### Post by WorMzy on 2010-11-11
First off, don't bundle the commands into one line like that. Run them one after another so that you can check the output before proceeding to the next stage.

--enable-pythoninterp requires an argument. Either use
```
--enable-pythoninterp=no
```
or
```
--enable-pythoninterp=yes
```
or
```
--enable-pythoninterp=dynamic
```

Reading the Vim documentation tells me that dynamic is for Windows users only, and you obviously don't want to use no (which is the default btw), so try configuring with yes and pay attention to the output. You should see something like:

```
checking --enable-pythoninterp argument... yes
checking for python... /usr/bin/python
checking Python version...
```

But that's all I can tell you, since I use Arch Linux, and "python" is now "python3", annoyingly, so I get a syntax error after that point. Hopefully you'll have better luck, or at least some intelligible output explaining what went wrong.

---

### Post by ametaireau on 2010-12-18
Hey there, I've been through the same problem.

The configuration file needed was in the "python-dev" package. Installing it and running again make && make install solved the problem for me.

---

