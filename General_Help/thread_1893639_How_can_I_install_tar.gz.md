---
title: "How can I install tar.gz"
date: 2011-12-10
forum: General Help
---

### Post by kifcaliph on 2011-12-10
Hello there

I'd like to know how can I install premake. I downloaded a file from its website and it's a tar.gz extension. I did the following command 
**tar zxf file.tar.gz**
and I found the bin premake4 and nothing else.

---

### Post by spiky001 on 2011-12-10
What s it you downloaded? It might be int the software centre which would make it easier to install

---

### Post by lechien73 on 2011-12-10
If it's premake you were looking to install, then:

```
sudo apt-get install premake
```

does the trick :) otherwise, as spiky said, we'd need to know what you were trying to install!

---

### Post by kifcaliph on 2011-12-10
no, it's not in the download center. I downloaded premake tool from [there]("http://industriousone.com/premake"). it's a tool like cmake and Qmake. after I extracted the premake-4.3-linux.tar.gz file I found premake4 and I got no idea what to do next.

---

### Post by Mr. Shannon on 2011-12-10
Unless you absolutioly have to have a newer version than what is avialible in the repository then use the command below in a terminal to install premake instead of installing from the tar.gz file.

```
sudo apt-get install premake
```

---

### Post by kifcaliph on 2011-12-10
the following code don't work because it's not listed in the software center
```
sudo apt-get install premake
```

and the result is 
```
sudo apt-get install premake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package premake**
```

---

### Post by spiky001 on 2011-12-10
In the premake folder there should be an install or README

---

### Post by lechien73 on 2011-12-10
What version of Ubuntu are you running?

Alternatively, you could do the following:

1. Extract the premake4 executable file from the archive to your home folder

2. Open a terminal window and type:
```
cp ./premake4 ~/bin/premake
```

3. Now try running:

```
premake --version
```

to confirm it is installed.

---

### Post by kifcaliph on 2011-12-10
thanks lechien73 it's working. I am running Ubuntu 10.04 the Lucid Lynx by the way.

---

### Post by lechien73 on 2011-12-10
You're welcome...glad it helped :)

---

### Post by Mr. Shannon on 2011-12-10
> **kifcaliph said:**
> I am running Ubuntu 10.04 the Lucid Lynx by the way.

That's why its not in your repository.  premake is in the repository of 11.04.

---

