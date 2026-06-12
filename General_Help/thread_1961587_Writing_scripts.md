---
title: "Writing scripts"
date: 2012-04-19
forum: General Help
---

### Post by theRich on 2012-04-19
I need help with an assignment for my System Administration. Below is the problem:

[FONT=Arial]1)Inactive accounts on a network waste disk space and may become a security risk. [/FONT][FONT=Arial]
Write an administrative script (to be invoked by root or the cron daemon) that checks for and generates a list of user accounts that have not been accessed within the last 60 days.
[/FONT]
[FONT=Arial]
2)Write a script for a multi-user system that checks users' disk usage. If a user surpasses the preset limit (100 MB, for example) in him/her /home/username directory, then the script will automatically send him/her a warning e-mail.
The script will use the du and mail commands.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Tried searching but I am not sure as how yo exactly write the script. Please help me
[/FONT]

---

### Post by sisco311 on 2012-04-19
Sounds like a homework. Don't expect that someone else will do it for you.

Where did you get stuck?

---

### Post by theRich on 2012-04-19
Well for the first part I thought this line would work:
[FONT=Arial]lastlog –b 59 ,  which searches for users who havent logged in for over 59 days 
 not 100% sure

as for the second I only managed to get as far as:
[/FONT]du -sh /home/*

that is suppose to show the disk usage of all /home directories if I'm not mistaken. I don't know if I'm to store it in a variable or text file, and I don't know how to use the control fucntions to find out those who surpass their amount of space. I was thinking using a for..in to read the file but not sure

---

### Post by theRich on 2012-04-19
Also, I'm not sure as to use the 'mail' command well. Haven't had to use it before

---

### Post by CharlesA on 2012-04-19
> **sisco311 said:**
> Sounds like a homework. Don't expect that someone else will do it for you.

Yep.

[http://unixhelp.ed.ac.uk/CGI/man-cgi?mail](http://unixhelp.ed.ac.uk/CGI/man-cgi?mail)

---

### Post by Vaphell on 2012-04-19
while it's possible to work with output of that du command it's much easier to wrap it in for loop and test dirs one by one

```
for d in /some/path/*
do
  echo \$d="$d"
done
```

---

### Post by nok_bvdc on 2012-04-19
I'm guessing you're from UB right?

Well for question #2 it would help if you read [How to keep a detailed audit trail of what’s being done on your Linux systems]("http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html").

As to #1 like CharlesA said [read]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mail") this and additionally [this]("http://ss64.com/bash/du.html") will help.

---

