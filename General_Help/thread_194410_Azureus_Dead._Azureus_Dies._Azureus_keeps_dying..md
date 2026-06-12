---
title: "Azureus Dead. Azureus Dies. Azureus keeps dying."
date: 2006-06-11
forum: General Help
---

### Post by AndEat on 2006-06-11
Azurues keeps dying, randomly it would seem. Sometimes it will stay up and get chugging on a torrent, and then hit some wall and die with no warning. Other times it will just die without getting really started.

Tried this 

[http://ubuntuforums.org/showthread.php?t=193660&highlight=azureus](http://ubuntuforums.org/showthread.php?t=193660&highlight=azureus)

and seemed to work, cured the unmovable popups problem.

But I keep having to restart every 5-20 minutes.

I've just started looking into tracing what is happening......some memory collapse? gremlins? some sort of kill signal by my isp I can't block out?

Any suggestions, anyone else having a similar hard time?:confused:

---

### Post by Evoreth on 2006-06-11
Are you using Sun Java? [https://wiki.ubuntu.com/Java?highlight=%28Java%29](https://wiki.ubuntu.com/Java?highlight=%28Java%29)
Don't forget to select the right version.

---

### Post by Mr Green on 2006-06-13
If you are running with Sun's Java you should also search the Azureus wiki for "Azureus dies". They have a suggested solution for your problem.

Basically they say limit the number of simultanious connections I think!

---

### Post by AndEat on 2006-06-13
Actually, I ended up reinstalling Azureus; no problems now. i have no idea what corrupted that install. Beyond my diagnostic ability, though I tried.....

---

### Post by stanna on 2006-06-24
im still having the random crashing. i would wake up in the morning and azureus wouldnt be running. i see nothing in the log files which could indicate whats happenning. so im at a loss. im running the latest beta from the azureus website, as i was having problems with those little error messages popping up and not being able to close them, the beta version solved that, and now the random crashing persists. ill try limiting the max connections and see how that goes.

if anyone has any other suggestions id like to hear them :)

---

### Post by joshrobinson on 2006-06-24
[QUOTE=stanna]im still having the random crashing. i would wake up in the morning and azureus wouldnt be running. i see nothing in the log files which could indicate whats happenning. so im at a loss. im running the latest beta from the azureus website, as i was having problems with those little error messages popping up and not being able to close them, the beta version solved that, and now the random crashing persists. ill try limiting the max connections and see how that goes.

if anyone has any other suggestions id like to hear them :)[/QUOTE]

i noticed that with sun java 1.4.2 it would crash and not start up again.. with java 1.5.0 it never crashes, maybe thats something to look into

---

### Post by incubus on 2006-06-24
I had that when I used blackdown's java too.

If you go to azureus' website, it has a big link to Java 1.5.0 in the download section, so I guess it's like a requirement.

Never had any problem with Sun's Java. 

incubus

---

### Post by FredB on 2006-06-25
Java 1.5.0 from Sun is installable after activating multiverse repository in synaptic. Simplest way to add it. After, you have to select which version you want to use, but I don't remember how to do this :(

---

### Post by incubus on 2006-06-25
Good point. 
I'd go for:
```

$ sudo apt-get install sun-java5-jre

```

You may need to:
```

$ sudo update-alternatives --config java

```

incubus

---

### Post by stanna on 2006-06-25
thanks for the update guys, im installing sun java right now, so ill leave things running and i should know in 12 hours or soo when i get home if azureus has survived and remained running.

thanks again! ill post when im home to check things.

---

### Post by stanna on 2006-06-28
im happy to report that installing the proper sun java stuff has made all the difference. azureus now functions just like it should. sucking up all my system resources and running slow as anything. but it works! and it works well!!

so thanks to everyone who suggested fixes. :)

---

### Post by lajja on 2007-05-12
:(  Nothing works for me. I've reinstallad Azureus about 10 times and the same with java. I've tried all possible combinations of "sun-java5-xxxx" packages and "sun-java6-xxxx" packages.

What can I do?

---

