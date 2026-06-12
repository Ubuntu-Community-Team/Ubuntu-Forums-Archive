---
title: "oracle express 10g  -  its working, but the web interface isnt"
date: 2010-03-05
forum: General Help
---

### Post by bummm on 2010-03-05
I installed Oracle Express 10g on my ubuntu 9.04 machine.

ran   /etc/init.d/oracle-xe configure   (did not change the default port: 8080)

then logged into the webinterface at [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex) & it worked.

Now I wanted to run it from the command line, according to online-guides
I added to my .bashrc file:ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server PATH=$PATH:$ORACLE_HOME/bin export ORACLE_HOME export ORACLE_SID=XE  export PATH

This also worked.  so far so good.

But now I can not log in through the webinterface at [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex),
any suggestions???  (this is my first attempt on trying to install oracle)

---

### Post by Intrepid Ibex on 2010-03-05
So what exactly is your error message when you are trying to login?

---

### Post by bummm on 2010-03-05
Sorry, bad error description on my part.

Failed to Connect.
Firefox can't establish a connection to the server at 127.0.0.1:8080.


 Im running it on my laptop locally.
so I also tried [http://localhost:8080/apex](http://localhost:8080/apex) 

Failed to Connect.
Firefox can't establish a connection to the server at localhost:8080.

hmmm..

---

### Post by Waappu on 2010-03-06
Hi,

You can remove lines you did ad to .bashrc and follow this
[http://ubuntuforums.org/showpost.php?p=7838671&postcount=4](http://ubuntuforums.org/showpost.php?p=7838671&postcount=4)

Logout after you have make changes.
Then try start and stop database
```

sudo /etc/init.d/oracle-xe stop
sudo /etc/init.d/oracle-xe start

```

---

### Post by bummm on 2010-03-12
thank you for your reply,
I followed all those steps, the database is still working beautifully from command line (locally), but the "database homepage" is still not.   I checked with netstat & its still not listening at the ports below after I start the database. any other possible solutions on how I might fix that?  thanx

heres my oracle config file:

# ORACLE_DBENABLED:'true' means to load the Database at system boot.
ORACLE_DBENABLED=false

# LISTENER_PORT: Database listener
LISTENER_PORT=1521

# HTTP_PORT : HTTP port for Oracle Application Express
HTTP_PORT=8080

# Configuration : Check whether configure has been done or not
CONFIGURE_RUN=true

---

### Post by bummm on 2010-03-12
sudo /etc/init.d/oracle-xe force-reload

seems like this might have fixed it, i'll test it a bit & report back later

---

### Post by Sylchat on 2010-12-07
damn I had the same issue, and 'sudo /etc/init.d/oracle-xe force-reload' solved it... ;)

---

### Post by vangop on 2010-12-11
Oracle is soo buggy. I've had all kinds of weird issues, tried to list them here [http://ubuntu-answers.blogspot.com/2010/10/oracle-xe-issues.html]("http://ubuntu-answers.blogspot.com/2010/10/oracle-xe-issues.html")
Hope that helps someone.

---

