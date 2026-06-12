---
title: "Advanced STDIN redirection"
date: 2010-10-04
forum: General Help
---

### Post by cipherboy_loc on 2010-10-04
Sorry if I posted this in the wrong forum, but I did not think any of the sub-forums in the Development & Programming forum really fit what I needed. Feel free to move it if I posted it in the wrong place.

I have been using Ubuntu a lot, switching between GNOME and Fluxbox, setting up servers, etc, but I mainly use it for programming. I am working on a large console-based Dungeons and Dragons game (which is far from complete) and when ever I need to test it I have to go through the process of creating a new user and going where I want to go. This gets a bit tiring after the 4th or 5th test in the hour (I change little, but test a lot). I know how to redirect output and input to files, but is there a way to redirect a file to STDIN and once the program has done all the instructions in the file to read keys again, instead of going to the top of the file? I have already created different input files to allow for easy testing of certain parts of the program, except it reads the file over and over again instead of giving it back to the regular STDIN.

---

### Post by Captain Giraffe on 2010-10-04
A - (minus, stdin) appended to cat should give you this.
```
cat inputs_file - | program_executable
```

---

### Post by cipherboy_loc on 2010-10-05
Thank you. This does exactly what I wanted. 



Thank you again, 

Cipherboy

---

