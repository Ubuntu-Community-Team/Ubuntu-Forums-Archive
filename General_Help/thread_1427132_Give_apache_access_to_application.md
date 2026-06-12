---
title: "Give apache access to application"
date: 2010-03-11
forum: General Help
---

### Post by mech7 on 2010-03-11
I have installed pdf2swf and on windows it works great.. only now am moving to ubuntu server.. but something like:

exec("pdf2swf -q -t -T 9 -G -p 17 -f scripting.pdf  scripting.swf", $output = array()); 

Gives nothing in return.. I guess it's access rights when I run it from sudo it works. How can I give apache access to pdf2swf ?

---

### Post by Olav on 2010-03-11
> **mech7 said:**
> I have installed pdf2swf and on windows it works great.. only now am moving to ubuntu server.. but something like:

exec("pdf2swf -q -t -T 9 -G -p 17 -f scripting.pdf  scripting.swf", $output = array()); 

Gives nothing in return.. I guess it's access rights when I run it from sudo it works. How can I give apache access to pdf2swf ?

Why run it with sudo? Try it with your normal user. If that works, it should also work with Apache.

As for the PHP call, try specifying the complete path to pdf2swf, like /usr/bin/pdf2swf (or wherever you installed it, only you can know).

If it still does not work, are you running PHP in safe mode? Is exec() disabled in php.ini? I think it is more likely this is a PHP issue than an Ubuntu issue.

---

### Post by mech7 on 2010-03-16
I found out... the application needs to be called without path.. and the files need a full path (in windows they dont need a path)

Everything works good now :popcorn:

---

