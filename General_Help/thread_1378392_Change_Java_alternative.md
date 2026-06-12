---
title: "Change Java alternative"
date: 2010-01-11
forum: General Help
---

### Post by Yohai on 2010-01-11
Hi

I've been trying to change the java engine that my eclipse 3.5 uses by changing the java_home file in /etc/eclipse. It doesn't work at all. I still get 
"java.version=1.6.0_06" 
in my eclipse comfiguration data. The problem is that I'm trying to do profiling but it is TERRIBLY slow, and I think this might be the problem.

also, trying the  
```
sudo update-java-alternatives -s java-6-sun
```doesnt seems to change anything be cause I still get 
```

corson@alkashi:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

```[SIZE=4]Information:[/SIZE]
under usr/lib/jvm I have these folders:
```

corson@alkashi:/usr/lib/jvm$ ls
java-1.5.0-gcj-4.2-1.5.0.0  
java-6-sun  
java-6-sun-1.6.0.06
java-gcj

```but java-6-sun is only a link to java-6-sun-1.6.0.06

I'm using Hardy Heron, and I have two insances of eclipse on my computer.

suggestions? 

thanks,
Yohai

---

### Post by Mighty_Joe on 2010-01-11
> **Yohai said:**
> It doesn't work at all. I still get 
"java.version=1.6.0_06" 

That sounds like it is working correctly.  What do you expect?
Profiling is non-trivial.  Is your CPU hitting 100% and staying there?  Are you running out of RAM and swapping to disk?

---

### Post by .nedberg on 2010-01-11
```
update-java-alternatives -l
```to see options
```
update-java-alternatives -s <name>
```to set it

---

### Post by Yohai on 2010-01-12
Thanks all.

a) My CPU is indeed hitting 100%, and stays there. No swap is used. profiling even the silliest "Hello world" program takes half a minute....
b) Why do you say it's working? it says that the java version is 1.6. Is this the same as sun 6?
c) So if that is not the problem, where could be the problem with profiling? 

Thanks again.
Yohai

---

### Post by Mighty_Joe on 2010-01-13
> **Yohai said:**
> Thanks all.
a) My CPU is indeed hitting 100%, and stays there. No swap is used. profiling even the silliest "Hello world" program takes half a minute....


The JVM is enormous.  It's got to load a couple thousand classes before it can run your program and your profiler will be tracking all those instances.

> **Yohai said:**
> 
b) Why do you say it's working? it says that the java version is 1.6. Is this the same as sun 6?

Yes.  [See here]("http://en.wikipedia.org/wiki/Java_version_history")

> **Yohai said:**
> 
c) So if that is not the problem, where could be the problem with profiling? 


My wild guess is that you have a slow, single-core CPU.  Profiling is very intensive.  Since you say your computer isn't swapping, your memory should be fine.  What are your system stats?

---

