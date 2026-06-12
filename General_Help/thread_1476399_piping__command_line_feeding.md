---
title: "piping / command line feeding"
date: 2010-05-07
forum: General Help
---

### Post by Yohai on 2010-05-07
Hi all. 

I have a silly problem. I'm using qhull to calculate something for my thesis, and I would love to be able to call qhull from my program without writing to a file and telling qhull to read it. 

normally, qhull can read from the command line and starts executing on ^D. Another possible thing is to do pipe.

How can I do that in my program? 
For example, using Runtime.getRuntime().exec(...) in Java 
or, alternatively, using dos(...) in matlab?

Thanks all,
Yohai

---

### Post by lmarmisa on 2010-05-07
I have no experience with qhull, but the manual says that it reads its data from the standard input:

[http://www.qhull.org/html/index.htm#TOC](http://www.qhull.org/html/index.htm#TOC)

[http://en.wikipedia.org/wiki/Standard_streams](http://en.wikipedia.org/wiki/Standard_streams)

Therefore, qhull seems a standard program of Unix/Linux and it is able to be integrated in scripts (bash scripts) or with other programs written in C language.

So, if you type 

> 
qhull
the input will be read from the keyboard until a CTRL-D character is detected.

Other option is to edit a text file (for example, data.txt) using your preferred text editor (gedit, vi, etc) containing the instructions for qhull.

In this case, you will type:

> 
qhull < data.txt
Pipes are very powerful tools that allow to connect the output streams of a program stdout (or stderr) to the input stream stdin of other program. So, imagine that you write a program (for example, named prepare_data) that writes the text containing the instructions for qhull in its stdout stream.

The command

> 
prepare_data
 will show the output text in your terminal.

The command 

> 
prepare_data > data.txt
  will create a new file named data.txt containing the data for the qhull program.

And finally, the command

> 
 prepare_data | qhull
   will redirect by means of a pipe the stdout of the program prepare_data to the stdin of the qhull program.

You can find a lot of documentation about these topics in Internet or in Unix/Linux documentation. This is only an example:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc3](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc3)

I do not know qhull and probably this program uses other additional parameters. So, consider this message only like a very generic explanation about stdin, stdout, redirection and pipes.

Anyway, I would like that this information could be useful to you.

Best regards,

Luis

---

