---
title: "How do i compile Java?"
date: 2011-04-22
forum: General Help
---

### Post by Kitkin15 on 2011-04-22
Ok so ive been using a bot for Runescape to get my levels up while im asleep, ive been using it on Windows because the batch file provided to compile scripts obviously cant work on Ubuntu, today i finally thought about compiling on Ubuntu because its no longer working on Windows, and i truthfully dont feel like fixing Windows anymore.
How do i compile these scripts? Their located in:
home/myusername/RSBot/Scripts/Sources

I googled and i found this code:
# export PATH=$PATH:/usr/java/jre.6.0_24/bin
Which is where Java is corectly installed on Ubuntu, i just have no idea what to do with this command. I entered it in the Terminal and all it did was provide a new space for me to enter, as if the code was correctly entered and completed. But i dont see how it would complete anything...

Can anyone help me with this?

Thanks

  -Kitkin15

---

### Post by Kitkin15 on 2011-04-24
Can anyone help me with this?

---

### Post by r-senior on 2011-04-24
You don't need to recompile Java classes. You can just move them from one architecture to another and they should work. Write once, run anywhere and all that.

Do you just need to run a Java program?

The PATH command you list shouldn't be necessary. Could you try this in a terminal and see if you have Java runtime installed?

```
java -version
```

Also, what are these scripts you speak of? Are they .jar files? Or do they have no extension on the file name?

---

### Post by Kitkin15 on 2011-05-10
The files have a .java extension. Are you sure that the above code will work sense it dont link to the files?


What i do is i grab the code and save it as "BlahBlahBlah.java" Then when i compile them they make other files ".class and some other files" And those are needed to run the script, so i need to make it compile. Ive been compiling them on my brothers Windows laptop and then transferring them to Ubuntu, but he dont like me doing that and i can no longer do it.

---

### Post by WorMzy on 2011-05-10
You can compile java with javac, a terminal app.

```
javac /path/to/source/file.java
```

---

### Post by Kitkin15 on 2011-05-10
Really its that easy? Ok thank you, ill try it out right now and see what happens :)

---

### Post by Kitkin15 on 2011-05-10
How do i make it compile ALL .java in a directory instead of doing it singularly?

---

### Post by Kitkin15 on 2011-05-10
*.java seemed to do the trick

---

