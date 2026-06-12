---
title: "How to script rc.local"
date: 2009-12-29
forum: General Help
---

### Post by joshli on 2009-12-29
Hello. I have been searching for three hours and I finally found out that I have to edit the rc.local file with the command vi rc.local.

[B]But, I want to add lampp to startup at root but I dont even know how to script it.
[/B]
I want to run these two commands:
/opt/lampp/lampp startssl
/opt/lampp/lampp start

Im on Ubuntu 9.10.

Thank you.

---

### Post by Brandon Williams on 2009-12-30
At its simplest, an sh script is just a listing of commands that could otherwise be run on the command line. So the two commands that you listed just need to be added to /etc/rc.local just before the line that says 'exit 0'. In order to ensure that rc.local is run at startup, you should run this command in a terminal: sudo chmod a+x /etc/rc.local

---

### Post by joshli on 2010-01-01
Thanks.

So, I have to chmod it so that it gets run.

Then just pretend it is a command line?

---

### Post by Brandon Williams on 2010-01-03
That's about all there is to scripting at this level, when you want something to be run unconditionally with no variation. When you want to do more complicated things in your scripts, you'll want to start thinking about the task a bit differently.

---

