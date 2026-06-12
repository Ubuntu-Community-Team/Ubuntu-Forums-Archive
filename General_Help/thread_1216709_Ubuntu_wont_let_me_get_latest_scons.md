---
title: "Ubuntu wont let me get latest scons"
date: 2009-07-18
forum: General Help
---

### Post by BUTTS on 2009-07-18
I am trying to compile yafaray and blender on my Ubuntu 8.04 intel 64bit pc - without success! Cutting a long story short and after reading the Yafaray forums, I suspect that I require a version of Scons higher then 0.97, which is the highest the synaptic package manager will allow on my system. Scons 1.2 is available as tar.gz, but of course I need the package manager to put things where they are supposed to be. In short, how do I install Scons 1.2 on my OS and everything goes where it needs to be. I have read that I may need a deb version of Scons 1.2. Is this true? I am still pretty new to Ubuntu so please forgive my lack of knowledge and I hope I have posted in the correct part of the Forum. 
Many Thanks.

---

### Post by munky99999 on 2009-07-18
Well my suggestion would be to upgrade to Jaunty. The jaunty repo has 1.2.

OR

```
deb http://cz.archive.ubuntu.com/ubuntu jaunty main 

```

Add that as a "third party software source" in the repo - software sources.

Then it should be available.

---

### Post by BUTTS on 2009-07-18
Thanks,
       Yes, did what you said and scons-1.2 did install - at least! Now different errors occur on compiling. Think I will upgrade to Jaunty though eventually and give it a go.

---

