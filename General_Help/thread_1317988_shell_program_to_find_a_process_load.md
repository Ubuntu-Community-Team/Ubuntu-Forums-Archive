---
title: "shell program to find a process load"
date: 2009-11-07
forum: General Help
---

### Post by ttsdinesh on 2009-11-07
I need to find the CPU load using by a particular process,say for example "java".Also that process's load must be written to a file. i used > TOP command. but it lists all the processes and its load. Is there any way to parse the output or somebody help me with a shell program.

---

### Post by suhana on 2009-11-07
Perhaps looking at the output of:

```
ps aux | head
```and

```
ps aux | grep -i bash
```(where bash is just an example here) will give you a clue.

It's not perfect, but it can provide sufficient information:

For example, CPU% load for a particular process, (in this case I am looking at the firefox process)

```
ps aux | grep firefox | grep -v grep  | awk "{print $3}"
```

What is happening here, is that we are asking the system for all ps information, then just looking for lines containing the relevant process (in this case firefox), removing any line ALSO containing grep, and finally printing the 3rd column.

---

### Post by mo.reina on 2009-11-07
top | grep <process>

ex. to get the load of firefox:

top | grep firefox

not quite sure how to parse the output to a file.

---

### Post by mo.reina on 2009-11-07
here's a script i just wrote:

```
#!/bin/bash

echo -n "Enter file name to be written to: "
read file_name
echo -n "Enter process name: "
read process_name
top -b -n 1 | grep CPU > load.txt
top -b -n 1 | grep $process_name >> load.txt
```

file name is the name of the file you want the output written/parsed to.  process name is obviously the name of the running process.  you'll have to modify the script if you want more than one process to be outputted.

---

### Post by ttsdinesh on 2009-11-07
Thank u Suhana. Let me try ur command and will get u back.

---

### Post by ttsdinesh on 2009-11-07
mo.reina, thank u for ur help.):P

---

### Post by ttsdinesh on 2009-11-07
```
ps aux | grep firefox | grep -v grep  | awk "{print $3}"
```What is happening here, is that we are asking the system for all ps information, then just looking for lines containing the relevant process (in this case firefox), removing any line ALSO containing grep, and finally printing the 3rd column.[/quote]
 I ran this command and got the following o/p:
> dinesh@home:~$ ps aux|grep firefox|grep -v grep|awk "{print $3}"
dinesh    6143  8.4  4.0 132980 40132 ?        Sl   06:12   0:04 /usr/lib/firefox-3.0.3/firefox

But i need to display the load alone. Can u help me further?

---

### Post by ttsdinesh on 2009-11-07
[SIZE=5]**:confused: mo.reina**[/SIZE]
> **mo.reina said:**
> here's a script i just wrote:

```
#!/bin/bash

echo -n "Enter file name to be written to: "
read file_name
echo -n "Enter process name: "
read process_name
top -b -n 1 | grep CPU > load.txt
top -b -n 1 | grep $process_name >> load.txt
```file name is the name of the file you want the output written/parsed to.  process name is obviously the name of the running process.  you'll have to modify the script if you want more than one process to be outputted.

I created a shell program named "cpu.sh" and a text file named "load.txt". i got the following o/p:
> dinesh@home:~$ sh cpu.sh
: not found
load.txtle name to be written to: 
: bad variable name
firefoxrocess name: 
: bad variable nameme
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
dinesh@home:~$ 

I dont know is the bug in ur shell program. Please help me by debugging ur program

---

### Post by mo.reina on 2009-11-07
yeah i forgot to remove the remove the parameters i was using to test it:

```
#!/bin/bash

echo -n "Enter file name to be written to: "
read file_name
echo -n "Enter process name: "
read process_name
top -b -n 1 | grep CPU > **$file_name**
top -b -n 1 | grep $process_name >> **$file_name**
```

there's no need to create the txt file, the script will do it for you.

---

### Post by ttsdinesh on 2009-11-08
[SIZE=5][B]mo.reina
[/B][SIZE=1]thank you for ur help. let me try it and get u back.:)[/SIZE]
[/SIZE]

---

