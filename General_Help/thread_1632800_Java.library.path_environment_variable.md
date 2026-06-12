---
title: "Java.library.path environment variable"
date: 2010-11-28
forum: General Help
---

### Post by Ivan_32 on 2010-11-28
I'm trying to install xuggler(java wrapper for ffmpeg), it needs LD_LIBRARY_PATH var, but as far as i know it is marked as deprecated since 9.10, and there's realy nothing to do with it. 
If i set needed libpath by setting it from my app by System.setProperty("java.library.path","/usr/local/xuggler/lib") - it works. 
So the question is how to manualy set this variable. 
Java -Djava.library.path="/usr/local/xuggler/lib" just dont work, it outputs list of commands and nothing changes. 

I read mans, googled, tryed many variants - nothing works. 
My OS are Ubuntu 10.10. 

[COLOR="White"]I probably need another dose of haloperidol...[/COLOR]

---

### Post by areeda on 2011-05-23
Anybody figure out how to do this?

What I've figured out so far:

[LIST]
[*]LD_LIBRARY_PATH works from my .profile but is deprecated from /etc/profile
[*]ld.so.config.d the replacement doesn't get passed to JVM
[*]you can't set java.library.path as an environment variable bash doesn't allow dots in the name
[/LIST]
I need to run the programs from the panel so my .profile doesn't solve the problem.

Any ideas?

---

