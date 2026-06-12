---
title: "Startup application problem"
date: 2010-01-09
forum: General Help
---

### Post by mmistroni on 2010-01-09
Hello all,
 i am trying to run my  tomcat 5.5 at startup..
I went to System-->Preferences-->Startup applications and entered
the command to launch my script

/bin/sh /home/marco/apache-tomcat-5.5/bin/catalina.sh run


But when i restart ubuntu, my tomcat does not run and i dont know where
to find the proper logs to see what happened

could anyone help me?

thanks and regards
 marco

---

### Post by michy99 on 2010-01-09
Did you make sure that the script is executable? Does it run ok from the terminal? Do you need to cd to a particular directory before running it?

---

### Post by mmistroni on 2010-01-09
Hello  ,
 thanks for reply

Yes it definitely run from terminal and it is executable.
i even changed ownership to root but it didnt work

the new command is as follows

/usr/bin/perl /home/marco/PerlDevelopment/testperl.pl

i tried a simple perl script that copies file to a directory, and no files wre 

here's permissions

-rwxrwxrwx  1 root  marco  515 2010-01-09 17:19 testperl.pl

I wish i could find why at least why it does not run from logs..

regards
 marco

---

