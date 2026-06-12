---
title: "commands"
date: 2011-05-09
forum: General Help
---

### Post by rusty_jones on 2011-05-09
Where can I finds Terminal commands for Ubuntu?
 Such as checking what cpu , load , system...etc

---

### Post by ComradeSlice on 2011-05-09
[FONT=Courier New]uptime[/FONT] will get you the load. [FONT=Courier New]uname -a[/FONT] will get you the system name. The rest of your question is too vague.

---

### Post by Lars Noodén on 2011-05-09
There aren't really any *commands*, just a lot of **programs**.  Each one does one thing very well.
 
[list]
[*][top](http://manpages.ubuntu.com/manpages/natty/en/man/top.1.html) will tell you which processes are using the most CPU or RAM.  The sort order of the output can be changed.

[*][df](http://manpages.ubuntu.com/manpages/natty/en/man1/df.1.html) will tell you how much disk space is used.
[/list]

The programs are rather specific so your request must also be specific.  What other information do you want from your system?

---

### Post by rusty_jones on 2011-05-09
I want to find out about my CPU's any and all info

---

### Post by WorMzy on 2011-05-09
Install the lshw package
```
sudo apt-get install lshw
```

then run it like this:

```
sudo lshw > lshw.txt
```

then view the document with
```
less lshw.txt
```

---

### Post by bodhi.zazen on 2011-05-09
cat/proc/cpuinfo

What is "any and all info" ?

---

### Post by rusty_jones on 2011-05-09
Where can i find info about the command you just gave me . 

I don't want to keep asking questions about every command i may need.

---

### Post by WorMzy on 2011-05-09
```
man <command name>
```
or
```
<command name> --help
```

will usually give you information about a command.

If neither of those yield anything
```
info <command name>
```
is your last port of call.

```
man -k <search term>
```

may help you to find commands. It searches through the descriptions of all the man pages you currently have installed and tries to locate the search term for you.

---

### Post by bodhi.zazen on 2011-05-09
> **rusty_jones said:**
> Where can i find info about the command you just gave me . 

I don't want to keep asking questions about every command i may need.

You will learn these things as you use them, but, learning to read the man pages is a useful skill.

You can slow see:

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by Frogs Hair on 2011-05-09
[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by Topsiho on 2011-05-09
You should do a google search on linux commands, there are lots of excellent tutorials which can point you the way. To answer your question would take a lot of time and a lot of typing :)

Topsiho

---

### Post by rusty_jones on 2011-05-09
Thank you one and all. @Frogs hair- thats exactly what i was looking for. THX

---

### Post by AlphaLexman on 2011-05-09
> **rusty_jones said:**
> I want to find out about my CPU's any and all info
Maybe you would enjoy the customization of [http://conky.sourceforge.net/](http://conky.sourceforge.net/) It is in the repo's also.

---

