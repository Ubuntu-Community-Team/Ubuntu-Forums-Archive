---
title: "JRE Trouble"
date: 2012-01-12
forum: General Help
---

### Post by EpicWorld on 2012-01-12
I need that <snip> JRE to run some programs like StencylWorks. The problem is how <snip> do i install it? I googled lots of Java Oracle (SUN) and nothing worked. When i try to open it still says <<THIS PROGRAM REQUIRES JRE 1.5.0>> . Also the Firefox plugin somewhy doesn't work so i needed to reinstall IcedTea.

---

### Post by Double.J on 2012-01-12
Hi there, [This]("http://www.ubuntugeek.com/install-jre-on-ubuntu-11-10-oneiric.html") may help - see adding the repo at the bottom,

Hope it helps :)

---

### Post by EpicWorld on 2012-01-13
> **gnu/mirow said:**
> Hi there, [This]("http://www.ubuntugeek.com/install-jre-on-ubuntu-11-10-oneiric.html") may help - see adding the repo at the bottom,

Hope it helps :)

Unoftunatelly still can't run some programs, here is a screenshot if that helps. 
[http://img442.imageshack.us/img442/1999/comeon.png](http://img442.imageshack.us/img442/1999/comeon.png)

---

### Post by Double.J on 2012-01-13
Sorry I couldn't see from the pic - are you selecting run with wine?

---

### Post by EpicWorld on 2012-01-13
> **gnu/mirow said:**
> Sorry I couldn't see from the pic - are you selecting run with wine?

Yes :S I was running it on windows, so i decided not to reinstall it.

Edit: Also idk what is with the ubuntu version of this program. When I try to run it shows 
```
#!/bin/bash

java -Xms64m -Xmx512m -Djava.library.path=./lib -jar ./sw.jar
```

Edit2: Oh looks like i should make in an executable.

---

### Post by Double.J on 2012-01-13
Sorry I'm pretty confused what you're trying to do - are you trying to get wine to run the program installed on a windows system from ubuntu, run it on Wine on an ubuntu install, or run the linux version in ubuntu?

I'd recommend downloading the latest source from [here]("http://www.stencyl.com/stencylworks/get/") (sorry if it starts downloading the windows.exe - I can't find a link on their site that doesn't! anyway, delete that, just click on the "linux" link at the bottom, middle of the page - it should download a .tar.gz file - open this with the archive manager and read the readme and any other relevant text files it asks you to to work out how to install, it'll probably be something like this in the terminal, but read the readme's

```

./configure
make
make install

```

Hope it helps :)

---

### Post by EpicWorld on 2012-01-13
I reinstalled Oracle JRE and made it the default. Looks like it works now.

---

