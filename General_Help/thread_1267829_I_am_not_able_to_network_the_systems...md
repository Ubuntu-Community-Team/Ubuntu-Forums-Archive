---
title: "I am not able to network the systems.."
date: 2009-09-16
forum: General Help
---

### Post by aprashanth on 2009-09-16
I am having a 2 linux systems,, let mesay it as A and B..
I am able to access from A to B but I am not able to connect from B to A

the command that I am using is ssh abel@10.92.95.11 from A to B..
but when I try the same from B to A. nothing is happening..


Plese help..

---

### Post by jonobr on 2009-09-16
Hello

Im assuming you Can you ping between clients?

To ssh from one to the other you need an ssh server to respond to the connection attempt.

Sounds as if you dont have one.


If yes, then install openssh on one or both machines, and then you should be able to ssh sftp and scp between both machines

---

### Post by aprashanth on 2009-10-16
Ooops sorry I am late.. 
Thanks for the reply.. 

by the way..I got that problem cleared..
I reinstalled the OS again
I feel few necessary packages were not installed..

---

