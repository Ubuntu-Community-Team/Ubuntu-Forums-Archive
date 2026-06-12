---
title: "What happens in /proc/ and /sys/ ?"
date: 2009-06-29
forum: General Help
---

### Post by viking_maniac on 2009-06-29
[COLOR=black][FONT=Verdana]Every time I try to search for files or text within files in these folders, the search halts and I get some error messages. I've heard that the /proc/ folder isn't actually a typical file folder but rather a kind of description of the processes running.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]What are these folders and how do they work?[/FONT][/COLOR]

---

### Post by bodhi.zazen on 2009-06-29
Probably because the fiels are owned by root, try your search using sudo.

[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

> /proc

A virtual file system containing information about system resources.  More information about the meaning of the files in proc is obtained by entering the command **man *proc*** in a terminal window.  The file proc.txt discusses the virtual file system in detail.

/sys contains system information.

---

