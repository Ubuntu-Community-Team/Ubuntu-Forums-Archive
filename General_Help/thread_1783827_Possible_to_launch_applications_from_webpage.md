---
title: "Possible to launch applications from webpage?"
date: 2011-06-16
forum: General Help
---

### Post by ojdon on 2011-06-16
Hi there, I'm thinking about making some offline splash page for Ubuntu (Similar to how Jolicloud functions) I'm wondering if it's possible to be able to launch an application (For example, gedit) by clicking a link on the offline webpage?

---

### Post by ojdon on 2011-06-16
Any ideas?

---

### Post by FormatSeize on 2011-06-16
I have an idea, but I'm not very polished when it comes to scripting to know if it will even work. 
 
But my idea would be that you figure out what shell script runs when gedit is called. That would take some searching around (unless you already know where it is), but it's possible. Then, on your webpage, you would need a script that will execute the gedit script. 
 
And all of that depends on how well versed you are in scripting. What are you using to design the page?

---

### Post by pqwoerituytrueiwoq on 2011-06-16
if the web page's server and the client are the same system yes it should be possible
[PHP]<?php
shell_exec("gedit &");
?>[/PHP]
it may be necessary to specify the display
opening gedit with a web page on the client's copmuter (assuming server is not also the client) would be considered a hack (unless you are talking about activeX (IE only) which i consider very unsafe to use)

---

