---
title: "Application in Terminal?"
date: 2012-02-09
forum: General Help
---

### Post by onilink422 on 2012-02-09
Hey all, I want to make a script to run an application in the Terminal. Let's say I want to run minecraft in the terminal with Java 6 runtime. 
/home/onilink422/.minecraft/bin  
and the file inside is 
minecraft.bin
I know how to make a script, but how do I make the magic happen? any magicians willing to help? :shock:

---

### Post by raja.genupula on 2012-02-09
you mean you wanna run that script ? 

```
chmod +X <your_script>.sh
./<you_script>.sh

```
it will run that script. 

i am not getting that "magic" meaning .

something else you are expecting ?

please provide us some more information .

---

### Post by onilink422 on 2012-02-09
I know how to run the script, but I need the actual scriptness. I know how to make an .sh

---

### Post by Vishnu V on 2012-02-09
Just make a file and save it as .sh
Content of file is the command to run your application

---

### Post by drmrgd on 2012-02-09
I'm a little confused as to what you want to do (but I've also never run minecraft before).  If you just want to launch an application from the Terminal, you just have to type the name (assuming the binary is located in a path that's part of your $PATH variable).  

If you've compiled it to another directory, then all you need to do is to make sure the executable is set to be executable (which it seems you already know), and then launch it:

```
./pathtoexectuable/minecraft.jar
```  

I supposed you could create a script to save you from typing the above like:

```
#! /bin/bash
/pathtoexectuable/minecraft.jar start
```

You could also add an alias to your .bashrc file (which may be smarter depending on just what you want).

---

### Post by onilink422 on 2012-02-09
> **Vishnu V said:**
> Just make a file and save it as .sh
Content of file is the command to run your application
Sad that many people do not know how to read. I already said I needed the script! I know how to make an .sh script, but I needed the actual scripting. o.O

Anyway, thanks drmrgd, that helped a lot. :D


btw this is my script.

#! /bin/bash
cd onilink422/.minecraft/bin/
java -jar minecraft.jar
 Thnaks again, drmrgd, you are amazing

---

### Post by _0R10N on 2012-02-09
Well, if you want to make a script for running a Java program, you must code something like this in your script

```
java -jar jar_file.jar
```

In case you want to run the program with a different JRE than the system uses by default, then you should code

```
 /path_to_the_specific_jre/java -jar jar_file.jar
```

I hope this helps you out.

---

### Post by efflandt on 2012-02-09
I could be wrong, but I believe you are attempting to run the wrong minecraft.jar.  Typically you need to run the minecraft.jar with the launcher that you downloaded originally (version should not matter, just that it is a release version that includes the launcher).  That is what logs you in and runs (or creates if non-existing) the minecraft.jar in ~/.minecraft/bin/

I don't think the one in ~/.minecraft/bin includes a launcher, at least I know it does not in prerelease snapshots.

Also if you create a **bin** directory in your home directory (~/bin), once you log out and log back in once, put any scripts there and that **bin** will automatically be in your $PATH, so you will not need to use ./ prefix.

Don't forget to **chmod u+x scriptname** to give any new scripts execute permission.

The script I use is:

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/Downloads
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```The example on minecraft.net is incorrect as it shows **M**inecraft.jar when the download is **m**inecraft.jar (Linux filenames are case sensitive).

---

### Post by cortman on 2012-02-09
> **onilink422 said:**
> Sad that many people do not know how to read. 

This comes across as unnecessarily belligerent. Keep in mind that these are people volunteering to help you.

> **onilink422 said:**
> I already said I needed the script! I know how to make an .sh script

If this is the case, you DO NOT know how to make a script, you know how to create a file and give it a .sh extension. Be clear.

If you just want to run a .jar file, it would be as simple as

```

#!/bin/bash
java -jar /pathtojar/my_jar.jar
```

That's it. Save that in your /bin folder (you'll need sudo permissions to do that) after making it executable as shown above.

---

### Post by onilink422 on 2012-02-09
> **cortman said:**
> This comes across as unnecessarily belligerent. Keep in mind that these are people volunteering to help you.



If this is the case, you DO NOT know how to make a script, you know how to create a file and give it a .sh extension. Be clear.

If you just want to run a .jar file, it would be as simple as

```

#!/bin/bash
java -jar /pathtojar/my_jar.jar
```That's it. Save that in your /bin folder (you'll need sudo permissions to do that) after making it executable as shown above.


I DO know how to make a script, sir I have been doing it for years. I just couldn't get this one to execute properly because I realized I was using the wrong extention, I was inserting a .bin instead of a .jar file as my sun java launcher. Yes, I am very experienced with .sh scripting. I just couldn't figurer out why it wasn't working. I agree I could have been a little more clear, so that is my fault.
I wonder why people make assumptions about people they know nothing about? ;)

---

