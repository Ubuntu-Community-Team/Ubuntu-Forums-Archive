---
title: "problen in runnig a script"
date: 2009-07-02
forum: General Help
---

### Post by mmbathan on 2009-07-02
Hi guys,
 
I have an experiment to test the performance of SSH tunnel
 
I access to the remote host which I have an account in that host (node 1). from node 1 I also ssh to another host which is work successfully.
 
the problem that I face, I have a script which work in my computer but when I want to run it in the remote host it gives me this problem : 
 
[user@east-lin 2x5x20unsock]$ ./multipl.sh 
[COLOR=red]-bash: ./multipl.sh: /bin/bash^M: bad interpreter: No such file or directory[/COLOR]
 
while the file in the folder 
[user@east-lin 2x5x20unsock]$ ls
multipl.sh
 
 
so what do you think the problem .
 
Regards,

---

### Post by asmoore82 on 2009-07-02
at some point, that file has been edited by a DOS text editor.

the "^M" (Control+M) is the code for a Carriage Return(CR) and
only DOS and its descendants demand that each line end with the
Carriage Return and Line Feed(CR+LF) combination.

[http://en.wikipedia.org/wiki/CRLF#History](http://en.wikipedia.org/wiki/CRLF#History)

---

### Post by t0p on 2009-07-02
Is Bash possibly in a different location on the other machine? Like you are telling the script it is at /bin/bash but on the other box it is actually at /usr/bin/bash (or something)?

**EDIT:** Ah yes, the ^M thing. Silly me.

---

### Post by mmbathan on 2009-07-02
thank you guys 
 
yes I change the file format and it is work 
 
dos2unix multipl.sh 
 
 
 
But I have another problem for writing in a script
 
in the remote host node 2 I tried to write in a file but I could not 
 
[user@EAST-02 bin]$ ./iperf -s >> result.log
-bash: aa.log: Permission denied

Also when I need to use the vi editor too as bellow
 
~
~
:wq
"aa.txt" E212: Can't open file for writing
Press ENTER or type command to continue
 
How I can fix this problemdo I need to be a root?
 
thank you again guys

---

### Post by geirha on 2009-07-02
You should learn about how file permissions work. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by mmbathan on 2009-07-02
thank you geirha
 
but what about when I want to create new file using vi Editor
 
~
~
:wq
"aa.txt" E212: Can't open file for writing
Press ENTER or type command to continue

---

### Post by t4thfavor on 2009-07-02
Permissions on that directory will not allow your user to create files. Try another directory, or escalate your privs.

---

