---
title: "security issues with www-data in sudoers file?"
date: 2010-02-03
forum: General Help
---

### Post by artheus on 2010-02-03
Hey!

I'm in need of using sudo command in php shell_exec(); And so I put the www-data user in to the sudoers file. With NOPASSWD privileges.

What are the security issues with this?

Cheers,
Artheus

---

### Post by Olav on 2010-02-03
If a malicious script is uploaded to your web server and gets executed, you can see the security risks... It can happen if for instance you are using some wiki, cms, gallery or other web application that has security issues itself.

I can see why you would want the sudo functionality sometimes. Better to restrict it to only the commands that you actually use in your own scripts.

E.g. in /etc/sudoers (visudo):

```
www-data localhost=nopasswd: /usr/bin/convert, /bin/netstat
```

---

### Post by artheus on 2010-02-03
Ah alright...
Am I supposed to put that into the sudoers file then?

//Artheus

---

### Post by Lars Noodén on 2010-02-03
> **artheus said:**
> Hey!

I'm in need of using sudo command in php shell_exec(); And so I put the www-data user in to the sudoers file. With NOPASSWD privileges.

What are the security issues with this?

Cheers,
Artheus

I can't tell if you're joking or not, but that gives full root access to anything your web server can run.  In other words it is potentially giving full root access to your machine to any web vistor who cares to poke around a little.  

www-data should not be in /etc/sudoers

If you want to create a group for web work, then make a new group and use that.  

Can you be very specific about what program you are trying to run in php shell_exec() ?   It is likely that there is another way, or at worst a way to make a very specific sudoers formula so as to minimize the risk.

---

### Post by Olav on 2010-02-03
Yes, but it was just an example I made up. For those two utilities (convert and netstat) you would not need sudo to execute them. But Lars is right, there are probably other ways to achieve what you want. So if you could tell us what you need to do perhaps we can help.

---

### Post by artheus on 2010-02-03
Ofcourse I realise that there are security flaws in using www-data as super user. But I'm just curious on which those flaws are.. And sure I would like to use www-data to restart some services on the server.

What I don't really get, is how people could just starting to use www-data to make changes to my server from the outside. Do you mean through ssh? Or where are those flaws?

Cheers,
Artheus

---

### Post by Lars Noodén on 2010-02-03
There are two concepts to look up elsewhere:  Least privilege, Privilege separation.

The web server Apache2 runs as user **www-data** by default and in group **www-data** by default.  Since we're talking about groups, we can ignore the user. 

Access and other permissions are traditionally granted to groups.  It scales better.  

So by giving root access to the group www-data, any user in the group www-data can run programs as root, read files and directories as root, or write files, etc.

Since the web server runs as the group www-data, it can then run anything as root.  Basically the built-in privilege separation is defeated.  Any script or module, then will run with root privileges (via being a member of the group www-data, which has root privileges) and any misconfiguration, oversight, misfeature, bug or hole that exists will also have root access. 

Debian and derivatives might be better off renaming www-data to _www-data or something like that to remind folks that it is for the daemon to use.

---

### Post by Lars Noodén on 2010-02-03
Why do you say you are in need of running something in php shell_exec() as root?  Say what is it you want to run and we can find a safer way.

---

### Post by artheus on 2010-02-03
Well.. I'm working for a small company.. And my boss wants to be able to restart some services like apache2, openvpn, mysql, samba.. you name it.. And get some status reports and stuff like that. Just by clicking a link in the intranet (which is on the same server as the companies webpages).

Thanks,
Artheus

---

### Post by Lars Noodén on 2010-02-04
> **artheus said:**
> Well.. I'm working for a small company.. And my boss wants to be able to restart some services like apache2, openvpn, mysql, samba.. you name it.. And get some status reports and stuff like that. Just by clicking a link in the intranet (which is on the same server as the companies webpages).


Ok.  FWIW, if Apache is your web server and it is down or does not come back up from a restart (say no space left on the disk), then the links won't work.  That's why I always go on about shell scripting skills.  If you have a graphical sftp client you can later try to set up something similar to your web tools.  


Here are some other ideas:

For the "Intranet" that would be [HTTPS](http://httpd.apache.org/docs/2.2/ssl/) + password.  You should be able to dig up an [Apache authentication module](http://httpd.apache.org/docs/2.2/howto/auth.html) that allows authentication to your Samba or Kerberos servers.  

On the system side of things, create a special group for the restart/stop/start activities.  [Use SUexec to use that group](http://httpd.apache.org/docs/2.2/suexec.html) for your special scripts.  

In /etc/sudoers, write out the *exact* strings to be used to start or stop or anything else that must be done:

```

# /etc/sudoers
%assistants  ALL=(ALL) NOPASSWD: \
             /etc/init.d/mysql start, /etc/init.d/mysql restart,  \
             /etc/init.d/mysql stop 

%assistants  ALL=(ALL) NOPASSWD: \
             /etc/init.d/samba start, /etc/init.d/samba restart,  \
             /etc/init.d/samba stop 

```

Then in the web script, which is behind https and a password, you can have links with pulldown menus.  Since what you are doing can probably be expressed as multiple choice pulldown menus, please don't pass any data from the web form to the system.  

For your scripts, PHP might have caught up with perl and the other scripting language and added a [taint mode](http://www252.pair.com/comdog/mastering_perl/Chapters/03.taint-checking.html).  Use that, but again, don't pass any variable on to the system if there is conceivable a way to avoid it.  

That should do it.

If you want to add two factor authentication, (ie. single-use passwords like the bank has, in addition to your regular authentication) then after everything above is working the way you like it, look at things like [libpam-opie](http://packages.ubuntu.com/karmic/libpam-opie) or [donkey](http://packages.ubuntu.com/karmic/donkey).  The place for that would be in using sudo, but I'm not sure offhand how to do that with PHP.

---

