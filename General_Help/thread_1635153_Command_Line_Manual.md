---
title: "Command Line Manual???"
date: 2010-12-01
forum: General Help
---

### Post by zainlodhi on 2010-12-01
I am absolutely new to Linux/Ubuntu and Command Line. Could anyone please direct me to a Linux Command Line manual or a list of all commands used in Ubuntu Linux terminal?

---

### Post by aeronutt on 2010-12-01
More than just a list of commands...

[http://cdnetworks-us-2.dl.sourceforge.net/project/linuxcommand/TLCL/09.12/TLCL-09.12.pdf](http://cdnetworks-us-2.dl.sourceforge.net/project/linuxcommand/TLCL/09.12/TLCL-09.12.pdf)

---

### Post by WorMzy on 2010-12-01
The commands that can be used from the command line are not static. As you install and remove software, the number of commands you can run from it increases and decreases.

You might want to start here: [http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by rummy77 on 2010-12-01
I've always found [http://www.computerhope.com/unix.htm#04](http://www.computerhope.com/unix.htm#04) helpful.

---

### Post by sikander3786 on 2010-12-01
There might be many suggestion pouring in here :-)

The one I would suggest is a manual from the Terminal itself ;-) i.e, the man pages.

Put man before any command you want to know about e.g,

```
man shutdown
```

```
man apt-get
```

```
man shutdown
```

You'll see detailed documentation on each of them.

---

### Post by tgm4883 on 2010-12-01
Running this in a terminal will give you a complete listing of every command you can run in the terminal. Keep in mind, as said before, that installing or removing programs can add or remove commands that you are able to run

```
ls `echo $PATH | sed 's/:/\ /g'`
```

---

### Post by deserthowler on 2010-12-01
I found several useful Unix books in the public library and in some used book stores.

Earl

---

### Post by oldos2er on 2010-12-01
I like [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by zainlodhi on 2010-12-02
thanks.......

---

### Post by Habitual on 2010-12-02
[http://ss64.com/bash/](http://ss64.com/bash/) and 
[http://www.commandlinefu.com/commands/browse](http://www.commandlinefu.com/commands/browse)

---

### Post by Spyderkid on 2010-12-02
I think you can type info into terminal to give you a bit of information (obviously)
and if you type *man* infront of any command it tells you what it does.

---

