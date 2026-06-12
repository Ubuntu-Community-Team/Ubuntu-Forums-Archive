---
title: "umask for Particular File Type."
date: 2009-08-01
forum: General Help
---

### Post by lvleph on 2009-08-01
I was wondering if there was a way to set the default permissions to say 777 for all files created of type avi? I have a file server that I would like my other computer users to read write and execute any newly created avi by default.

---

### Post by shaggy999 on 2009-08-01
First of all, you probably don't want to set the execute bit on an avi file. So at worst you would want to set the file chmod 666. Realistically, you probably only want one person able to write to the file as well, so chmod 644 is probably better.

I don't know of a process that works exactly the way you want, but I can think of a couple of things:

1) Find a program that monitors for new files and can run a command when a new file is found. When it's found it executes a bash script that you would write that does something like:

if (file is avi)
  chmod 777 file
endif

2) You could create a bash script that just does something like this:

#!/bin/bash
find . -iname "*.avi" -exec chmod 666 \;
find . -iname "*.exe -exec chmod 700 \;

And then set cron to run that script every 5 minutes.

---

### Post by shaggy999 on 2009-08-01
A quick search of the repository produced 'inoticoming':

Description: trigger actions when files hit an incoming directory
 inoticoming is a daemon to watch a directory with Linux's inotify
 framework and trigger actions once files with specific names are placed
 in there.
 .
 For example it can be used to wait for .changes files uploaded
 into a directory and call reprepro to put them into your repository.

---

### Post by lvleph on 2009-08-01
Nice, because really what I wanted was to have all files in particular directories with proper permissions. I am going to have to check that out.

---

### Post by lvleph on 2009-08-01
I am feeling pretty stupid, because I can't figure out how to use it.

I tried the following

```
inoticoming Downloads chmod 644\;
[\code]
and I get the following error:
[code]inoticoming: Missing ';' at end of action!
(Don't forget to escape it (\;) if you use a shell)
```
The following is the help for inoticoming
```
Syntax: inoticoming [<options>*] <directory to watch> <actions>
where option can be:
	--logfile <file>
	--pid-file <file>
	--foregroundSyntax: inoticoming [<options>*] <directory to watch> <actions>
where option can be:
	--logfile <file>
	--pid-file <file>
	--foreground
	--initialsearch
and each action is [<action-options>*] command [<arguments>] ;
with possible action-options:
	--prefix <string>	only processes filenames starting with string.
	--suffix <string>	only processes filenames ending with string.
	--regexp <regular expression>	... matching the regular expression given.
	--chdir <directory>	change directory before calling action.
	--stdout-to-log		send output to the logfile
	--stderr-to-log		send error output to the logfile
In the arguments {} is replaced by the filename found.
Note the ; at the end of every action. (In a shell, use \; to get ;)

	--initialsearch
and each action is [<action-options>*] command [<arguments>] ;
with possible action-options:
	--prefix <string>	only processes filenames starting with string.
	--suffix <string>	only processes filenames ending with string.
	--regexp <regular expression>	... matching the regular expression given.
	--chdir <directory>	change directory before calling action.
	--stdout-to-log		send output to the logfile
	--stderr-to-log		send error output to the logfile
In the arguments {} is replaced by the filename found.
Note the ; at the end of every action. (In a shell, use \; to get ;)

```
Maybe someone can translate that for me.

---

### Post by lvleph on 2009-08-02
I figured it out. inoticoming needs to know what to apply the command to so
```

inoticoming Downloads chmod 644 {} \;
```

---

