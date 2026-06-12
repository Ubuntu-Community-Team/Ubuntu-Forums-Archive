---
title: "Fiile not found, but it is there."
date: 2011-01-31
forum: General Help
---

### Post by coilwinder on 2011-01-31
Hi. Hope someone can point me in the right direction here.

I occasionally use an offline blogging software named Bleezer, which is a .jar file. It has worked before (like, two months ago), and to my knowledge I haven't messed with the java on this machine.

Using Ubuntu 9.10, 32-bit (on an AMD Phenom II x4 965 BE, if that helps).

I used to use terminal and just cd to the directory, then issue a
```
./Bleezer
```
to use it. Now, however, it gives me the following error message:
```
Bleezer.jar: command not found
```

But it is right there, if I do a "ls":
```
ls -l
total 1112
-rwxr-xr-x 1 myuser 1000 617278 2007-02-11 16:07 Bleezer.jar
-rw-r--r-- 1 myuser 1000   6196 2010-08-09 07:34 Bleezer.xml
-rwxr-xr-x 1 myuser 1000 489471 2006-11-10 21:33 english.0
drwxr-xr-x 2 myuser 1000   4096 2010-01-30 20:29 lib
-rw-r--r-- 1 myuser 1000   7273 2005-12-23 09:25 phonet.en

```

I read somewhere in another thread about 64-bit vs 32-bit, and that this could be connected to the problem, I just don't really see how. If I do a "uname -m", i get "i686" for an answer. So I got a 32-bit OS, I knew that, and as stated it has worked before.

I also tried to switch the java vm (interpreter, not compiler) just now, from openjdk to sun, just in case, but it didnt help. Neither do issue the command "java Bleezer.jar" ("Could not find the main class: Bleezer.jar. Program will exit."). Other java software works though, so this was just a last resort for my limited ubuntu troubleshooting skills.

Could it be some of the later system updates broke something maybe?

I'd like to get this working again, even if it is pretty quirky (or if someone got a better alternative to Bleezer).

---

### Post by Hoopz on 2011-01-31
maybe this will help [http://ubuntuforums.org/showthread.php?t=348698](http://ubuntuforums.org/showthread.php?t=348698)

---

### Post by |{urse on 2011-02-01
java -jar Bleezer.jar

yep ^_-

the ./ is for running bash scripts. If you prefer using ./ you can do something like this.

> 
gksudo gedit

Now paste the tiny bash script below in gedit. 
> 
#! /bin/bash
cd ~/Bleezer/
java -jar Bleezer.jar

now change the "cd ~/Bleezer/" part to the actual path to the working directory where your .jar is stored and save the text file as Bleezer .

Next, make it executable.
> 
chmod +x Bleezer

then you can launch it with ./Bleezer which saves you some keystrokes if you plan on running this from terminal a lot in the future =)

---

### Post by coilwinder on 2011-02-01
Thank you both!
> java -jar Bleezer.jar

yep ^_-

What do you know, that at least started to run it!
The Bleezer.jar was set to executable, and I'm pretty sure I used the ./ to run it before. 

Except it hangs on a new error message now;
```
[ERROR]: (HTMLTranslate.class) creating the character-to-reference mapping table

```
Which I guess is unrelated to my original problem. This too didn't happen before btw.

Anyway, thanks for your tips!

---

