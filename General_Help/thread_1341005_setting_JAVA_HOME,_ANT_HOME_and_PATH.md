---
title: "setting JAVA_HOME, ANT_HOME and PATH"
date: 2009-11-29
forum: General Help
---

### Post by johnyjj2 on 2009-11-29
Hello!

I try to follow this: [http://cmusphinx.sourceforge.net/sphinx4/#how_build](http://cmusphinx.sourceforge.net/sphinx4/#how_build) and they say "[FONT=Arial]Set your JAVA_HOME, ANT_HOME and PATH environment variables as described above.[/FONT]". I don't see any "description above". Above it is only written how to unpack files and where to download those from. My java -version says:

mainaccount@mainaccount-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/lib$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)
mainaccount@mainaccount-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/lib$ 

Do I need to type "export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun" or should I type something else? What about "ANT_HOME and PATH"? Ant -version says:

mainaccount@mainaccount-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/lib$ ant -version
The program 'ant' is currently not installed.  You can install it by typing:
sudo apt-get install ant
ant: command not found
mainaccount@mainaccount-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/lib$ 

Greetings!

---

### Post by raffaele181188 on 2009-11-29
Ant is a build tool and is not currently installed on your system, so you need
```

sudo apt-get install ant

```
It should also set your ANT_HOME, but you may need to log out/in. PATH is automatically set by your Ubuntu. Anyway, to check a variable you just type
```

echo -e "java=$JAVA_HOME \nant=$ANT_HOME \npath=$PATH"

```
Anyway after installing ant everything should go. cd to sphinx4 directory (there should be a build.xml file) and type
```

ant

```

---

### Post by johnyjj2 on 2009-11-29
Thank you for your answer!

I thought I should have everything installed properly. But:

mainaccount@mainaccount-laptop:~$ echo -e "java=$JAVA_HOME \nant=$ANT_HOME \npath=$PATH"
java= 
ant= 
path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
mainaccount@mainaccount-laptop:~$ ant
Buildfile: build.xml does not exist!
Build failed
mainaccount@mainaccount-laptop:~$ 

Greetings!

---

### Post by johnyjj2 on 2009-12-04
May I have your answer, please, what to do?

---

### Post by john newbuntu on 2009-12-05
First install ant as suggested by raffaele above.
Open a terminal and edit your .bashrc file in your home directory (if it exists otherwise create a new one) and set these 3 variables in there:
```

export JAVA_HOME=/usr/local/jdk1.5.0_07
export ANT_HOME=/usr/local/ant
export PATH=$PATH:${JAVA_HOME}/bin:${ANT_HOME}/bin
```

Now, I just picked some random folder names here.  Figure out the exact directory/folder where your jdk.xxxx. and ant are installed.

After saving the .bashrc file, type:
```
. .bashrc
```
and then proceed with whatever you need to do.

---

