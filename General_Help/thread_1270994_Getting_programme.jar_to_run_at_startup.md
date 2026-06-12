---
title: "Getting programme.jar to run at startup"
date: 2009-09-20
forum: General Help
---

### Post by grackleman on 2009-09-20
I need to have a java programme (call it programme.jar) run at startup. Putting the .jar file on the start menu works in 8.10 but not in 8.04. I've tried everything I can think of, changing the start menu command to 'java -jar programme.jar', making a link and putting that on the start menu, putting a launcher on the start menu. Nothing works.
I've tried having it save the session with the programme running and it just doesn't work.
Running 'java -jar programme.jar' from the terminal works.

How do I get a jar file to run at startup?
Thanks

---

### Post by Joshua Lückers on 2009-09-20
Try adding java -jar /full/path/to/programme.jar
Replace /full/path/to with the path where you program can be found.

---

### Post by grackleman on 2009-09-20
THANKS JOSHUA!!!!!!!!!!!!!
It worked.

---

