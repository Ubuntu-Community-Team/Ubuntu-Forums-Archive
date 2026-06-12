---
title: "How does &quot;installion of program by adding ppa&quot; work?"
date: 2012-03-26
forum: General Help
---

### Post by arroy_0209 on 2012-03-26
First of all I need to understand how addition of ppa work. Suppose there is a program (xyz) available from ubuntu using the command:
```
sudo apt-get install xyz
```It is known that the latest version can be got by adding the ppa this way:
```

sudo add-apt-repository ppa:name-of-owner/ppa
sudo apt-get update
sudo apt-get install xyz

```The command format above is as given in the download instruction. I am confused if in this case I am getting the program from ubuntu or from the creator of the program. In fact the program can be directly downloaded from creator; so what is the difference? Also which method is better from security point of view? It is said that programs downloaded from ubuntu repo are safe.

Second, please check if the ocmmand sequence for installation through ppa as given is correct or not.

---

### Post by jerome1232 on 2012-03-26
Your getting the package from whoever owns that ppa, from a security standpoint you are explicitly trusting them (the owner of the xyz ppa) to not hand you malicious packages.

Ubuntu is in no way responsible for what you install via ppa (personal package archive)

---

### Post by 3rdalbum on 2012-03-26
You are getting the program from the PPA creator. The difference between this and getting the program straight from the developer is:

1. It may be more difficult to install from the developer - they might only have the source code available that you have to compile. Whereas everything in a PPA is precompiled, in Ubuntu's native package format, ready to run.

2. You can get updates as they arrive in the PPA.

If you trust the PPA creator then PPAs are as secure as the regular Ubuntu repositories. If the person running the PPA is malicious they could add malware to their packages. Your choice.

And yes your commands seem correct.

---

