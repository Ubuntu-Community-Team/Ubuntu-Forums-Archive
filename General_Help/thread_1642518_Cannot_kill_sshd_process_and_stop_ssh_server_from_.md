---
title: "Cannot kill sshd process and stop ssh server from automaticall starting"
date: 2010-12-10
forum: General Help
---

### Post by vhg119 on 2010-12-10
I'm running Ubuntu 10.10. I recently installed the open ssh server so that I can sftp stuff.  However, I do not want the server to always be on, only when I manually start it.  So, I did an 'update-rc.d -f ssh remove' and now I don't see any startup scripts in the rcx.d directories any more.  However, when I do a 'ps ax', there is always a '/usr/sbin/sshd' process running.  I try to kill it but it keeps restarting under a different process ID.  How do I disable sshd?

---

### Post by NertSkull on 2010-12-10
you could just use UFW to block the port when you aren't using it, then open the port when you are.

Then nothing comes in or out unless you let it.

and UFW is super simple to use

---

### Post by vhg119 on 2010-12-10
Thanks NS, I suppose that's one way of tackling the problem.  However, I am also curious as to why the process keeps restarting.  I'm not running inetd.  I don't think I have it in any other startup script.

---

### Post by schuerstedt on 2011-05-16
Took me a while, but I wanted to find it out :-).

Its all about upstart!

Have a look at /etc/init/ssh.conf. 

Here is a line which says: respawn

If you comment out this line, upstart will not respawn the process once it is killed. 

#respawn

After that you can use the init scripts again, e.g. /etc/init.d/ssh start 
to start it again.

If you want to prevent that the service is started during boot, simply change the 
start on filesystem
to
start on never
in the /etc/init/ssh.conf
(which I did not test, because I am remoting into my machine and do not want to lock me out ;-)

Remark: you might need to reboot or google how to restart upstart

---

