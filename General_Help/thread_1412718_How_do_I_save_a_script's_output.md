---
title: "How do I save a script's output?"
date: 2010-02-21
forum: General Help
---

### Post by ckuecker on 2010-02-21
Hello,

I have a question about rerouting the output of a Perl script to a log file. I am trying to run the script to build a filesystem for an embedded ARM processor, and I need to get a record of what the script is sending to STDIN. The STDERR output is working fine, but the errors reported lack the detail I need to debug the problem.

A former co-worker gave me a command that did this, but I've lost the scrap of paper it was on, and I no longer have access to his knowledge.

What I run:

./ltib -c

which is supposed to build the filesystem. I tried:

./ltib -c 2>> ltib_log

which puts the normal output into log. 

So, how do I redirect stdin to both the terminal and to the log file?

Thanks in advance,

Chuck Kuecker

---

### Post by MaxIBoy on 2010-02-21
The key here is the "tee" command. This command will both put its input in a file, and then echo the input as output as well. 

If you want to both see the output of *command* and have it go to a *file*, you do
```
command | tee file #puts the results of command in "file" and also echo them to the screen 
```To include stderr as well:
```
command 2>&1 | tee file #2>&1 joins the contents of stderr with stdout and puts the result in stdout
```To log stderr and display everything else:
```
command 2>file #stderr is not displayed, it is put in "file"
```To log stderr and display everything:
```
command 2>(tee file) #stderr is displayed and put in "file." stdout is only displayed.
```

---

### Post by jflaker on 2010-02-21
Use > or >> at the end of your script at the command line..

If your command is MyScript...then it will be
$ ./MyScript > /Path/To/Your/OutputFile/YourOutputFile.txt
or
$ ./MyScript >> /Path/To/Your/OutputFile/YourOutputFile.txt

>/Path/To/Your/OutputFile/YourOutputFile.txt

or

>>/Path/To/Your/OutputFile/YourOutputFile.txt

> will overwrite the output file each time
>> will append to the output file each time

The > or >> pipes the output to the file and nothing will be echoed to the screen.

---

### Post by ckuecker on 2010-02-21
Thanks - those helped a lot. I've got the clues I need, now. :D

Perhaps a dumb question, but where can I look to learn all these neat tricks? I've got a couple of Linux books, but none seem to have this stuff out where it's easily found.

Chuck Kuecker

---

### Post by jamesisin on 2010-02-21
I use this book on BASH:

[http://www.amazon.com/Bash-Cookbook-Solutions-Examples-Cookbooks/dp/0596526784](http://www.amazon.com/Bash-Cookbook-Solutions-Examples-Cookbooks/dp/0596526784)

---

### Post by ckuecker on 2010-02-21
Thanks. Just ordered a copy.

Chuck

---

