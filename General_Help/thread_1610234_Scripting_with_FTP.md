---
title: "Scripting with FTP"
date: 2010-10-31
forum: General Help
---

### Post by arcticsno on 2010-10-31
I'm trying to run a test running "get" and "put" a number of times to test network speed for various configurations. 

I made the following script:

[INDENT]#!/bin/bash

echo ""Begin test"
cd ftp
ftp XXX.XXX.X.X

echo "Trial 1"
get FILENAME
put FILENAME

echo "Trial 2"
get FILENAME
put FILENAME

bye

echo "Done!"
[/INDENT]

The beginning works fine, and I log into the other machine, but then it doesn't work because once terminal is in the ftp> mode, it won't run the next commands. Should the executable be in the other computer (which is not linux) and be run from there or is there a way to designate the get and put as commands in the ftp> mode?

---

### Post by ragtag on 2010-10-31
You might want to consider using ncftpget or wget instead. 

With these you can define login and what file or folder to get, and even recursive downloads, without needing to echo anything to them afterwards.

p.s. ncftpget is part of ncftp, so "sudo apt-get install nftp" will install it.

---

### Post by arcticsno on 2010-10-31
the echos were just so that I could find the test cases easier. actually getting and putting the files works fine when I manually type the commands. the goal was just to automate the testing. if I said "echo get FILENAME" would that work? 

my target scenario -
output from running the get/put ftp commands for ten trials (ideally with trial numbers)

---

### Post by luvshines on 2010-10-31
To automate FTP transactions(or any other interactive ones), you'll need to take help of 'expect' script

---

### Post by btindie on 2010-10-31
You're trying to run ftp command in the shell which won't work. Take a look at the following on how to [script FTP transfers]("http://www.unix.com/answers-frequently-asked-questions/14020-automate-ftp-scripting-ftp-transfers.html").

In addition take a look at [this]("http://www.unix.com/unix-advanced-expert-users/14417-loops-within-ftp-comands.html") one which allows you to send the commands directly to the ftp process.

---

