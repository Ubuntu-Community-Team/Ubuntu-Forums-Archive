---
title: "Klibido and Stunnel"
date: 2009-10-02
forum: General Help
---

### Post by MonsterDuc on 2009-10-02
I've had klibido and stunnel running fine on my laptop for a while now.  Yesterday I installed Jaunty 904 but having problems getting klibido to connect.

Details:
```
$ grep nntp /etc/services
nntp		119/tcp		readnews untp	# USENET News Transfer Protocol
nntps		563/tcp		snntp		# NNTP over SSL
nntps		563/udp		snntp

```

```
$ more /etc/default/stunnel4 
# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0
```

> $ more /etc/stunnel/stunnel.conf | grep -v "\;"
sslVersion = SSLv3

chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
pid = /stunnel4.pid

socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1

debug = 7
output = /var/log/stunnel4/stunnel.log

client = yes

[nntp]
accept = localhost:119
connect = news-europe.giganews.com:563


Klibido is set to connect to localhost at 119, but I have also tried 563.

See any issues with the setup that I am missing?

---

### Post by MonsterDuc on 2009-10-02
Just a friendly bump :)

---

### Post by MonsterDuc on 2009-10-02
Tried a million things now and still having the same problem... last friendly bump...

---

### Post by MonsterDuc on 2009-10-10
This is getting weirder and weirder...hoping someone might have a suggestion...

I can telnet to localhost 119 and see that I get to giganews:
```
$ telnet localhost 119
Trying ::1...
Connected to localhost.
Escape character is '^]'.
200 News.GigaNews.Com

```

While the telnet session is open I can verify that stunnel redirects to port 563:
```
$ sudo netstat -an -tcp | grep EST
tcp        0      0 192.168.2.110:47660     216.196.109.144:563     ESTABLISHED 11177/stunnel4
```  

But when I try starting klibido from cmd line I get:
```
$ klibido
Database nzb opened
$ Cannot connect
Cannot connect
Cannot connect
Cannot connect
Cannot connect
Cannot connect
Cannot connect
Cannot connect
Cannot connect
Cannot connect
1, 1: Thread::slotRetryTimeout
Resuming thread
Cannot connect
1, 2: Thread::slotRetryTimeout
Resuming thread
Cannot connect
etc, etc
``` 

Any thoughts/suggestions as to why I can telnet to localhost port 119, but klibido can't connect over it?

ANY thoughts appreciated!

---

### Post by nitor on 2009-10-10
Stunnel really is a bitch on ubuntu. I just got it working after three hours of poring all over the internet.

You've got to change enabled to 1 in the init file as well as the default. At that point you'll probably get a connection reset by peer error-- make sure the server you've got in the conf file is correct.

I'll post more if you need help. Ugh, I need a rest.

---

### Post by nitor on 2009-10-11
Oh, and try using port 2000 instead of 119 for the local connection (be sure you set the clients to that as well), and change the SSLv3 in the conf to TSLv1.

And try pam. After all this, it really should work for you.

---

### Post by MonsterDuc on 2009-10-12
Hi, and thanks for your reply!  I was just about to update the message with a final update and saw your post.  My update was going to be that it works with Pam so I'll have to abandon Klibido as I am not making any progress...but now that I saw your post maybe I'll try a bit more as I prefer klibido over pam :)

I changed /etc/stunnel/stunnel.conf to:
```
$ more /etc/stunnel/stunnel.conf | grep sslV
#sslVersion = SSLv3
sslVersion = TSLv1

```

Now getting an error when I start stunnel:

```
$ sudo /etc/init.d/stunnel4 start
Starting SSL tunnels: file /etc/stunnel/stunnel.conf line 11: Incorrect version of SSL protocol

```

Do I need to make any other adjustments/installs for TSLv1 to work?

---

### Post by nitor on 2009-10-12
Yes, it should be TLSv1, not TSLv1. Sorry about that.

I haven't attempted to get it to work in klibido since pam started working, but yes, I do like that interface more too.. so let's see if it can work.

Gah, how to enable debug mode.

---

### Post by MonsterDuc on 2009-10-16
Changing to TLSv1 made stunnel start up correctly at least, but no progress getting connected with Klibido...


Thanks for your help though Nitor!

---

### Post by MonsterDuc on 2009-10-27
No luck getting this to work so I ended up installing 8.04 again.  It magically started working as it should again...

Should someone be aware of this so it can be resolved?  Not sure where to post.

---

### Post by AnotherBrian on 2010-05-06
I did wireshark traces on the loopback interface (is - 127.0.0.1) and the ethenet card (etho).  On the loopback interface, pan sends internet protocol version 6 messages and klibido sends just plain ole intennet protocol messages (version 4?).. For pan, the ethernet interface has a corresponding message for each loopback message.  klibidon has none.   For pan on the loopback, the ip address is 0.0.0.0 and for kllibido is 127.0.0.1 in both to and from fields.   That led me to leaving sslVersion=TLSv1 as suggested above in stunnel.conf but replacine localhost so that 
accept = 127.0.0.1:119

It works.  

Seems like a bug to me in stunnel4.

---

### Post by IcarusR on 2010-08-22
Changing SSLv3 to TLSv1 works for me.

Strange cos I had this working in Intrepid. Did fresh install & it did not work with Klibido, but did with Pan, using intrepid config files. Klibido is same version, development stalled. 
Downgraded Stunnel4 to version used in Intrepid but still did not work with Klibido.

---

