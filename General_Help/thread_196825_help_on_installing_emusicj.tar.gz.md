---
title: "help on installing emusicj.tar.gz"
date: 2006-06-14
forum: General Help
---

### Post by linuxguiri on 2006-06-14
Trying to install and run emusicj player (opensource player for emusic.com).

I downloaded emusicj-linux-i686-0.18.tar.gz from [http://www.kallisti.net.nz/EMusicJ/Download](http://www.kallisti.net.nz/EMusicJ/Download) and extracted it to /opt/emusicj-linux

But when I run emusicj, nothing happens. When I run it in a terminal I get: Exception in thread "main"

I already have Sun Java JRE 5.0 installed.

Ideas?

---

### Post by taurus on 2006-06-14
See what version of java your system thinks you have.  Open a terminal (Applications -> Accessories -> Terminal) and type
```

java -version

```
You need at least java version 1.5...

---

### Post by linuxguiri on 2006-06-15
thanks taurus!

"java -version" said: 
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

i guess even though i had installed the sun-java5-bin package installed, ubuntu continued to use gcj.

in case others come across this thread looking for the same answer, i found: [https://wiki.ubuntu.com/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://wiki.ubuntu.com/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b) to be very helpful.

now "java -version" says:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

emusicj works now. i bet some other java apps might work a little differently too.

thanks again.

---

