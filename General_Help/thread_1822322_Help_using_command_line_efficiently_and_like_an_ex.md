---
title: "Help using command line efficiently and like an expert"
date: 2011-08-10
forum: General Help
---

### Post by HunterDX77M on 2011-08-10
I recently started using the command line for the first time and know the bare basics when it comes to commands (ls, cd, etc.). Is there a quick and easy way to get efficient at using the command line?

I'm the kind of person who learns well from examples and from books (that's why I like school). Is there a good place that gives something like command line exercises and solutions? I don't want to limit myself to only Ubuntu command line, but Linux in general.

---

### Post by MG&amp;TL on 2011-08-10
[http://linuxcommand.org/]("http://linuxcommand.org/")

No quick and easy way, but this is the best site I found-goes from basics to shell scripting. :D

And it works, wrote my first shell script the other day. Deals with all linux distributions that use bash (i.e. almost all of them)

---

### Post by Toz on 2011-08-10
The best way to learn is to just do it - throw yourself at it. If you have a spare computer lying around (or you can create a vm in virtualbox) install the server version of ubuntu or debian (or whatever) with no gui. Then configure it to do something (ssh, ftp, samba, http, firewall, etc). You'll quickly learn to be proficient on the command line when there is no gui to turn to.

---

### Post by MG&amp;TL on 2011-08-10
Or that. But there is a temptation to 

```
sudo apt-get install gnome-desktop
```

:D

But I agree, it is an excellent way. Make sure you have access to the internet elsewhere though, in case you need to look something up.

---

### Post by Habitual on 2011-08-10
```
echo "export LESS='FiX'" >> ~/.bashrc
source .bashrc 
```
Then type man bash and scroll a page or 2 then Q for exit.

It stays on the screen.

---

### Post by nothingspecial on 2011-08-10
If you do want to know what you are doing....... :P

Read this

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by whatthefunk on 2011-08-10
Try to find command line solutions for everything.  Dont do anything in the GUI.  For me, this has been the best way to learn.

---

### Post by HunterDX77M on 2011-08-10
> **MG&TL said:**
> [http://linuxcommand.org/]("http://linuxcommand.org/")

No quick and easy way, but this is the best site I found-goes from basics to shell scripting. :D

And it works, wrote my first shell script the other day. Deals with all linux distributions that use bash (i.e. almost all of them)

This is an extremely nooby question, I know (forgive me), but what is the difference between shell scripting, shell programming, and using the command prompt. People seem to use these interchangeably and I can't keep up with which is which. :confused:

---

### Post by Vaphell on 2011-08-10
using command prompt = general concept of running an managing stuff from cli
shell scripting/programming = writing bash/sh/whatever_shell scripts that perform sequences of commands as if they were written in terminal, important skill of pro command line user.

---

### Post by HunterDX77M on 2011-08-10
> **Vaphell said:**
> using command prompt = general concept of running an managing stuff from cli
shell scripting/programming = writing bash/sh/whatever_shell scripts that perform sequences of commands as if they were written in terminal, important skill of pro command line user.

Okay, cool. So I guess scripting is akin to writing a js file if you were a web developer or something. Because, you have that file, you can just include it each time you need it, as opposed to rewriting the entire JavaScript code, right?

---

### Post by HunterDX77M on 2011-08-11
Thanks for all the helpful advice and links, everyone.:)

---

### Post by erind on 2011-08-11
Adding two other useful links.

Bash Guide for Beginners:
[http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf](http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf)

Advanced Bash-Scripting Guide:
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)

---

### Post by MG&amp;TL on 2011-08-11
Good luck! BASH is good to get into. :)

Worth doing, too. A couple of .sh files for everyday tasks will speed things up considerably.

---

### Post by HunterDX77M on 2011-08-14
> **Vaphell said:**
> using command prompt = general concept of running an managing stuff from cli
shell scripting/programming = writing bash/sh/whatever_shell scripts that perform sequences of commands as if they were written in terminal, important skill of pro command line user.

Another stupid question: what is the difference between shell scripting and Bash scripting?

---

