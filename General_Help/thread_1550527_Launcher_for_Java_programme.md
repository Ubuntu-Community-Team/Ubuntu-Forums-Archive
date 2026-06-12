---
title: "Launcher for Java programme"
date: 2010-08-11
forum: General Help
---

### Post by drpjkurian on 2010-08-11
Hi Friends
I have a programme known as OpenRep which can be launched by executing the file named OpenRep.jar by OpenJDK Java 6 Runtime programme

This programme can also be launched through terminal by the command
```
java -jar OpenRep.jar
``` 

The location of the programme is in my Home folder.

Well I would like to create a launcher for that programme.
Please guide me

---

### Post by surfer on 2010-08-11
you could write a shell script (and make it executable) with +/- these contents:

```

#!/bin/bash

HERE=$(/bin/readlink -f "${BASH_SOURCE}")
HERE_DIR=$(/usr/bin/dirname "${HERE}")

/usr/bin/java -jar "${HERE_DIR}/OpenRep.jar" 

```

the way the script is written it must be in the same directory as the jar. make sure it is executable.

the HERE and HERE_DIR variables at the beginning make sure that the jar is found if you start the bash script from a different directory.

---

### Post by drpjkurian on 2010-08-11
Hi Surfer
Thank you very much for your prompt reply.
Well I would be grateful if you check my the script 

My location of the executable file is in
/home/repertory/open/

So therefore the script should be 
```
#!/bin/bash

/home/repertory/open/=$(/bin/readlink -f "${BASH_SOURCE}")
/home/repertory/open/=$(/usr/bin/dirname "${HERE}")

/usr/bin/java -jar "$/home/repertory/open//OpenRep.jar"
```

Am I right

---

### Post by surfer on 2010-08-11
there is no need to change the script!

just save the code above in a file called OpenRep.sh (for example) put it in the same directory as the jar and make it executable. the rest should work as is!

---

### Post by drpjkurian on 2010-08-11
I will give a try buddy

---

### Post by luigi_mb on 2010-08-11
In most cases, where the jar to be executed resides in a folder with other dependent jars, commands such as

```

/usr/bin/java -jar "$/home/repertory/open//OpenRep.jar"

```

do not work (unless you have the correct -lc switch in the command). You must first cd to the folder where the jar resides (but always read the docs accompanying the software). In your case, something like this should work

```

$ cd /home/repertory/open
$ java -jar OpenRep.jar

```


/luigi

---

### Post by surfer on 2010-08-11
you can also add the classpath to the command line:

```

#!/bin/bash

HERE=$(/bin/readlink -f "${BASH_SOURCE}")
HERE_DIR=$(/usr/bin/dirname "${HERE}")

/usr/bin/java -cp "${HERE_DIR}" -jar "${HERE_DIR}/OpenRep.jar"

```

that should then find the other .jar files in the directory.

---

### Post by drpjkurian on 2010-08-11
DEAR Friends

I am very sorry to say that I do not know how to make .sh file and make it executable.

I know that this is a basic question but Unfortunately I did not get the procedure of making it (.sh file) by googling

---

### Post by claracc on 2010-08-12
> I am very sorry to say that I do not know how to make .sh file and make it executable.


You simply do :
In xterm, you go to your home folder, you make the software executable with : chmod +x OpenRep.jar. In this way, the file can be running.

---

### Post by claracc on 2010-08-12
> I have a programme known as OpenRep which can be launched by executing the file named OpenRep.jar by OpenJDK Java 6 Runtime programme

This programme can also be launched through terminal by the command
Code:

java -jar OpenRep.jar

The location of the programme is in my Home folder.

Well I would like to create a launcher for that programme.
Anyway, I think you can create the launcher through the GUI:
you go to to system --> preferences -->main menu, there you select a menu where the launcher will be situated, then new element. In the command line i would write /usr/bin/java -jar /home/OpenRep.jar. Then click on accept and try if it works.

---

### Post by Cabalbl4 on 2010-08-12
> **drpjkurian said:**
> DEAR Friends

I am very sorry to say that I do not know how to make .sh file and make it executable.


A .sh file is just a text file with .sh at the end of it's name. So just open gedit or similar program, put the text in, and save it anywhere with the name "NAMEOFFILE.sh" . Then make it executable as described above via chmod.

---

### Post by drpjkurian on 2010-08-12
Dear Claracc

Thank You very much.
But the command line did not help me.

> **claracc said:**
> Anyway, I think you can create the launcher through the GUI:
you go to to system --> preferences -->main menu, there you select a menu where the launcher will be situated, then new element. In the command line i would write /usr/bin/java -jar /home/OpenRep.jar. Then click on accept and try if it works.

---

### Post by drpjkurian on 2010-08-12
I DID IT

Thank you Very Very Much

---

