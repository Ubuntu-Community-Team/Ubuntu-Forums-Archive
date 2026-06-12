---
title: "Memory use - is this normal?"
date: 2010-09-04
forum: General Help
---

### Post by Cyph0n on 2010-09-04
My server is running a basic LAMP configuration with proFTPd. I'm planning on adding Postfix/Dovecot later on as well.

Here's what I get when I run the 'top' command in terminal:

[IMG]http://lulzimg.com/i3/c35384be.png[/IMG]

Is that normal for such a configuration? I also forgot to add that absolutely no one is using it other than me, meaning no visits/page views.

If it isn't normal, which processes do you think I should disable?

Thanks.

Edit: Scroll down for the problem.

---

### Post by sandyd on 2010-09-04
> **Cyph0n said:**
> My server is running a basic LAMP configuration with proFTPd. I'm planning on adding Postfix/Dovecot later on as well.

Here's what I get when I run the 'top' command in terminal:

[IMG]http://lulzimg.com/i3/c35384be.png[/IMG]

Is that normal for such a configuration? I also forgot to add that absolutely no one is using it other than me, meaning no visits/page views.

If it isn't normal, which processes do you think I should disable?

Thanks.
no. that is much too heavy. 
A configuration with apache2, mysql, pureftpd, and php takes 40-60mb ram on most computers, while you are using 398mb (approximate, I was too lazy to divide by 1024)

---

### Post by MooPi on 2010-09-04
Doesn't look out of place

---

### Post by sandyd on 2010-09-04
> **MooPi said:**
> Your computer is fine. Why do you think something is wrong ? From your top display everything looks as it should. Here is my desktop:
thats not a computer, really.
Its a VPS.
so it should be running much much less than we run.

---

### Post by Cyph0n on 2010-09-04
But what I don't understand is why the hell do I have around 6 instances of apache2 running.

Edit: I have a problem now, actually.

I just killed all but one apache2 process. But every time I refresh my webpage, a new process is started.

Why is this happening?

---

### Post by sandyd on 2010-09-04
> **Cyph0n said:**
> But what I don't understand is why the hell do I have around 6 instances of apache2 running.

Edit: I have a problem now, actually.

I just killed all but one apache2 process. But every time I refresh my webpage, a new process is started.

Why is this happening?
ah.
are you using apache prefork (apache2-mpm-prefork) or apache worker (apache2-mpm-worker).
theirs a difference.

---

### Post by Cyph0n on 2010-09-04
How can I find out? All I did was use the command:

sudo apt-get install apache2

---

### Post by Cyph0n on 2010-09-05
I still need help please. I just don't understand why this is happening.

---

### Post by pbrane on 2010-09-05
apache forks about five worker threads to start with, that way there is a quick response to new requests to view your web page. That is normal and you can find it in the apache config file in */etc/apache2/apache2.conf*. If you want to change the behavior of apache you can do it here, but you should make a backup before you change it and then research what you want to change first.

This is from my config file:
```

# prefork MPM                                                                
# StartServers: number of server processes to start                          
# MinSpareServers: minimum number of server processes which are kept spare   
9# MaxSpareServers: maximum number of server processes which are kept spare   
# MaxClients: maximum number of server processes allowed to start            
# MaxRequestsPerChild: maximum number of requests a server process serves    
<IfModule mpm_prefork_module>
    **StartServers          5**
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

```

---

### Post by Cyph0n on 2010-09-05
Thanks for the help. I changed MaxSpareServers to 2 and everything is fine.

---

### Post by The Cog on 2010-09-05
> **Cyph0n said:**
> Is that normal for such a configuration? 

No. You don't have any swap configured.

---

### Post by Cyph0n on 2010-09-05
Crap.. I still can't get the RAM below 200 megabytes. At least 3 instances of apache have to run at the same time, and 2 instances of samba as well.

---

### Post by ppatrick on 2010-10-09
I run into the same thing on my VPS until I decided to go with lighttpd and good bye Apache...
now I have

Lighttpd
ProFTPd
Dovecot (not authorizing yet ;-(  )
Postfix

under 170 MB

---

