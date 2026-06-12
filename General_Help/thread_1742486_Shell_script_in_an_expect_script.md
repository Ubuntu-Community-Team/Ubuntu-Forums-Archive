---
title: "Shell script in an expect script"
date: 2011-04-28
forum: General Help
---

### Post by duckyq on 2011-04-28
I'm trying to run a expect script that creates a ssh tunnel to mysql server and also executes a script(testingsh with argument root) that connects to mysql and retrieve data from mysql.
 
This is my expect script lol.exp
```
#!/usr/bin/expect -f
set password [lrange $argv 0 0]
set cmds "./testingsh root"
set timeout -1
spawn ssh -f [EMAIL="Administrator@192.123.321.1"]Administrator@192.123.321.1[/EMAIL] -L 6666:localhost:3306 -N
match_max 100000
expect "*?assword:*"
send -- "$password\r"
expect "*\r"
send -- "$cmds\r"
expect eof
```
 
when i run lol.exp all i get is 
```
ubuntu@ubuntu:~$ ./lol.exp password
spawn ssh -f [EMAIL="Administrator@192.123.321.1"]Administrator@192.123.321.1[/EMAIL] -L 6666:localhost:3306 -N
Administrator@192.123.321.1 's password:
ubuntu@ubuntu:~$ 
```
 
When i run a ps -A on my ubuntu there is no ssh process running so i assume the ssh tunnel is closed at the completion of lol.exp script, however immediately after executing lol.exp at ubuntu i switched to mysqldatabase (windows server 2008 ) using cygwin and i did a ps -a i saw 2 processes of sshd so i'm sure the there is nothing wrong with the tunnel. 
 
How do i run a shell script in an expect script? Sorry for the wall of text

---

### Post by duckyq on 2011-04-28
up for help

---

### Post by duckyq on 2011-04-29
up for help

---

### Post by duckyq on 2011-04-29
In desperate need for help with this problem

---

