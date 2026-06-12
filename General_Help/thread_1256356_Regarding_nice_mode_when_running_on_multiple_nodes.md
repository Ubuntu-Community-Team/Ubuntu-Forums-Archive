---
title: "Regarding nice mode when running on multiple nodes"
date: 2009-09-02
forum: General Help
---

### Post by Deathfrost on 2009-09-02
Hello all!
How is everyone?
I had a question about nice mode. I am attempting to run a program on multiple nodes on our campus cluster:-

so I type in:-

nice -n 19 myprog

I have a nodelist file set up so that myprog runs on several nodes of my choosing, needless to say everything is running fine, but nice mode is only applied to the instance in the home directory of the cluster where I run the program from. In all other nodes its not running in nice mode. How do I get it to be nice 19 in all nodes?

Thanks

---

### Post by XCan on 2009-09-02
How are the commands sent to the other nodes? It's kind of hard to find a solution with so little information. I guess you will have to start every instance of the distributed processes niced up on every node.

---

### Post by Deathfrost on 2009-09-02
Hmm Im not sure. I know that the program uses rsh to start up on each node.

---

### Post by Deathfrost on 2009-09-02
Goodness this forum moves fast

---

### Post by XCan on 2009-09-03
You're not sure? How are you going to fix it then? If it indeed uses rsh just slam ```
 nice -n19 
``` in front of whatever command is passed to the nodes.

---

### Post by Deathfrost on 2009-09-03
Ok a little more detail might help. 
The program I am running is NAMD, I run it like following:-
nice -n 19 charmrun namd2 +p6 configfile.conf > log.log

+p6 tells namd that I want it to use 6 cores to run, namd by default looks into a nodelist file to get a list of nodes it is allowed to use. Whenever I do this it will only nice the instance that is running on the master node. 

When you say add nice infront of the command that uses rsh, where do I do this? Do I open up the source code of the program and hunt for this? or is there some other way to do it?

Thanks in advance.

---

### Post by XCan on 2009-09-03
I'm not sure how your program is built up. The easiests scenario for you would be if namd2 (I guess) is a simple shell script. If it is, you should be able to edit it using a text editor, isolate the 'rsh' line and add nice -n19 infront of it. But as I said, distributed stuff can be written in a million different ways, so there's no definite answer since I haven't used your program.

---

### Post by Deathfrost on 2009-09-03
Ok I found somethign related to my problem here,
[http://www.lam-mpi.org/MailArchives/lam/2003/05/5975.php](http://www.lam-mpi.org/MailArchives/lam/2003/05/5975.php)

I guess this is becoming less of a regular learn how to use linux problem now.

---

### Post by XCan on 2009-09-03
:) , I hope it'll all work out. :)

---

