---
title: "Consume stdin continually with Python script"
date: 2009-12-17
forum: General Help
---

### Post by stefanadelbert on 2009-12-17
I want to be able to run each line of a file through a Python script, which I can easily do like this:

```
cat file | script.py
```

But how do I pass each new line that is added to the file into the Python script? This doesn't work:

```
tail -f file | script.py
```

I would like to keep the script consuming stdin if possible. Any ideas?

---

### Post by synapsys on 2009-12-17
```
tail -f file >> script.py
```

? hard to understand your question....

---

### Post by earthpigg on 2009-12-17
> **synapsys said:**
> ```
tail -f file >> script.py
```

? hard to understand your question....

no. he wants to have the data in the text file handed over to the python script, and have said data then removed from the data file (so the same data isn't processed over and over again by his python program).

so he can run the command from time to time and have the data in the text file evaluated/modified/etc by the python program, i assume then have the results of that evaluation outputted somehow, and have the original evaluated data then removed from the text file.

using ">>" would simply wipe the python script and replace it with the contents of the text file.


@op: alas, i cannot help you.

edit: well, maybe... lets see if i am thinking correctly.

```
#!/usr/bin/bash

#feed the contents of file1 into python script, remove the processed data from file1

mv file1 file2 # rename file to file2
cat file2 | script.py # feed file2 into the script
echo >> file1 #create a new, blank, file1
rm file2 # remove the middle-man file
```

---

### Post by stefanadelbert on 2009-12-17
Thanks for the suggestions.

What I'm looking to do is process a file (the input file), line by line, using a Python script. But the input file is created and added to by another process. As the input file changes (e.g. a line is added to it), I would like the Python script to process that new line and print the result to stdout.

If I tail -f the input file, every new line that is added to the file appears on stdout. What I would like to do is grab stdout and feed it into my Python script. So every new line that is added to the intput file is processed by the Python script.

Hope that makes better sense!

---

### Post by synapsys on 2009-12-17
along the lines of earthpigg's idea...

```
tail -f file >> tempfile && cat tempfile | script.py
```

---

### Post by stefanadelbert on 2009-12-17
Thanks for the suggestion, but this also won't work for what I'm after unfortunately. I'll have another go at explaining what I'm after.

Imagine /var/log/syslog which is constantly being added. Imagine that you had a Python script that processed log messages and printed them to stdout in some kind of pretty format.

If I did this:

```
tail -f /var/log/syslog
```

I would see log messages printed to stdout as they were appended to /var/log/syslog in realtime and continuously until tail is stopped.

But let's say that I wanted to rather pass each log message through the Python script so that instead of seeing each log message in its native format, I would see each log message in the pretty format just after it was appended to /var/log/syslog in realtime and continuously.

I'm beginning to think that this might not really be possible without some kludgery.

---

### Post by stefanadelbert on 2009-12-17
I found the answer [here]("http://www.pixelbeat.org/programming/readline/python"). The problem was with my Python script.

The Python script should look something like this:

```
#!/usr/bin/python

import sys

while 1:
        line = sys.stdin.readline()
        if line == '':
                break
        try:
            print pretty_string(line)
        except:
                pass
```

The the script can be called like this (using the example above):

```
tail -f /var/log/syslog | script.py
```

I was using sys.stdin.read* and those buffer the input, which is not what I was after.

---

