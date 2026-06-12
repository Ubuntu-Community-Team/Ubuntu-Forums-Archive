---
title: "Java 1.5 install question"
date: 2006-04-14
forum: General Help
---

### Post by JimS on 2006-04-14
...

Need to run a viewer that needs Java 1.5.

see [www.dis-danmark.dk/forum/read.php?f=11&i=4290&t=4290](www.dis-danmark.dk/forum/read.php?f=11&i=4290&t=4290)

How do I instill Java 1.5?

JimS

...

---

### Post by oscar on 2006-04-14
See:
[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)
it looks like a java web start program so you need to download the .jwdsp file and:
```
javaws whatever.jwsdp
```
but with the correct name, I dont know how to get firefox to automatically launch it.

---

### Post by testube_babies on 2006-04-14
See this site:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Instructions for installing java are toward the bottom of the page.

---

### Post by JimS on 2006-04-15
...

Thanks for the replys.

Looking in Synaptic Package Manager I find
Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
appears to be installed, I assume by default.
It's file name is sun-j2re1.5.
j2re1.4 and j2re1.4-mozilla-plugin are not installed.

Don't know where to go from here.

[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by hove99 on 2006-04-15
I just followed a HOWTO on this page:
> 
[http://www.ubuntuforums.org/showthread.php?t=76735&highlight=Install+java](http://www.ubuntuforums.org/showthread.php?t=76735&highlight=Install+java)

I haven't had any problems since then, neither in Firefox or any other programs.

Cheers

---

### Post by JimS on 2006-04-15
...

Kære Hove99,

As I mentioned before it appears that sun java 1.5 is already installed.  
The HOW TO appears to be install instructions.
I have folder usr/lib/j2re1.5-sun with lots of subfolders and files.

Will the HOW TO install procedure add proper functionallity?
Do I start at the beginning?

mvh,
[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by oscar on 2006-04-15
If you have that package installed then you do have Sun java, you must have previously installed it, or downloaded someone else's package. Sun java cannot be distributed by ubuntu because of lisencing and copywrite issues (sun java isn't open source).

To make sure that you are using sun java instead of an alternative:
```
 sudo update-alternatives --all
```
and answer the questions, most can remain default but make sure you change all of the java related ones to the sun option.

To check your installation:
```
java -version
```
should show something like:
```
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode)
```

---

### Post by JimS on 2006-04-15
...

Oscar,

Don't when or where I got the sun java.

Did "sudo update-alternatives --all" and got alot of stuff.
Some were java related, but I didn't know how to modify
or if they needed modifying.
I clicked "enter" for all.

"java -version" 
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

So it looks like I'm a bit behind.
Can I update it (for free)?

What to do??

[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by oscar on 2006-04-16
Firstly check if you can actually do what you want to, that is the best way of checking. If you cant then follow the guide several of us linked to:
[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

I don't know why I said "java -version" before, what it should be is:
```
which java
```
I get:
```
/usr/lib/j2re1.5-sun/bin/java
```

---

### Post by JimS on 2006-04-17
...

Oscar,

question  "which java"
answer    "/usr/bin/java

My ISP has been down 24 hours.
Just saw your msg.

Got a msg from Denmark coder.
The coder wrote something Linux Firefox being different from Windows Firefox. 
I don't understand, but will relay it to this forum Monday.
Got to go.  Rushm rush.
I'll be back noon USA Eastern time, I hope.

Thanks again,

[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by JimS on 2006-04-17
...

Programmer (coder) from Arkivalieronline sent me the following:

"First, let me asure you that one of the reasons for writing the LAViewer
in java was it's ability to run on any platform supporting java.
Linux is good for many things, but to my knowledge however,
there is not a standardised way to tell the operating system
(shell, GUI, etc.) which contenttypes (defined by mimetype
or suffix e.g.) are associated with which programs,
hence the user i.e., you, must tell the browser how it's
supposed to handle unknown contenttypes.
There are two problems of which I am aware.
The first is that the Linux version of Firefox does not handle content
by mimetype (as it is supporsed to and actually does on windows)
but rather by suffix, which - due to security considerations - is not jnlp by aspx.
So your task is to tell Firefox that aspx (actually Microsoft ASP,NET)
is to be opened by Javaws (java WebStart)."

Does this make any sense?
What should I do next?
Send this to Bugzilla?

[COLOR="Red"]JimS[/COLOR]

Google Quote for the Day
Before God we are all equally wise - and equally foolish.
  - Albert Einstein

,,,

---

### Post by oscar on 2006-04-18
could you give us a link to the thing you are trying to run so we can try?

---

### Post by JimS on 2006-04-19
...

The link is
[http://www.arkivalieronline.dk/](http://www.arkivalieronline.dk/)

You need to get a password which is emailed to you.

This is a Danish site.
There are directions in English.

The place where it quits is after selecting a church book.
It asks what to open the viewer with, but does not have
a program selected already for this task (as it does in Windows.)

I passed this problem on to [http://forums.mozillazine.org/](http://forums.mozillazine.org/)
No replys as yet.

Good luck,

[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by oscar on 2006-04-19
Ok I found how to do it. I dont think the problem has to do with the file extension, just Firefox doesnt know what to do with it. When you click on the link it brings up the window asking what you want to do with it. It should say something like:
"You have chosen to open ViewImage.aspx which is a: JNLP file from: [http://www.arkivalieronline.dk](http://www.arkivalieronline.dk) What should Firefox do with this file?"
You want to select Open with then click the Box which says "Firefox Web Browser (default)" and select other.
On the left double click File System and then select /usr/lib/j2re1.5-sun/bin/javaws
Now click OK and it should download and run the program.

If you don't have /usr/lib/j2re1.5-sun/bin/javaws then you haven't got java installed correctly.

---

### Post by JimS on 2006-04-19
...

OSCAR,:KS :KS :KS 

YOU ARE THE MAN!!!:p :p 

YOU SOLVED THE PUZZLE.  IT WORKS.:-\" 

MANY THANKS.=D> 

[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by oscar on 2006-04-19
glad you finally got it sorted out

---

