---
title: "How to make a shutdown script"
date: 2011-07-05
forum: General Help
---

### Post by royalflush5 on 2011-07-05
Hello all, I was wondering if there was a way to create a script that would kill a process (the Folding @ Home one in particular), then shut down my pc. And I was wondering if there was a way to create another script that would set it to a timer, kind of like the shutdown -h command

I'm a noob to all this, so any help is greatly appreciated.

---

### Post by ratcheer on 2011-07-05
I don't completely understand the new system (Upstart), but the old system (init) still works.

Put your kill command in a script in /etc/init.d. Put a symbolic link to it in /etc/rc0.d. The link name must start with the characters Knn where nn is a number between 01 and 99 (depending on when you want the kill to occur). The link should have permissions of 777 and should be owned by root.

For more information see /etc/init.d/README.

Tim

---

### Post by conradin on 2011-07-05
Are you using Boinc? WCG?
```
sudo pkill boinc
```

---

### Post by 98cwitr on 2011-07-05
[http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown](http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown)

> 
To execute a script at shutdown

Put your script in /etc/rc6.d
and make it executable (sudo chmod +x myscript)
Note that: The scripts in this directory are executed in alphabetical order.

The name of your script must begin with K99 to run at the right time. 

---

### Post by royalflush5 on 2011-07-05
> **conradin said:**
> Are you using Boinc? WCG?
```
sudo pkill boinc
```

i was familiar with that, is it possible to put it on a timer?

---

### Post by ?#Yhf%*&amp; on 2011-07-05
I'm not entirely sure how to solve your specific problem, but I can help you make the actual script. To make a script, open a simple text editor (like gedit, the Ubuntu text editor) and type each command as a line.

Once you do that, save it as a .txt file (like script.txt). Then rename the file with a .sh ending (like script.sh). Then, right-click on the file and go to Properties, then Permissions, then click the box next to 'Allow executing file' or something like that.

Whenever you want to run it, simple double-click on the file and click on Run. I hope that helps at all. :)

---

