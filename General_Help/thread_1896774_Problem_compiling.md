---
title: "Problem compiling"
date: 2011-12-17
forum: General Help
---

### Post by icedice on 2011-12-17
Its a pain to have to open a terminal and then cd to my dirctory and then type javac -cp ./*.java all the time so I made an executable bat file with the command in it but for what ever reason its not working. heres what i have type in it:

```
javac -cp ./*.java 
pause
```The first line is exactly what I type into the terminal after i change directories but when i try to run this it opens the terminal for a second and then closes. What would be making it do that?

---

### Post by docbop on 2011-12-17
What do you mean have to do it all time.  You open a terminal window and leave it open.  What I do is either open a second terminal and have my editor open in it.  So edit in one, compile in the other other.   Taking advantage of history command I don't have to re-type the command each time.

So you're a Window person... it a script not batch file and pause is a Windows command not unix.   Are you running the script from a terminal or from the file manager, my guess the file manger that's why your trying to pause the output.   Run from a terminal once you get used to it, it's a faster process.

Also may want to consider sending the output from the compiler to a file so you can go back to it.   At the end of your javac line add   >& jerror    That send stderr to a file call jerror or whatever filename you desire. 

I think you'll find if not using an IDE programming in terminal windows with scripts or even just using history to pull back a previous commnad line is a few fast way to work.

---

### Post by icedice on 2011-12-17
alright thanks for the help

---

