---
title: "Squid installation on 10.10 problem"
date: 2010-10-27
forum: General Help
---

### Post by billsambal on 2010-10-27
Hi,

This is my first post on this forum, so as you may guess, I am a relative newbie to Ubuntu, although I have a reasonable working knowledge of linux, etc. Hello all!

I have just performed a clean install of Ubuntu 10.10. After installing samba and and NX server with out any real issues, my latest task was to install the squid proxy server.

I used:

"sudo apt-get install squid"

This appeared to download and install ok. However, if I try to check the status, start or stop squid, I run into a problem. 

When I used:

"/etc/init.d/squid status"

I quickly realised that there is no "squid" in the "/etc/init.d/" directory?? I dont understand why this is not there? Does anybody have any thoughts? The other squid files seem to be present on my disk, but just not anything in the "/etc/init.d" to allow me to execute commands.

A couple of further points:

1) "ps -ef" shows that squid is running but as user "proxy"

2) I have not installed apache2. Do I need this for squid to work? This is suggested by the Ubuntu documentation.

3) Do I need any other downloads for this matter? I did not install the 3rd party stuff when installing Ubuntu.



Thanks very much in advance

---

### Post by SeijiSensei on 2010-10-27
There's an /etc/init.d/squid on my 10.04 Server, but if I query it, it tells to use the "service" command.  Daemons are started by the new "[upstart]("http://upstart.ubuntu.com/")" facility which uses the "service" command rather than having you execute the startup script to start/stop/restart daemons.

```
sudo service squid status
```

You shouldn't need Apache if all you're doing is proxying traffic through Squid.  Nor should you need any third-party software.  

I presume it runs as the "proxy" user for security reasons, so it can't be exploited to gain root.  The same holds true for the Apache webserver which runs as user "www-data".

---

### Post by billsambal on 2010-10-27
Thanks kindly SeijiSensei,

I will try this command shortly and hopefully it will allow me to gain control of my proxy server.



Regards

---

### Post by billsambal on 2010-10-28
Thanks again SeijiSensei,

This command worked as you suggested.

This thread can now be considered closed.

---

### Post by garukun on 2010-11-03
So, I'm not sure why squid 2.7 is not working on 10.10. I opted to install squid3 which works like a charm for me.

---

### Post by fuzzyworbles on 2010-11-03
i've upgraded to 10.10, too, and am at a loss as to why there's no /etc/init.d/squid. i'm guessing this is why squid also fails to start at boot. squid *does *start however with 'start squid' (using upstart or whatever it is)

i've spent so much time perfecting my squid.conf, i'm reluctant to upgrade to squid3

---

### Post by Dzany on 2010-11-24
Is there a way, if I already installed squid 2.7 and it's runnig, to just upgrade it to squid 3? Or I have to uninstall this squid, install squid3 and then configure it from the begining?

---

### Post by hbnf3333 on 2011-01-16
I've upgraded to 10.10, too, and installed SQUID by the commend :
**sudo apt-get install squid**

It seems to be installed correctly .....
But I am totally confused why there's no "squid" file under the directory /etc/init.d/

And that's why I'm not able to Strat or Stop the Squid by the command : 
**sudo /etc/init.d/squid restart**

Am I installing the Squid in UBUNTU 10.10 in VMWare . 

Am I missing something ?

---

