---
title: "how to debug an expect script running on a tomcat server"
date: 2010-11-25
forum: General Help
---

### Post by randeel on 2010-11-25
Hello everyone,

I have a small expect script as follows;
#!/usr/bin/expect -f
set force_conservative 0 ;# set to 1 to force conservative mode even if
;# script wasn't run conservatively originally
if {$force_conservative} {
set send_slow {1 .1}
proc send {ignore arg} {
sleep .1
exp_send -s -- $arg
}
}
set timeout -1
spawn /bin/bash
match_max 100000
send -- "su randeel\r"
expect -exact "su randeel\r
Password: "
send -- "some password\r"
expect "randeel@"
send -- "wine cmd /c wscript Z:\\\\tmp\\\\tomcat6-temp\\\\3fe21de5ca0fe5fb.vbs"
expect -exact "wine cmd /c wscript Z:\\\\tmp\\\\tomcat6-temp\\\\3fe21de5ca0fe5fb.vbs"
send -- "\r"
expect "IRemUnknown_RemRelease"
expect "IRemUnknown_RemRelease"
expect "IRemUnknown_RemRelease"
send -- "\r"
exit
expect eof


when i run this script as another user the above works great!!
But when i invoke the above script from tomcat server(using a java programme to execute the script) as user "tomcat6"
the script doesn't execute fully. How can i debug this issue?
when i issue the command ps -ef; 
I see that tomcat6 user has called the script and the process is running.
i also see the bash command also invoked, also i see "su randeel" command also being running.
But i don't know how to debug this issue. I am new to expect,ubuntu.
Any kind of help would be appreciated.

Thank you,
Randeel.

---

### Post by DaithiF on 2010-11-25
Hi, so you have a tomcat instance calling a java process calling an expect script calling bash calling su calling wine calling cmd calling wscript calling vbs ...

...time to rethink the architecture I think.

what are the vbs scripts actually doing ... I would suggest you implement whatever they are doing in a way native to linux rather than going through hoops with wine / windows scripts.

---

