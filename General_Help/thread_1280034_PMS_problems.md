---
title: "PMS problems"
date: 2009-10-01
forum: General Help
---

### Post by Orbaneqtrx5 on 2009-10-01
I'm just a newbie on linux and have a query regarding PMS (playstation media server)...
If i execute the program ( ./PMS.sh ) from terminal it works fine, but if i try to execute the program manually by double click and run it won't sync with my ps3 and from the debug log the last trace is "[main] TRACE 22:05:13.980 Encoding: UTF-8"

from the terminal i can see that after  "[main] TRACE 22:05:13.980 Encoding: UTF-8" the next trace is "[main] TRACE 22:05:13.986 Temp folder: /tmp/javaps3media"

can anyone help please... 
thanks from before

---

### Post by sancho panza on 2009-10-01
I'm sorry I do not know the answer to your problem, but I'm
surprised you claim to be a newbie given how much you seem to 
already know. Anyways, good luck.

Btw, it might help if you put a moments thought into your post
title if you want anyone to read it ;)

---

### Post by Giblet5 on 2009-10-01
It's possible that PMS.sh is intended to be run from a terminal, or that it does something weird, like try to flush the input on startup. Both tests will fail if that's the case.

Try running it in a terminal like this:
```
./PMS.sh < /dev/null > PMS.sh.log 2>&1
```
Does it still work?

If so, you can just create a launcher that uses that same command string or, you can put that command string in a separate script and run that.

---

### Post by Orbaneqtrx5 on 2009-10-02
> **Giblet5 said:**
> It's possible that PMS.sh is intended to be run from a terminal, or that it does something weird, like try to flush the input on startup. Both tests will fail if that's the case.

Try running it in a terminal like this:
```
./PMS.sh < /dev/null > PMS.sh.log 2>&1
```Does it still work?

If so, you can just create a launcher that uses that same command string or, you can put that command string in a separate script and run that.

First of all thanks for the reply and also sancho panza for the advice about title..... When i did the command you adviced from terminal it worked fine.... so what should i do now ???? and what exactly does the command you gave me instruct the program 2 do ???? 
thanks

---

### Post by Orbaneqtrx5 on 2009-10-02
I just googled those commands and i think i know what it is but someone correct me if i'm wrong pls...... /dev/null means to empty the logs of PMS.sh and if found any errors to log them. Is it correct ??

---

### Post by Giblet5 on 2009-10-02
"<" means redirect input (aka stdin) from something - in this case a device file, /dev/null, which PMS.sh can flush w/o hanging.

">" means redirect standard output (aka stdout) to something - in this case a log file.

"2>&1" means redirect the standard error stream (aka stderr) to the same place as stdout.

The numbers have to do with standard I/O file descriptors and the way that linux starts applications. FD=0 is stdin, FD=1 is stdout, and FD=2 is stderr.

Redirection of I/O is discussed in the man page for bash and other command shells. It is extremely handy to know about redirection because it allows you to use the output from one program as the input to another. And another. And another...

Example:

Lets grab the README file from ftp.x.org and save just the file names in the top-level directory in a separate file:
```
ftp -i -n ftp.x.org << ! | awk '{ print $9 }' > Files.txt 
user anonymous me@here
dir
get README
quit
!
```

"<< !" means redirect stdin from the text below until we see another "!" by itself. The lines after the first one are all passed to the ftp command as it attempts to read commands.

Cool and handy.

---

### Post by Orbaneqtrx5 on 2009-10-02
lol u amazed me with your knowledge and you're very good at explaining... thanks for your patience and time ....

---

### Post by Simian Man on 2009-10-02
Shouldn't this be in the [Ubuntu Women's]("http://ubuntuforums.org/forumdisplay.php?f=76") forum?

---

### Post by jlacroix on 2009-10-02
This is the best thread. Ever.

And let me know how that PMS thing works, I have a PS3 and I am interested.

---

### Post by Orbaneqtrx5 on 2009-10-02
> **jlacroix said:**
> This is the best thread. Ever.

And let me know how that PMS thing works, I have a PS3 and I am interested.

It's working perfect for me now and if you need any help about it just let me know.....

---

### Post by jonobr on 2009-10-02
Im told with PMS problems, taking baths and relaxation techniques works best.
Maybe also a few scented candles?

---

