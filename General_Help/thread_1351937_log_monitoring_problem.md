---
title: "log monitoring problem"
date: 2009-12-11
forum: General Help
---

### Post by v0nd00 on 2009-12-11
I want to run this command to my log file 

tail -f some-logfile | awk '/some-pattern/'

each command can take out their result individually but when i join together with "|" nothing come out 

I tried this way



1.ping 192.168.0.1 >>test
   This command put the ping result into "test" file without stopping

2.tail -f test | awk '/from/'
 the first part of the command will take out the latest update of the "test" file and second part will take out record that contain "from"

I tried to run each part individually everything work but when i combine with "|" . it doesn't work 

pls tell me if I am wrong

---

### Post by john newbuntu on 2009-12-11
You used the -f command for tail, which infinitely waits and reads whatever is being appended to the file.  Just use tail or other options like -n.

---

