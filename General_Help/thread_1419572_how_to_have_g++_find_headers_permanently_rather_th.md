---
title: "how to have g++ find headers permanently rather than using -I"
date: 2010-03-02
forum: General Help
---

### Post by cgb223 on 2010-03-02
Hi, I want to make g++ find a bunch of header files in a very specific folder, that is not in any path without having to type out the -I command over and over each time i use a new command. any idea to make it automatically look for the headers in that folder. 
(please don't respond "move them to another folder where it already looks")

much appreciated

---

### Post by lloyd_b on 2010-03-02
> **cgb223 said:**
> Hi, I want to make g++ find a bunch of header files in a very specific folder, that is not in any path without having to type out the -I command over and over each time i use a new command. any idea to make it automatically look for the headers in that folder. 
(please don't respond "move them to another folder where it already looks")

much appreciated
Use the CPLUS_INCLUDE_PATH environment variable.  If you add "export CPLUS_INCLUDE_PATH=/home/user/somedir" to your ~/.bashrc file, that directory will be added to the default search path for include files every time you run g++.

Lloyd B.

---

### Post by cgb223 on 2010-03-02
Awesome. Now how do I add that to bashrc?

---

### Post by HermanAB on 2010-03-02
```
$ gedit ~/.bashrc
```

---

