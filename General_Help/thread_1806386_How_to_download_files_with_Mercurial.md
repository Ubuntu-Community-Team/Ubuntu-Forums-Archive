---
title: "How to download files with Mercurial"
date: 2011-07-17
forum: General Help
---

### Post by Karlas on 2011-07-17
Hello,so I want to download Barrelfish OS [http://www.barrelfish.org/#release](http://www.barrelfish.org/#release).
Now it says:The latest release of Barrelfish can now be obtained by anonymous [Mercurial]("http://mercurial.selenic.com/") access from  [http://hg.barrelfish.org/](http://hg.barrelfish.org/).

SOOO can anybody tell me how to do it?
Thanks

---

### Post by ron999 on 2011-07-17
> **Karlas said:**
> 
SOOO can anybody tell me how to do it?


Hi
Use this command:-
```
hg clone http://hg.barrelfish.org/
```

That will download the sourcecode.
Then look in the hg.barrelfish folder for the README file, it explains how to go about compiling it.

---

### Post by Karlas on 2011-07-18
k@S3210:~$ hg clone [http://hg.barrelfish.org/](http://hg.barrelfish.org/)
destination directory: hg.barrelfish.org
abort: destination 'hg.barrelfish.org' is not empty

---

### Post by Karlas on 2011-07-18
Ok I downloaded it now how to build it,I dont understand this part:
2. Run hake.sh, giving it the path to the source directory and target architecture(s):
$ ../hake/hake.sh .. x86_64
This will configure the build directory and use GHC to compile and then run
hake, a tool used to generate the Makefile.

---

### Post by dino99 on 2011-07-18
[http://www.overclock.net/operating-systems/1021338-barrelfish-os.html#post13575428](http://www.overclock.net/operating-systems/1021338-barrelfish-os.html#post13575428)

---

### Post by Karlas on 2011-07-18
lol solved that but now I dont know this for sure!:
home/k/build/tools/fugu/Parser.hs:25:7:
    Could not find module `Text.ParserCombinators.Parsec.Language':
      Use -v to see a list of the files searched for.
make: *** [tools/bin/fugu] Error 1

---

### Post by HiImTye on 2011-07-18
Barrelfish is an experimental operating system without a graphical front end (meaning it is just a command line interface). it is a project by microsoft research and a swiss computing company to experiment with how to implement an OS using many cores on a CPU (which seem to be increasing steadily). if you can't compile it, odds are it isn't going to be much use to you

---

### Post by Karlas on 2011-07-18
oK guys Thank for all the answers!I guess Ill try it some time .future

---

