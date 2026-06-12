---
title: "can't mark allow executing file as program"
date: 2010-10-23
forum: General Help
---

### Post by s.shawky on 2010-10-23
yesterday,I upgraded to ubuntu 10.10
then when i try to mark allow executing file as program it unmarks itself although i used it on ubuntu 10.4

---

### Post by s.shawky on 2010-10-23
any help

---

### Post by TeoBigusGeekus on 2010-10-23
```
chmod +x /path/to/file
```
Do you get any error messages with that?

---

### Post by s.shawky on 2010-10-23
no all what happen  when i mark it my mark is unmarked automatically then i cant open that prog

---

### Post by TeoBigusGeekus on 2010-10-23
Open a terminal and give the command of my previous post.

---

### Post by s.shawky on 2010-10-23
> **TeoBigusGeekus said:**
> Open a terminal and give the command of my previous post.

No command 'chomd' found, did you mean:
 Command 'chmod' from package 'coreutils' (main)
chomd: command not found

---

### Post by TeoBigusGeekus on 2010-10-23
You mistyped the command, its chmod and not chomd.

---

### Post by s.shawky on 2010-10-23
can you tell me what do you mean by path/to/file

---

### Post by TeoBigusGeekus on 2010-10-23
Where is your file?

---

### Post by s.shawky on 2010-10-23
> **TeoBigusGeekus said:**
> Where is your file?
FOR EX
the partition softs / programs/FreeRapid-0.83u1

---

### Post by TeoBigusGeekus on 2010-10-23
Well, then, if your file is named FreeRapid-0.83u1
```
chmod +x /softs/programs/FreeRapid-0.83u1
```

---

### Post by s.shawky on 2010-10-23
nothing happens

---

### Post by TeoBigusGeekus on 2010-10-23
What's the name of the file?

---

### Post by s.shawky on 2010-10-23
frd.jar

---

### Post by TeoBigusGeekus on 2010-10-23
So, open terminal and type
```
chmod +x /softs/programs/FreeRapid-0.83u1/frd.jar
```
to make it executable
and then
```
java -jar frd.jar
```
to execute it.

---

### Post by s.shawky on 2010-10-23
it is still non-executable

---

### Post by TeoBigusGeekus on 2010-10-23
No error messages?

---

### Post by Ubuntows Rocks on 2010-10-23
Have you tried changing the permissions then allowing executable? If that fails try moving the folder, changing permissions and then allowing executable. Has happened to me before but that did the job. Normally if Linux does trust the file it may not allow it to be executable but usually you can change it.

---

### Post by s.shawky on 2010-10-23
no but from the start when i try to open that prog 
this message The file '/media/softs/programs/FreeRapid-0.83u1/frd.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.



of course i used this dir too /media/softs/programs/FreeRapid-0.83u1/frd.jar

---

### Post by Ubuntows Rocks on 2010-10-23
> **s.shawky said:**
> no but from the start when i try to open that prog 
this message The file '/media/softs/programs/FreeRapid-0.83u1/frd.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.



of course i used this dir too /media/softs/programs/FreeRapid-0.83u1/frd.jar
  
Move the folder and change permissions (so you have full control of the files and folders then that should do it, if not then I´m clueless...
EDIT just changing my keyboard (wrong settings)

---

### Post by s.shawky on 2010-10-23
> **Ubuntows Rocks said:**
> Have you tried changing the permissions then allowing executable? If that fails try moving the folder, changing permissions and then allowing executable. Has happened to me before but that did the job. Normally if Linux does trust the file it may not allow it to be executable but usually you can change it.

it worked when i moved the folder to the desktop

---

### Post by Ubuntows Rocks on 2010-10-23
> **s.shawky said:**
> it worked when i moved the folder to the desktop

Please mark this solved now so there's no need for anyone else to say anymore :)

---

### Post by ndriw on 2010-12-06
thx bro... cool!!!!

---

### Post by rostamiani on 2011-03-07
Thanks everyone
but it does not solved !
I cannot move every 2 GB files to my home directory just for changing permissions !

Is this a bug ?

---

### Post by jermerf on 2011-04-20
Same here. I can't move every......single.........file........ just to set it executable. If I have to go through the command prompt to set something like this I'm just wasting more time until it doesn't work. Is there a way of disabling it from checking for the executable bit. I am aware of the security issue, but I don't care. I thought linux was about 'freedom', Ubuntu seems to be 'freedom if you follow these rules'.

EDIT

And of course by command prompt I mean terminal

---

### Post by JimiJams91 on 2011-05-03
Does anyone know a work around for this? I don't have enough space on my desktop to move all my programs there just to get permission to execute the file.

---

### Post by FlekkeN on 2011-05-04
first method:
right click -> properties -> permissions -> mark executable 

second method:
chmod +x path/to/file
eg.: chmod +x /home/user/programs/something.jar

If none of the above works you could check that the mounted filesystem have the "exec" option set. If not set it and try again one of the methods.

---

### Post by Morbius1 on 2011-05-04
A jar file does not have to be executable to run. 3 options:

** [1] Do it from the terminal as TeoBigusGeekus stated above:**
```
 java -jar "path/to/jar/file"
```** [2] Change the file association:**
Right click an *.jar file and select Properties  -> Open With -> Add -> Use a custom command > type in:
```
java -jar
```In the "Open With" tab mark the "jar"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default .

** [3] Fix the problem at it's source:**

As root go to /usr/share/applications/Sun Java 6 Runtime

Right click > Properties > And in the command box change it from this:
> cautious-launcher %f /usr/lib/jvm/java-6-sun-1.6.0.24/bin/java -jarTo this:
```
/usr/lib/jvm/java-6-sun-1.6.0.24/bin/java -jar
```It's not java it's "cautious-launcher" that's the problem.

*I prefer option 2 myself*.

---

