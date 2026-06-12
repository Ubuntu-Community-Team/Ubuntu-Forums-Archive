---
title: "help please."
date: 2009-12-26
forum: General Help
---

### Post by aydn on 2009-12-26
i'm new to linux and was wondering if there anyway to use a run.bat on ubuntu 9.10? because when i try run it, it comes up with gedit text editor with this.

@echo off
title interrupted client by dieter
echo client by dieter
cd src
java L
exit

any help at all would be really appreciated.

also someone said something about turning it into a shell script but i didn't understand, if someone could explain it would be great.

---

### Post by Mr Nemo on 2009-12-26
Try running it out of a terminal using sudo. Probably cd (location of file) then sudo ./(nameoffile)

---

### Post by aydn on 2009-12-26
cd /home/ringo/Desktop/interrupted v2 client/interrupted client did 'no such file or directory' and sudo /home/ringo/Desktop/interrupted v2 client/interrupted client did 'command not found'

/home/ringo/Desktop/interrupted v2 client/interrupted client was location in run.bat properties

---

### Post by NFblaze on 2009-12-26
I dont think it would run because .bat are for the Windows environment. Pretty much they are like scripts for windows.

Tho I could be wrong, but I'm very sure that those are Windows speicfic.

You can try it in the terminal, but make sure you make it executable, by typing 
[I]
chmod +x run.bat [/I]

in a terminal. I'm sure it wont work tho in Linux.


Also, to turn it into a shell script, basically all you need to do is kinda port over the commands into something Linux will understand (like bash commands) and make it executable. Tho, you would have to make sure you know what you want the script to do.

---

### Post by Mr Nemo on 2009-12-26
Where is the .bat located?

---

### Post by aydn on 2009-12-26
can anyone translate this to a shellscript?

@echo off
title interrupted client by dieter
echo client by dieter
cd src
java L
exit

> **Mr Nemo said:**
> Where is the .bat located?

says this is location in properties/home/ringo/Desktop/interrupted v2 client/interrupted client
sorry if i sound dumb i'm new to this

---

### Post by aydn on 2009-12-26
bump, sorry.

---

