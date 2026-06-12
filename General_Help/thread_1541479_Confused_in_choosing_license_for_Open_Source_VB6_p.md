---
title: "Confused in choosing license for Open Source VB6 project"
date: 2010-07-29
forum: General Help
---

### Post by Kushal S. Pandya on 2010-07-29
Hi everyone,

I'm developing an enterprise application in VB6 for Windows XP as a part of my college project. The application is not using any 3rd party APIs or controls and is entirely self-reliant. In the back-end, it will use either Oracle 10g database or Microsoft Access (2003 or 2007). I want to make this project completely open source, but I'm confused in choosing appropriate license for it. I planned for GNU GPL v3 but I read somewhere that if the application links to any closed source proprietary software than LGPL is preferred. I'm novice to open source licenses, please help me in expanding my project by suggesting better open source license. Thanks in advance..... :)

---

### Post by prodigy_ on 2010-07-29
Always choose GPL of course. Basically, [LGPL allows anyone to use your code to make money without opening the sources of their own code](http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License#Differences_from_the_GPL).

---

### Post by Kushal S. Pandya on 2010-07-29
Thanks, so it doesn't matter with the license even if I use closed source database as back-end to my project, I guess.

---

### Post by prodigy_ on 2010-07-29
As long as you don't redistribute Oracle or Access, no.

---

### Post by Kushal S. Pandya on 2010-07-29
Thanks a lot.... :-)

---

