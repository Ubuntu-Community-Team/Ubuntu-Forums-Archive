---
title: "Issue with simple shell script"
date: 2011-10-30
forum: General Help
---

### Post by datavirtue on 2011-10-30
I have placed a read command at the end of my shell script but it doesn't run, the other command 'cp' works great but the shell seems to skip the read command. It works great when I type it in directly and execute.

Script:

echo "Scanning /home/seanka/Software for new files, Sending to Hitachi..."
cp -v -R -u Software /media/Hitachi/
read -n1 -p"Press any key to exit..."  <----this isn't executing :(


Thanks for any help.

---

### Post by datavirtue on 2011-11-03
Following a long running tradition I seem to have with myself, I will answer my own question. Let me know if this feels weird to you. 

Following tons of advice I found by searching for a solution you can witness the above command, which works on a command line but utterly fails when run as a script. Below is what you should use instead, or rather it is what I used, and it worked.

read -p "Press ENTER to initiate backups..." key;

The word 'key' is just a variable for the read command to store its output (return), followed by a semicolon.

You will notice some differences from my original post but those are simply a result of me playing around and ultimately ending with what you see now which I posted in this reply. I assume you can use the standard options such as -N and it will work as well.

---

### Post by sisco311 on 2011-11-03
> **datavirtue said:**
> I assume you can use the standard options such as -N and it will work as well.

In scripting, standard usually means POSIX standard: [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)

POSIX specifies only one option (-r) for the read built-in command:
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/read.html#tag_20_109](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/read.html#tag_20_109)

All other options are shell specific. For example, dash's (in Ubuntu, /bin/sh is a symlink to dash) read command has two options -p and -r.  bash's read command has a lot of non-POSIX options, such as -n, -N, -d...

read reads from the standard input. So, if you run your command in bash and *read -n1* is *ignored*, then most likely the output of a command is redirected to STDIN. For example, if you run:
```
while :
do
    read -n1
done< file.name

```

read will read its input from file.name (check out BashFAQ 89 - link in my sig).

If you run your script in dash, then *read -n1* will throw an error, because the read command in dash does not support the -n option.

---

