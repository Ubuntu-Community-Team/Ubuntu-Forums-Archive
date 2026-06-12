---
title: "Ubuntu won't run jar file"
date: 2012-04-16
forum: General Help
---

### Post by Th3Blaze on 2012-04-16
I've got openjdk 6 installed but when I run a specific jar file, other jar files actually work, in terminal or by right clicking and selecting run with openjdk 6, it won't run and when ran in terminal comes up with this exception

```
mary@Mercury:~/M-Server$ java -jar Mineshafter-proxy.jar
Exception in thread "main" java.lang.NoSuchMethodError: method java.net.URL.openConnection with signature (Ljava.net.Proxy;)Ljava.net.URLConnection; was not found.
   at mineshafter.util.SimpleRequest.get(SimpleRequest.java:21)
   at mineshafter.util.SimpleRequest.get(SimpleRequest.java:14)
   at mineshafter.MineClient.main(MineClient.java:44)

```

If this is in the wrong place please tell me, and where to put it. Thank you, help is VERY appreciated

---

### Post by Th3Blaze on 2012-04-16
It's been 3 hours now so ^bump^

---

### Post by alex2e1gzy on 2012-04-16
Have you had a look at the following line of code?

> SimpleRequest.java:21

I would suggest this is a problem with the code or that you are missing some class file.

---

### Post by Th3Blaze on 2012-04-16
Yes, it HAS to be an error with the Mineshafter-proxy.jar file I am trying to run, but it has worked before(normally and from terminal), so I am confused.

Also when I type in java, instead of giving me the list of options I can do with java, it gives me the option to install java, which is already install, when I try (re)installing java, it tells me that it is already installed. very confused!!!

---

### Post by Th3Blaze on 2012-04-16
Been an hour-^bump^

---

### Post by albandy on 2012-04-16
Are you using the openJDK JVM or the Sun (Oracle) one?

type java -version

---

### Post by hrickh on 2012-04-16
> **Th3Blaze said:**
> Been an hour-^bump^
Stop that. It's annoying to read and pretty much guarantees you're not going to get help from people.

R.
==

---

### Post by Th3Blaze on 2012-04-16
> **hrickh said:**
> Stop that. It's annoying to read and pretty much guarantees you're not going to get help from people.

R.
==

It's better than nothing, no one might reply either way, and OpenJDK, is Sun (Oracle ) better ?

---

### Post by albandy on 2012-04-16
> **Th3Blaze said:**
> It's better than nothing, no one might reply either way, and OpenJDK, is Sun (Oracle ) better ?

It depends on the jvm version. In java 6 sun jvm works  better but in Java 7 both run well.
But this is for testing purposes I only want you to try with a diferent JVM.

---

### Post by Th3Blaze on 2012-04-17
What should i download then ?

---

### Post by albandy on 2012-04-17
I tested it with jre 1.6.30 from Oracle and works.

---

### Post by Th3Blaze on 2012-04-17
Will that be on synaptic, can you give me a specific link, and I think they're may be an error with the .jar file or hopefully, im just missing some extra java packages or maybe ive got the wrong ones, you need lwjgl, and a few other because it is a java game, so does anyone have a clue where i go from here ?

And im using jre 1.6.31 one version up from yours, ive installed it anyway, but

```
mary@Mercury:~$ java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

```

---

### Post by albandy on 2012-04-18
You have to download it from oracle website.  It was removed from repos because Oracle don't allow to redistribute it.

---

### Post by Th3Blaze on 2012-04-19
Can you send me a specific link, so I get the right version/file

---

### Post by flurospar on 2012-04-19
Did they offer a .jad along with the jar? If so, get the .jad and run the .jad .

---

### Post by albandy on 2012-04-19
> **Th3Blaze said:**
> Can you send me a specific link, so I get the right version/file

[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

If your system is 64 bit download "Linux x64"
else download "Linux (self-extracting file)"

---

### Post by Th3Blaze on 2012-04-19
no they didn't sorry. the website with downloads is [http://mineshafter.appspot.com/downloads](http://mineshafter.appspot.com/downloads)

---

### Post by Th3Blaze on 2012-04-19
> **albandy said:**
> [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

If your system is 64 bit download "Linux x64"
else download "Linux (self-extracting file)"

Thanks Albandy, I'll update you when I've ran it.

---

### Post by Th3Blaze on 2012-04-19
I've installed it but nothing's working still, still the same exception coming up, Ive removed and rebooted my stuff about a billion times

---

### Post by thomas sigurdsen on 2012-04-19
what does 'java -version' give you now?

---

### Post by albandy on 2012-04-20
> **Th3Blaze said:**
> I've installed it but nothing's working still, still the same exception coming up, Ive removed and rebooted my stuff about a billion times

Did you ran the downloaded file?

command:
sh jre-6u31-linux-(i586 or x64).bin

---

### Post by Th3Blaze on 2012-04-20
```
mary@Mercury:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.6.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by Th3Blaze on 2012-04-21
> **albandy said:**
> Did you ran the downloaded file?

command:
sh jre-6u31-linux-(i586 or x64).bin

I've re-re-re-re-redone it, and nope, still an exception, and it HAS to be something wrong with the file, because other jars work ?

I have a similar one called MinecraftSP.jar , which launches a similar launch screen, and the same game obviously.

And as well , I did it ./jre-6u31-linux-i586.bin , not sh, but now ive done both, same result either way

---

### Post by Th3Blaze on 2012-04-21
Hmm, not sure where this error came from; but anyway

```
mary@Mercury:~/Downloads$ java -version
java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

```

---

### Post by Th3Blaze on 2012-05-08
^bump^ , any help yet ? Anything I can run in terminal to inform you a bit more ?

---

### Post by Th3Blaze on 2012-05-09
^bump^ Please, I really need help on the matter, I have decided I am going to uninstall ALL java, update it to Ubuntu 12.04 Precise Pangolin. Then install java from Oracle/Sun

---

