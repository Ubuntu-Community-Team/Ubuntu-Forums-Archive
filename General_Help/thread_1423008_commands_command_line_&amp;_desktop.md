---
title: "commands: command line &amp; desktop"
date: 2010-03-06
forum: General Help
---

### Post by unueco on 2010-03-06
Hi...I'm new to linux and Ubuntu. Have two questions that are probably extremely basic.....so basic that I cannot find answers in any of my reference texts (mainly because I don't know what keywords to use for the searches).

The two questions are:
1. When at the command line, how do you enter a dir or filename that contains a <space> character. What I mean is that if I have a dir called "BIG DIR" and a in it is a file called "random file", how do I do a cd from /home to that dir? How do I execture an ls for that file?


2. How do I edit commands that appear in my desktop pull down menu? For example, when I shutdown by using the pulldown menu option, a message goes up that the system is shutting down in 60 sec. I'd like to change that to 10 sec. I know how to use the shutdown command from the command line.....but how/where do I edit the properties of that pull down option?

3. What is a good resource for researching such questions. I have the following textbooks:

Ubuntu Unleashed 2010 edition
Ubuntu Linux Toolbox
Ubuntu Hacks

The info I'm seeking "might" already been in there...but I haven't been able to find it....

THANX!!

---

### Post by JamezQ on 2010-03-06
For files with spaces you can use cd "BIG DIR" with quotes or just cd BI*

---

### Post by HPD2 on 2010-03-06
> **JamezQ said:**
> For files with spaces you can use cd "BIG DIR" with quotes or just cd BI*

you should also say the if you use "cd BI*" the * acts as a wild card, and if you have more than one directory that starts with BI then it will cd to the first alphabetical directory.

---

### Post by darolu on 2010-03-06
> **unueco said:**
> Hi...I'm new to linux and Ubuntu. Have two questions that are probably extremely basic.....so basic that I cannot find answers in any of my reference texts (mainly because I don't know what keywords to use for the searches).

The two questions are:
1. When at the command line, how do you enter a dir or filename that contains a <space> character. What I mean is that if I have a dir called "BIG DIR" and a in it is a file called "random file", how do I do a cd from /home to that dir? How do I execture an ls for that file?


2. How do I edit commands that appear in my desktop pull down menu? For example, when I shutdown by using the pulldown menu option, a message goes up that the system is shutting down in 60 sec. I'd like to change that to 10 sec. I know how to use the shutdown command from the command line.....but how/where do I edit the properties of that pull down option?

3. What is a good resource for researching such questions. I have the following textbooks:

Ubuntu Unleashed 2010 edition
Ubuntu Linux Toolbox
Ubuntu Hacks

The info I'm seeking "might" already been in there...but I haven't been able to find it....

THANX!!
**1)**
To type spaces or special characters you use "\"; for example:
```
$ cd Big\ Dir/

$ ls ~/ls Music/Vladimir\ Ashkenazy/Rachmaninov\:\ Piano\ Concertos\ Nos.\ 2\ \&\ 3/
```

**2)**
I don't know how to change that, but you can use a different applet. Right click on your panel - Add.
I know how to eliminate the confirmation box so it shuts down immediatly though; press ALT+F2 type "gconf-editor" in, and go to Apps - Indicator

**3)**
Google always helps, you need to learn how to use it though; I usually use [http://www.google.com/linux](http://www.google.com/linux) to limit my search to linux-related websites, use quotation marks when looking for exact sentences/phrases "mplayer -playlist" is not the same as *mplayer -playlist*, second option will take out all results with -playlist-; etc...

---

### Post by unueco on 2010-03-06
Thank you very much to all who replied...excellent suggestions.  :D

(Still looking for information on how to change properties of pull-down menu commands.)

---

### Post by unueco on 2010-03-06
By the way.....

> **darolu said:**
> 

**3)**
Google always helps, you need to learn how to use it though; I usually use [http://www.google.com/linux/](http://www.google.com/linux/) to limit my search to linux-related websites.......


I tried this and if resulted in a 404 error:

"The page - **[www.google.com/linux/](www.google.com/linux/)** - does not exist."

---

### Post by Lunx on 2010-03-06
[URL="http://www.linuxcommand.org/index.php"]
Linux Command[/URL] is a good site for learning about working with the CLI. There is also a PDF available from that site which deals with the topic in a more in-depth manner. You can download it [here]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download").

The Ubuntu Pocket Guide also covers the basics of working at the command line (as well as the general basics of using Ubuntu), you can find it by clicking on the Pocket Guide link in my signature

---

### Post by mk1w86 on 2010-03-06
A quick tip, you can use the tab key to auto complete commands.  For example type ```
ls B
``` and press tab to auto complete the directory name ('Big Dir' in this case).  You can press tab twice to list the contents of a directory if more than one starts with B for example.  You can also use it to complete commands as well directory/filenames e.g. ```
apti
``` will auto complete to aptitude when you press tab, again press tab twice to list all possible commands starting with apti.

I'm sure you will get the hang of it. :D

---

### Post by asmoore82 on 2010-03-06
> **unueco said:**
> By the way.....

I tried this and if resulted in a 404 error:

"The page - **[www.google.com/linux/](www.google.com/linux/)** - does not exist."

take off the last slash: [http://www.google.com/linux](http://www.google.com/linux)

---

### Post by darolu on 2010-03-07
> **unueco said:**
> By the way.....




I tried this and if resulted in a 404 error:

"The page - **[www.google.com/linux/](www.google.com/linux/)** - does not exist."

My bad sorry, as asmoore82 said, you have to take off the slash at the end (I just edited my post).

---

