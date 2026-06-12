---
title: "how is jedit in dapper?"
date: 2006-06-09
forum: General Help
---

### Post by morguns on 2006-06-09
Has anyone installed JEdit in Dapper using 'apt-get install'? Will Java need to be updated? "java --version" returns the following:
```

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
```

The jedit.org site gives the info to do it, but it's not specific to Ubuntu (let alone Dapper).
> 
To install jEdit via Debian Linux apt-get, add the following lines to your /etc/apt/sources.list:

deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./

Then, just run apt-get update, followed by apt-get install jedit or apt-get source jedit. 

---

### Post by timetunnel on 2006-06-09
JEdit works fine on my system (ubuntu 6.06). I had JEdit on my Breezy setup and just copied the files over to my new Dapper setup. But I haven't used the deb file. I used the jar file that can be downloaded from sourceforge and installed into /home/me/opt/jedit. Moreover, I've installed Sun's Java, which is available in the Dapper repositories. When you want to use Sun's Java as the default Java you must change that in your system's setup. I did that with "galternatives" (must be run with "sudo"), where you just choose the Java version and that's it.

---

### Post by timetunnel on 2006-06-09
oh, yes, forgot: and there's a shell script "jedit" which is used to run JEdit. You have to adjust a few paths there, IIRC

---

### Post by jimmygoon on 2006-06-09
Just add the entries and try it. I'm not sure if it works out of the box in Dapper (I know in Breezy it required some java arm-twisting and file editing) but at the very least you can update to sun-java1.5 (you should anyways) and then just apt-get install jedit. Works great for me, aside from the fact that it doesn't maximize properly using AIGLX... but thats the fault of unstable technology.

---

### Post by crumja on 2006-06-09
If you like jedit, give geany a try. It's light, fast, and wickedly powerful.

---

