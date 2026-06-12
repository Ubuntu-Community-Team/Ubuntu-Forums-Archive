---
title: "Understanding the Ubuntu terminal?"
date: 2012-02-20
forum: General Help
---

### Post by bbno3 on 2012-02-20
Ubuntu 11.10

Is there an easy to understand PDF/Book on understanding the basics of the Ubuntu terminal for beginners?

---

### Post by Cheesemill on 2012-02-20
Have you looked at the [Linux Command Line Learning Resources]("http://ubuntuforums.org/showthread.php?t=1909108") thread?

---

### Post by Rallye on 2012-02-20
I was going to bring up 
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

It's definitely a good place to start if you literally know nothing.

---

### Post by roelforg on 2012-02-20
[http://www.faqs.org/docs/abs/HTML/](http://www.faqs.org/docs/abs/HTML/)
is all i have to say

---

### Post by bbno3 on 2012-02-20
So are you saying that the Bash scripting language IS the Terminal language of Linux? Its what iv read in most things if so il have no problem learning it.:o

---

### Post by MIRAAN Baloch on 2012-02-20
Chack these for Understanding!

[Click Here]("https://help.ubuntu.com/community/UsingTheTerminal")

[Click Here]("https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html")

---

### Post by MIRAAN Baloch on 2012-02-20
[B]________________________________________________________


[/B][CENTER][SIZE=3]**Chack these for Understanding!**
[/SIZE]
[SIZE=2][Click Here]("https://help.ubuntu.com/community/UsingTheTerminal")

[Click Here]("https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html")
[/SIZE][/CENTER]


_________________________________________________________________

---

### Post by Cheesemill on 2012-02-20
> **bbno3 said:**
> So are you saying that the Bash scripting language IS the Terminal language of Linux? Its what iv read in most things if so il have no problem learning it.:o

Bash is one of the shells available for Linux, others include zsh and dash although there are many more. The shell is the software layer that lets you interact with the kernel by entering commands.

Ubuntu actually uses dash instead of bash as its default shell (for performance reasons), but as they use the same set of commands then learning bash will let you use the Ubuntu terminal.

---

### Post by Khayyam on 2012-02-20
> **Cheesemill said:**
> [..] The shell is the software layer that lets you interact with the kernel by entering commands.

Well, no. This may be how [wikipedia define it](http://en.wikipedia.org/wiki/Shell_%28computing%29) but they are incorrect. Shells have no "interaction with the kernel", except perhaps in using facilities provided by the kernel.

A shell is in "userland" and the kernel is a bridge between hardware and software. Even facilities such as init, syslog, etc, do not "interact" with the kernel, at least not in any meaningful sense. As far as the kernel is concerned userland is superfluous to its operation, its focus is entirely on initialising the hardware and providing a means with which software can access it.

A shell (in its original *nix sense) is command interpreter, used interactively via a terminal (tty/pts), or non-interactively via the shells progamming language. In essence it is a programable interface capable of gluing together disperate parts of userland into a coherent whole. As other part of the system take on certain functions (daemons to run services and facilities, etc) the shell is a means of controling/configuring their behavior, as well as providing features to access, create, modify, etc, "files" and resources.

"Graphical shells" behave similarly, only the interface is designed to provide a visual representation of "commands", with a trade off made between "visual representation" and "programability".

I'm not sure who wrote that wikipedia entry but I think its quite misleading. Anyhow, I thought it worth clarifying.

best ... khay

---

### Post by Cheesemill on 2012-02-20
I've never read the Wikipedia entry, I was just trying to use layman's terms to make it easy to understand for a beginner.

+1 for the correct explanation :)

---

### Post by Khayyam on 2012-02-20
> **Cheesemill said:**
> I've never read the Wikipedia entry, I was just trying to use layman's terms to make it easy to understand for a beginner. +1 for the correct explanation

I see, I'd thought you probably hadn't, it was mearly mentioned due to the similarity of description.

Now I've re-read it I'm not entirely satisfied with my own attempt at explanation, c'est la vie.

best ... khay

---

