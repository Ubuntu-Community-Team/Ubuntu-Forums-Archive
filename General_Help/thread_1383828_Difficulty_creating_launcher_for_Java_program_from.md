---
title: "Difficulty creating launcher for Java program from terminal"
date: 2010-01-17
forum: General Help
---

### Post by Coco999 on 2010-01-17
I run a program by executing this command in a terminal screen.
```
coco@coco-desktop:~/Escritorio/MO_1.10/MagnumOpus$ java -jar MagnumOpus.jar
```

Since it is a bit tedious, I tried to create a launcher. I copied the above code into the Command box. The launcher is created, but fails to run the program. Instead I get an error message.

What must I do?

---

### Post by sisco311 on 2010-01-17
In the command field of the launcher type:
```
bash -c "cd ~/Escritorio/MO_1.10/MagnumOpus && java -jar MagnumOpus.jar"
```

or create a script:
```
#!/bin bash
cd path/todir
java -jar whatever
```
make it executable and run from a launcher.

---

### Post by Coco999 on 2010-01-17
> In the command field of the launcher type:

```
bash -c "cd ~/Escritorio/MO_1.10/MagnumOpus && java -jar MagnumOpus.jar"
```



Thank you very much. This did the trick. However, I wonder why.

> or create a script:


```
#!/bin bash
cd path/todir
java -jar whatever
```

make it executable and run from a launcher. 

It is not clear to me what a script is and how to make it executable. Has this second method any advantage over the first one?

---

### Post by sisco311 on 2010-01-17
> **Coco999 said:**
> Thank you very much. This did the trick. However, I wonder why.


bash -c "command1 && command2" = run **command1 && command2** in bash, bash is the default shell (the one you are using in the terminal).

cd /path/to/dir = change the current working directory to /path/to/dir

java -jar xxx.jar = launch the java application 

It's the automation of what you have to type in the terminal to run the application.

> **Coco999 said:**
> 
It is not clear to me what a script is and how to make it executable. Has this second method any advantage over the first one?


Scripts are collections of commands that are stored in a text file. 

To make a executable, right click on it, select Properties -> Permissions tab and select the *Allow executing file as program* checkbox. 

Now you can simply double click the file to execute it.

For more details see:
 
[uhelp]community/UsingTheTerminal[/uhelp]
[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

### Post by Coco999 on 2010-01-17
Thank you very much, sisco311, for your efficient help and explanations. I'll study the reference you gave me. But I'll close this thread as solved.

My best wishes and regards.

---

### Post by Dreamer-of-Days on 2010-02-16
Quite helpful. Used this to create a launcher for PS3 MediaServer among other things. Thanks sisco.

---

### Post by Juan.Solo on 2010-06-25
> **sisco311 said:**
> In the command field of the launcher type:
```
bash -c "cd ~/Escritorio/MO_1.10/MagnumOpus && java -jar MagnumOpus.jar"
```

or create a script:
```
#!/bin bash
cd path/todir
java -jar whatever
```
make it executable and run from a launcher.
sisco311, you're a lifesaver! Thanks, #1 worked perfectly!

---

