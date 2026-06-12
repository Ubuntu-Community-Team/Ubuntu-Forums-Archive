---
title: "Can someone fix my bash command(s)"
date: 2009-10-27
forum: General Help
---

### Post by rob86 on 2009-10-27
I'm trying to search for files and perform an action on them. Not surprisingly, during the course of my attempts I found at least 3 different ways to do it.

I have questions about a couple of the ways . It's not just about accomplishing the end goal, it's about understand how to do things multiple ways too.

My first command was like this: 

```
for i in `find / -name '*.avi'`; do echo $i ; done
```

The problem here, is that spaces the for loop delimits by spaces and my command is applied to each word instead of each full path. How can I get it to interpret  one iteration as a full path instead of a word?

My second command was like this:
```
find -name '*.avi'  -exec file {} | grep -i divx \; 

```

This code is supposed to search for files named *.avi, execute the file command on them to output file information including codec, and the "grep -i divx" to filter out ones matching divx .

I know the code above is wrong (with the | grep -i divx added), but I left it in there so it'd be clear what I'm trying to do.

How can I do this the right way? Basically, to do -exec and run one command and pipe into another.



PS: I did manage to write a functional command using xargs, but I still want to learn a bit about the other methods.

---

### Post by Eddward on 2009-10-27
> **rob86 said:**
> 
My second command was like this:
```
find -name '*.avi'  -exec file {} | grep -i divx \; 

```This code is supposed to search for files named *.avi, execute the file command on them to output file information including codec, and the "grep -i divx" to filter out ones matching divx .

I know the code above is wrong (with the | grep -i divx added), but I left it in there so it'd be clear what I'm trying to do.


The way I'd go for the second one is:

```
find -name \*.avi -print0 | xargs -0 file | grep -i divx
```In general I avoid files and directories with whitespace in the name, but when I need to traverse a tree that might have them I always try to turn it into a ```
find -print0 | xargs -0
``` type thing.

Edd

---

### Post by bribera on 2009-10-27
Regarding the second command: You can cut out the grep and thereby cut out all calls to "file" that you don't actually want to see if you use the -iname flag:

```
find -**i**name "***divx***.avi" -exec file {} \;
```

The name filter can do pretty robust regex matching; iname makes it case-insensitive.

---

### Post by bribera on 2009-10-27
Of course, after I posted that I realized that you're looking to filter by codec, not by file name. *facepalm*

Hopefully the post will still retain its own instructive value ;)

---

### Post by major.stubble on 2009-10-27
> **rob86 said:**
> My second command was like this:
```
find -name '*.avi'  -exec file {} | grep -i divx \; 

```This code is supposed to search for files named *.avi, execute the file command on them to output file information including codec, and the "grep -i divx" to filter out ones matching divx .

I know the code above is wrong (with the | grep -i divx added), but I left it in there so it'd be clear what I'm trying to do.

Find can be a little painful to master some times, so don't feel discouraged.

The difficult thing to remember with the -exec parameter is that the first word following -exec must be the command to execute.  It will spawn everything after -exec as a single command, where everything following that command is considered a parameter to that command until it finds an escaped semi-colon **with one very important distinction**: the shell in which find is running takes precedence over any special characters.

From example:

    find -name '*.avi'  -exec file {} | grep -i divx \;

When you execute this command, the shell sees the pipe ("|") and assumes that this is the end of one command and that all output from that command should be passed to the second command.  Effectively:

command 1:  find -name '*.avi'  -exec file {}
command 2:  grep -i divx "output from command 1"

The problem is that find errors out.  It's still looking for the "\;" to end the -exec parameter.  So it says, "missing argument to `-exec'" and doesn't output anything for grep to search.  

(Note:  This isn't quite true.  If you have learned about "standard out" and "standard error", you know that the find command actually outputs it's error to "standard error" and nothing to "standard out".  The grep command is waiting for input from "standard out".  You will actually get and error from grep saying, ";: No such file or directory" because you escaped the semi-colon, so grep thinks that's a file.  Ignore this note for now if you haven't been introduces to "standard error" and "standard out".)

So, if you were like me, you are probably thinking, "Why not escape the pipe then?"  You could, but you will not get the intended result.  By escaping the pipe, find will pass that to file as an argument.  The file command will think this is a file name then and say it can't open it.

There are two (and a half) possible solutions to your second command, and I will attempt to explain both.

The first:
```
find / -name \*.avi -exec file '{}' \; | grep -i divx
```The difference from your example is that the list of files matching the search criteria is generated first, then the entire output is passed to grep.  

The second:
```
find / -name \*.avi -exec sh -c "file '{}' | grep -i divx" \;
```This command will actually do exactly what you wanted originally.  It will find files with the .avi extention, get the MIME info using the file command, and pipe that one file's name to grep.  The reason this works is the comand that -exec is running is 'sh'.

Basically, it is spawning a new shell to execute everything between the double quotes following the -c.  Here, your parent shell (probably bash) sees the first double quote and realizes that this is still a part of the first command.  Find doesn't interpret the -c as one of its own arguments because it's still waiting for the escaped semi-colon.  So, it sees everything following -exec as arguments to the command it will run (in this case 'sh').

This brings us to the 'and a half' part.

```
find / -name \*.avi -exec *custom_script.sh* '{}' \;
```This is probably the most robust solution.  Here the special variable *$@* is replaced with the file name stored in {}.  This is important, as this is also the solution to your first question.

You can create a custom script that does all sorts of wonderful things to *$@*.

```
#!/bin/bash

FILENAME=$@;

/bin/file "$FILENAME" | /bin/grep -i divx
if [[ $? -eq 0 ]]; then
   #Add to a playlist file.
   echo "$FILENAME" >> ${HOME}/Videos/divx_movies.txt
   
  #Convert the divx file to xvid
  /usr/local/bin/mencoder "$FILENAME" -oac mp3lame -lameopts cbr:mode=2:br=96 -af resample=44100 -srate 44100 -ofps 20 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=300 -vf scale=320:240 -ffourcc XVID -o ${FILENAME%%.avi}-xvid.avi

  #Send an email to notify that this file has been converted.
  echo "Finished converting $FILENAME to xvid." | /usr/bin/mailx -s "mencoder process done" you@some_domain.tld
fi;

```The key here is that the file name, spaces and all, is quoted.  To commands like file, grep, mencoder, quoted arguments are treated as a single argument.  Without the double quotes, spaces are interpreted as a delineator between arguments.

---

