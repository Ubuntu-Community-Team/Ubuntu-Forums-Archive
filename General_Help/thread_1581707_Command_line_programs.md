---
title: "Command line programs"
date: 2010-09-25
forum: General Help
---

### Post by Coco999 on 2010-09-25
How do I find out which command line programs are installed and what do they do?

---

### Post by coldraven on 2010-09-25
Think of a subject that interests you. Say "disc" for example.
Then type 
```
man -k disc
```This will search all the man(ual) pages for the word "disc".
```
jamie@happy32:~$ man -k disc
cdrdao (1)           - reads and writes CDs in disc-at-once mode
ddate (1)            - converts Gregorian dates to Discordian dates
disco (1)            - Mono's Web Service Discovery Tool
Gnome2::VFS::DNSSD (3pm) - network service discovery
hp-probe (1)         - Printer Discovery Utility
HTML::Element::traverse (3pm) - discussion of HTML::Element's traverse method
ldattach (8)         - attach a line discipline to a serial line
morphy (7WN)         - discussion of WordNet's morphological processing
pppoe-discovery (8)  - perform PPPoE discovery
readom (1)           - read or write data Compact Discs
strip (1)            - Discard symbols from object files.
tc-prio (8)          - Priority qdisc
tracepath (8)        - traces path to a network host discovering MTU along this path
tracepath6 (8)       - traces path to a network host discovering MTU along this path
wngroups (7WN)       - discussion of WordNet search code to group similar verb senses
XCloseDisplay (3)    - connect or disconnect to X server
XOpenDisplay (3)     - connect or disconnect to X server

```Then if you are interested in "disco" type "man disco" for the options. Press "q" to quit man.

---

### Post by Lateralis on 2010-09-25
+1 

I did not know that!  *makes a note*

Also, there are many pages on the intersphere which list and detail a huge variety of Linux programs.  [Bash commands]("http://ss64.com/bash/") has a list relevent to the bash shell.  Also in my signature there is a link to page which lists I-don't-know-how-many commands and programs, with all of their man pages.

---

### Post by Coco999 on 2010-09-25
Thank you for your help. To coldraven for a very helpful tip, that will enable me to search for specific subjects. And to Lateralis for the helpful links, although I could not fin the one leading to  "I-don't-know-how-many commands and programs"

As a general comment, the system is extremely powerful, but overwhelming in its size and intricacy. Sure there is an abridged treatment suitable for a starter.

---

### Post by SeijiSensei on 2010-09-25
The "apropos" command is an alias for "man -k".  It might be easier to remember; it is for me :)

Man pages vary greatly in their comprehensibility.  Some of them can be quite overwhelming to new users because they provide long lists of options, associated files, examples, and the like.

For most tasks, you might find it easier to start by searching Google with a few keywords identifying what you want to do.  You'll find that man pages will show up as well; search Google for "man apropos" as an example.

---

### Post by stinkeye on 2010-09-25
You might also be interested in **man2html** which converts man pages to html.
Then you can access them in your browser with a local bookmark link - [http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html)
man2html is in the software centre

---

### Post by Lateralis on 2010-09-26
[http://www.linuxmanpages.com]("http://http://linuxmanpages.com/") is the link in my signature I was refering to Coco. :)

---

### Post by jv2112 on 2010-09-26
dpkg -l

then man "program" for anything you want a real detailed answer on.

---

### Post by Coco999 on 2010-09-26
Thank you for your help. I am tempted to declare the thread as solved, because I have learned a lot of tricks that open many doors to delve deeper into the system, but delve I'll have to. I was expecting to get a list of say 50 or 100 programs with a brief description of what they do. So I'll leave the thread open just in case for a few further days. Anyhow, thank you very much.

---

### Post by SeijiSensei on 2010-09-26
I recommend the "Nutshell" series of books from O'Reilly as a place to start.  [Here]("http://oreilly.com/linux/index.html") are their Linux titles.

---

### Post by oldos2er on 2010-09-26
> **Coco999 said:**
>  I was expecting to get a list of say 50 or 100 programs with a brief description of what they do. 

Overkill, but if you hit Tab twice in terminal, you'll get a list of *every* command. You can then use **info** or **man** to get further help

---

### Post by WorMzy on 2010-09-26
You may also want to check this Wikipaedia article out: [http://en.wikipedia.org/wiki/List_of_Unix_programs](http://en.wikipedia.org/wiki/List_of_Unix_programs)

---

### Post by amauk on 2010-09-26
apropos (or it's alias man -k) is great for common stuff, you can use it to search for broad topics you're interested in, then when something looks promising, use man to get detailed info on a specific program

but apropos won't know about something unless it's installed

for less common things, apropos may not return anything (or not the best solution, at any rate)

You may be better off using apt-cache
```
apt-cache search foo
```

On a default Desktop install, for example, there's nothing installed for configuring software RAID
```
apropos raid
``` will not return anything, however ```
apt-cache search raid
``` will return stuff to do with raid

---

### Post by Coco999 on 2010-09-27
Ann said
> **oldos2er said:**
> Overkill, but if you hit Tab twice in terminal, you'll get a list of *every* command. You can then use **info** or **man** to get further help

Overkill indeed!!! It offered to show me 2922 items and requested confirmation. I said no. I could not even begin to see it. In my opinion, it is necessary to classify them into categories. Yet it is nice to know this trick

---

