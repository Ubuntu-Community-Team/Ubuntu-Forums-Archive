---
title: "Interesting problem"
date: 2005-03-08
forum: General Help
---

### Post by Phosphoros on 2005-03-08
Ok, I feel a little dumb for this but it's all about learning right?  :grin: 

I'm trying to run Netflix Addict and it comes platform independant.  Written in Java, *supposedly* it just runs automatically but double clicking.  Well it doesn't for me.
So what do I do to get .jar files to run as a program?  Is there some magical arcane command-line I need to type?  hehe

Please throw me a line here.

Thanks

:)

---

### Post by Wombley on 2005-03-08
[QUOTE=Phosphoros]Ok, I feel a little dumb for this but it's all about learning right?  :grin: 

I'm trying to run Netflix Addict and it comes platform independant.  Written in Java, *supposedly* it just runs automatically but double clicking.  Well it doesn't for me.
So what do I do to get .jar files to run as a program?  Is there some magical arcane command-line I need to type?  hehe

Please throw me a line here.

Thanks

:)[/QUOTE]
 java -jar *filename* I think (presuming java's installed and in $PATH).

---

### Post by bored2k on 2005-03-08
[QUOTE=Wombley]java -jar *filename* I think (presuming java's installed and in $PATH).[/QUOTE]
 You would first need to install Java of course, if you apt-got one, the command from Wombley shoudl work.

Justin Case
## Java sources - Ubuntu Warty
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java

---

### Post by flaming_monkey on 2005-03-08
Here's the Unoffical guide to installing JRE (Java Runtime Environment).

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by bored2k on 2005-03-08
[QUOTE=flaming_monkey]Here's the Unoffical guide to installing JRE (Java Runtime Environment).

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)[/QUOTE]
 It's a bit easier to just apt-get install sun-j2re1.5debian than compile all that ... especially for newbies who would get **shocked** at command line terminal.

---

