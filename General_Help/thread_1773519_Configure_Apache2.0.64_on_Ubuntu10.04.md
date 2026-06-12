---
title: "Configure Apache2.0.64 on Ubuntu10.04"
date: 2011-06-02
forum: General Help
---

### Post by lidengdeng on 2011-06-02
Hi:

I am trying to configure apache2.0.64 on Ubuntu10.04 and get stuck.

Here is my steps:

1) Download apache2.0.64 from its official website and unpack the archive. 

2) Run the commands as shown in its INSTALL file
     $ ./configure --prefix=PREFIX
     $ make
     $ make install
     $ sudo PREFIX/bin/apachectl start

3) Reset the server name in file PREFIX/conf/httpd.conf
      ServerName 127.0.1.1:80

4) Test the sever by browsing [http://localhost/index.html](http://localhost/index.html), [http://localhost/](http://localhost/) [http://127.0.1.1:80](http://127.0.1.1:80)
   All failed with errors:

Forbidden

You don't have permission to access / on this server.
Apache/2.0.64 (Unix) Server at localhost Port 80

So any clue to fix this??

Thanks

---

### Post by cavh on 2011-06-02
A far easier way is simply to run the ```
tasksel 
```command from a terminal prompt. **_Do not_** deselect any of the other options which are currently ticked when doing this.

---

### Post by I'mGeorge on 2011-06-02
I believe you have to start apache httpd daemon, something like

```

sudo /path to daemon/httpd start

```

---

