---
title: "puzzlement with attempt to install SUN java 6 sdk"
date: 2010-10-31
forum: General Help
---

### Post by mrodent on 2010-10-31
I did this

chris@E6410:~$ java -version
> java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

then I did this 

chris@E6410:~$ sudo -i
root@E6410:~# add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
... # sudo apt-get update
# update-java-alternatives -l 
- I got: 
> java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

- then I did
# apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk
- (all sorts of packages were installed)... at the end I got a message 
> 
already installed by openjdk-6 
Setting up sun-java6-jre (6.22-0ubuntu1~10.04) ...
Setting up sun-java6-jdk (6.22-0ubuntu1~10.04) ...
Setting up visualvm (1.3-0ubuntu2)

- then I ran this again
# update-java-alternatives -l 
- and this is what I got (again)
> java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

why am I apparently not being told that I have SUN java 6 SDK on my sys as an option? 
and assuming it is indeed there, how do I choose to use it?
:confused:

---

### Post by lykeion on 2010-10-31
> **mrodent said:**
> 
why am I apparently not being told that I have SUN java 6 SDK on my sys as an option? 
and assuming it is indeed there, how do I choose to use it?
:confused:

You don't need to install both sun-java6-jre and sun-java6-jdk, as the latter package includes the JRE. If you *develop* Java applications yourself, keep the JDK. If you only need Sun Java to *run* Java applications, keep the JRE and uninstall the JDK.

To set the java runtime alternative to Sun Java:
sudo update-java-alternatives -s java-6-sun

---

### Post by mrodent on 2010-10-31
Hi,

Thanks for the reply... yes I do indeed want to write java apps, using Sun java, not OpenJDK java.  Or rather I'd like to be able to do both.

I ran your command... this is what I got:

> update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so for mozilla-javaplugin.so not registered, not setting.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so

More to the point, correct me if I'm wrong... but shouldn't
*update-java-alternatives -l *
list all the the various java possibilities (including different SDKs) present on your system... mine lists only the openjdk... even though I had a message during my attempt at installing ***SUN*** java (see my OP) saying 
> Setting up sun-java6-jdk (6.22-0ubuntu1~10.04) ...

NB after running the command you suggested I still get the same output from 
*update-java-alternatives -l*
as before... no sign of Sun SDK... 

hence... ?

---

### Post by lykeion on 2010-10-31
I think you are confusing things here.
The command update-java-alternatives -l will list the available paths to the java binary runtime, so a result like yours:
[FONT="Courier New"]java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun [/FONT]
indicate that you can chose between either OpenJDK java or Sun Java runtime.
Even though that you have installed both Sun Java JRE and JDK, you'll still only will have one Sun Java binary runtime. 
The Sun Java JDK and JRE packages overlap each other. The difference between JDK and JRE is that the JDK contains the Java compiler, 
i.e. the JDK allows you to compile and run Java from source code whereas the JRE only allows the running of Java byte code, i.e. source that has already been compiled.

---

### Post by mrodent on 2010-10-31
Thanks again,

OK I didn't know that about update-java-alternatives...

The Sun JDK contains the Sun JRE. Fine. 

How do I use the Sun JDK?  Is it available?  Where's it likely to be?

Sorry if I'm being tedious ... but I am a newb.

:-({|=

---

### Post by lykeion on 2010-10-31
No problems, everyone's a newb in the beginning.
You can compile Java sourcecode either from command-line or in an IDE. I'd recommend starting from command-line.

Use a text-editor and create a textfile with the filename Hello.java, and paste this code into it:
[PHP]public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}[/PHP]

Open a terminal and go to the dir where you saved the file.
Compile your source with the javac compiler:
```
javac Hello.java
```
This will create a Hello.class file with the compiled bytecode.
Run it with the java binary (it should output Hello world!):
```
java Hello
```

EDIT
If you can describe your programming experience, like if you've ever programmed in some language at all, or you are totally new to programming, I could point you to some starting places to learn (web pages, books, and stuff).

EDIT 2
And if you need introductory programming help, maybe this thread should be moved to Programming Talk

---

### Post by mrodent on 2010-10-31
... umm... no I know all this.

I want to use Sun JDK.

I am very experienced in programming java (!).

I want to use Sun JDK ... not OpenJDK.

As might have been clear from my opening comment of MyPost #2

> yes I do indeed want to write java apps, using Sun java, not OpenJDK java.

I am a newb in respect of ***Linux***... and this stuff to do with Sun JDK/OpenJDK is a bit of a specialist area, I suppose

---

### Post by lykeion on 2010-10-31
Well, excuse me if I'm being frank here, but you don't sound very experienced in Java if you can't tell the difference between JRE and JDK (and the SDK acronym was dropped a long time ago).
Furthermore OpenJDK is not exclusive to Linux. It's a project for the open-source implementation of Java started by Sun and now as a collaboration of IBM and Oracle.
If you've figured out how to select Sun Java JDK, you can tag this thread as solved: [http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by mrodent on 2010-11-01
Oh now you're getting annoying. There's never been any question of not knowing the diff between JRE/JDK. 

Also quite pointless if you don't take the trouble of reading what I've actually written... why don't you just not reply if you're not actually reading what I've asked about?

Who gives a toss whether I choose to go along with the new acronym?  Shows how many years I've been using this stuff.  So what?

To sensible people out there: I wish to use the Sun JDK/SDK, not the OpenJDK version.  The futile exchanges in this thread have not begun to answer my question.

To rephrase (for some other answerer maybe):

- I have chosen the Sun JRE rather than the OpenJDK JRE
- but how does the javac binary belonging to the Sun JDK get chosen when compiling code? Presumably there are two such files, one belonging to OpenJDK, the other to Sun JDK...?
- so how does the OS know which one to use (and where are they kept, by the way)?  Is this some sort of environment variable, and is the latter set when you run 
> sudo update-java-alternatives -v -s java-6-sun?

---

### Post by lykeion on 2010-11-01
Ok, no reason to get unfriendly with each other, I'm just trying to help here.

Back to the questions:
- how does the javac binary belonging to the Sun JDK get chosen when compiling code?

To get the full path to a command you can use *which* command, like this: ```
which javac
``` 
This will output the path /usr/bin/javac
To check what /usr/bin/javac points to you can enter:
```
ls -l /usr/bin/javac
```
You'll see that it's a symlink to /etc/alternatives/javac
To check next step:
```
ls -l /etc/alternatives/javac
```
In my case it's a symlink to /usr/lib/jvm/java-6-sun/bin/javac
and that's the javac binary which is used

- how does the OS know which one to use (and where are they kept, by the way)? Is this some sort of environment variable, and is the latter set when you run update-java-alternatives -s java-6-sun?

The available java alternatives as listed with update-java-alternatives -l are described in textfiles with .jinfo extension in /usr/lib/jvm directory. 
For example, java-6-sun is described in the file /usr/lib/jvm/.java-6-sun.jinfo. There all paths of the alternative are listed.
When you set an java alternative this file is read and the symlink /etc/alternatives/javac is changed accordingly.
You can get more info about update-java-alternatives using the *man* command:
```
man update-java-alternatives
```

Hope this long answer explains it...

---

### Post by mrodent on 2010-11-01
spot on... apologies for getting annoyed!

so update-java-alternatives -s does indeed rejig the mechanics of compiling as well as running java, although update-java-alternatives -l doesn't really tell you that, and leads to a spot of confusion, for a newb anyway, because of the *name* "openJDK"!

that simple piece of info is what I needed to know

thanks!

---

