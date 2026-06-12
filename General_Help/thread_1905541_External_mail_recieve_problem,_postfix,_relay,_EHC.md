---
title: "External mail recieve problem, postfix, relay, EHCP hosting software"
date: 2012-01-07
forum: General Help
---

### Post by klavslund on 2012-01-07
Hello experts,

I have a problem receiving email from the outside on my Ubuntu server using postfix. I have tried to follow infrmation found in other threads without finding the solution. I do believe though that it must be something in the DNS/MX setup behaviour. I truely hope on my behalf (and many others as it seems) to get the last bit of information here.

When this is done I will share a step-by-step guide to people on my findings and methods in disclosing this type/example of problems with mail.

Cheers Klavs

General setup

Private server at home, hosting 9 private domains
I am using a public DNS service provider where I can enter/edit DNS records for all the domains, (A, NS, MX records)
WAN has fixed IP-address
From my router NAT routes from WAN to internal 192.168.x.x address where homeserver is located

Server setup

Homerserver hostname = HomeServer.sitenet.dk
OS: Ubuntu 11.04
EHCP hosting panel installed with postfix and squirrel, roundcube clients


Test scenarios done

Domain:
Test content put in some of the domains to ensure correct routing --> works as expected

Mail Inside Out:
Create email user for one of the domains --> Use webmail client to send mail to external (gmail) address --> Success
Reply to sent mail --> Error = Relay access denied (state 14).

Mail Inside loop:
Send mail from user to self using webmail client --> Success
Autoreply from self --> Success

Telnet on WAN address
Ports 25, 110, 587 replies from this address

Mail using Telnet on WAN address:
Send mail directly using Telnet on port(s) is received conrrectly
internally (using telnet smtp example)
Autoreply to external --> Success

Log files:
/var/log/syslog does not show any trace when sending from outside

/var/log/mail.log
Some of these occur in the log file

Jan 7 10:39:02 HomeServer postfix/error[5465]: 2CC1538A08C7:
to=<root@HomeServer.sitenet.dk>, orig_to=<root>, relay=none,
delay=0.39, delays=0.26/0.02/0/0.12, dsn=4.4.2, status=deferred
(delivery temporarily suspended: lost connection with
HomeServer.sitenet.dk[90.185.130.214] while receiving the initial
server greeting)

My deductions
So far based on the above it seems that system actually works when I can 'poke' a mail using telnet directly from out-side. I am not sure about the relay denied though. I guess that MX records could be a problem either at my external DNS provider or internally in EHCP.

Additional info:

Dig mx and dns from outside:

Name Type IP address Class TTL
sitenet.dk  MX  backup-mx.post.tele.dk  IN  37139
sitenet.dk  MX  mail.sitenet.dk  IN  37139
sitenet.dk  NS  ns5.gratisdns.dk   IN  37139
sitenet.dk  NS  ns1.gratisdns.dk  IN  37139
sitenet.dk  NS  ns2.gratisdns.dk  IN  37139
sitenet.dk  NS  ns3.gratisdns.dk  IN  37139
sitenet.dk  NS  ns4.gratisdns.dk  IN  37139
I have removed the backup mx now - it was a previous ISP record. None
of the other domains have this - example:

From my DNS provider on skovgaardlund.dk

MX (@Vært -> A record mailserver)
Vært  Mail udveksler   Præference   TTL   Ændring
skovgaardlund.dk   mail.skovgaardlund.dk 1043200

External dig on domain skovgaardlund.dk

Name Type IP address Class TTL
skovgaardlund.dk  MX  skovgaardlund.dk  IN  37055
skovgaardlund.dk  NS  ns3.gratisdns.dk  IN  37055
skovgaardlund.dk  NS  ns1.gratisdns.dk  IN  37055
skovgaardlund.dk  NS  ns2.gratisdns.dk  IN  37055
skovgaardlund.dk  NS  ns5.gratisdns.dk  IN  37055
skovgaardlund.dk  NS  ns4.gratisdns.dk  IN  37055

From EHCP - DNS information:

$TTL    86400
@       IN      SOA     ns.skovgaardlund.dk. {dnsemail} (
                        {serial}     ; Serial, this is [www.ehcp.net](www.ehcp.net)
dns zone template file..
                        10800   ; Refresh
                        1200     ; Retry
                        86400  ; Expire
                        86400 ) ; Minimum

skovgaardlund.dk.           IN NS   ns.skovgaardlund.dk.
ns.skovgaardlund.dk.        IN A    {dnsip}
ns1.skovgaardlund.dk.       IN A    {dnsip}
ns2.skovgaardlund.dk.       IN A    {dnsip}
dns.skovgaardlund.dk.       IN A    {dnsip}
dns1.skovgaardlund.dk.       IN A    {dnsip}
dns2.skovgaardlund.dk.       IN A    {dnsip}
skovgaardlund.dk.           IN A    {webip}
mail.skovgaardlund.dk.      IN A    {mailip}
smtp.skovgaardlund.dk.   IN A    {webip}
imap.skovgaardlund.dk.   IN A    {webip}
webmail.skovgaardlund.dk.   IN A    {webip}
ftp.skovgaardlund.dk.       IN CNAME        skovgaardlund.dk.
[www.skovgaardlund.dk](www.skovgaardlund.dk).       IN CNAME        skovgaardlund.dk.
skovgaardlund.dk.           IN MX  10 mail.skovgaardlund.dk.
skovgaardlund.dk.           IN TXT "v=spf1 a mx"

{customdns}

*                       IN A    {webip}


Telnet from skovgaardlund.dk

EHLO SKOVGAARDLUND.DK
250 - HomeServer
250 - PIPELINING
250 - SIZE 102414000
250 - VRFY
250 - ETRN
250 - STARTTLS
250 - AUTH PLAIN LOGIN
250 - AUTH=PLAIN LOGIN
250 - ENHANCEDSTATUSCODES
250 - 8BITMIME
250 - DSN

---

### Post by galvatron408 on 2012-01-07
I'd love to help you with this. I need to know the following...

What is a valid email address that I can try sending e-mail to?
What do you think your mx record is?

So, far, I tried to telnet to your mail.sitenet.dk and instead of getting a mail server, I got an SSH server. 

telnet mail.sitenet.dk 25
Trying 90.185.130.214...
Connected to mail.sitenet.dk.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3

---

### Post by klavslund on 2012-01-08
Hi Galvatron,

Thanks for your answer. Already now I have learned something. I wrongly assumed that an answer on telnet 25 was a reply from a mail-listener.

I recreated an external telnet connection on what I set up as external MX records. As an example I tried on ports 25 and 587

telnet on sitenet.dk, mail.sitenet.dk, borneby.dk, mail.borneby.dk

port 25 --> As you discovered an SSH server replies
port 587 --> 220 HomeServer ESMTP Postfix powered by Easy Hosting Control Panel (ehcp) on Ubuntu, [www.ehcp.net](www.ehcp.net)

I also tried port 143 to see if imap replied and this was the response:
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2010 Double Precision, Inc.  See COPYING for distribution information.


Based on this I assume that the MX records setup at the external DNS provider are correct (?)

SSH is wronly listening on port 25 - not sure on how to correct this. This looks like a tunnel that has been set up and must be cleared for SSH and enabled for my EHCP control panel (Postfix)

Are there any other steps that can be processed to clairify? 

Cheers Klavs

---

### Post by lisati on 2012-01-08
SSH usually listens on ports 21 or 22. You might want to re-check your settings for OpenSSH otherwise Postfix might not hear anything.

---

### Post by klavslund on 2012-01-08
Hi Lisati,

Thanks for joining in. I checked the ssh server using this command:

ss -lnp | grep sshd
0  128       :::22      :::*      users:(("sshd",1454,4))
0  128        *:22       *:*      users:(("sshd",1454,3))

According to this it only listens on port 22

Local connection tried using command: ssh -v localhost (See result later in mail - but as expected according to what I have read)

Finally I looked into /etc/ssh/sshd_config which only states port 22

Is is correct to assume that everything regarding this setup is correct - and that the reply on telnet 25 is related to something else?

Cheers Klavs

Answer from local ssh connection


ssh -v localhost

OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: SELinux support disabled
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: Server host key: ECDSA <key>
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is <fingerprint>
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (ECDSA) to the list
 of known hosts.
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Next authentication method: password
root@localhost's password:
debug1: Authentication succeeded (password).
Authenticated to localhost ([127.0.0.1]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = da_DK.UTF-8
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-13-generic x86_64)


debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY

---

### Post by klavslund on 2012-01-08
Hi all,

Just discovered that a request using telnet 25 on localhost actually replies correctly (?) via postfix/ehcp.

telnet localhost 25 -->
220 HomeServer ESMTP Postfix powered by Easy Hosting Control Panel (ehcp) on Ubuntu, [www.ehcp.net](www.ehcp.net)

Cheers Klavs

---

### Post by galvatron408 on 2012-01-08
first of all, don't test localhost. if you want to test, then test your eth interfaces (i.e. eth0 and eth1)
even if a daemon is listening to localhost, it may not be listening to eth0 or eth1.

anyway, what is your mx record and what is a valid e-mail address I can try to send e-mail to. It doesn't have to be real but it has to be valid. why don't you setup a test account and I can try that.

don't worry, i'm a professional e-mail consultant of 10 years. I get paid a lot of money to do this for big companies but I also help our community too.

---

### Post by klavslund on 2012-01-08
Hi again galvaston,

Thanks. I only tested internal to rule out general problems, and I discovered that internally port 25 was assigend to postfix correctly (?)

You can use mx = mail.sitenet.dk
Account = [email]admin@sitenet.dk[/email]

Cheers Klavs

---

### Post by galvatron408 on 2012-01-08
so, based on the answers to my question...

1) your mx record appears to be correct.
nslookup
> set q=mx
> sitenet.dk
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
sitenet.dk	mail exchanger = 10 mail.sitenet.dk.

2) checkiing port 25 on that address, reveals an OpenSSH server. Connecting to it reveals...
RSA key fingerprint is cd:66:09:23:3c:a7:ed:e1:a2:f7:39:b3:c2:36:32:1a.

You claim that you checked and you are positive that openssh is not listening on 25 and that postfix is listening on 25. But you only checked localhost and that doesn't tell you anything useful. you need to test eth0 or eth1 (whichever one is the correct interface). run /sbin/ifconfig to see what it tells you. so, for example, my eth0 reports 192.168.0.105; so then, I would do.... telnet 192.168.0.105 25.

or since you have root access to the machine, maybe you should just run netstat (i.e. netstat -a -n -p tcp -b)

netstat will tell you definitively what is listening to port 25. Remember, testing localhost is useless because localhost is 127.0.0.1. Think about it like this. You are on the machine and you tested localhost and it works great. You hop on to a remote machine.... How will the remote machine connect to your machine's localhost? It can't.

If after you've definitevly determined that postfix is indeed listening on port 25, then it's a routing issue. That's networking. For example, when someone connects to mail.sitenet.dk:25, the switch/router routes this to your machine on port 22. (i.e. gmail --->mail.sitenet.dk:25 *router*----> yourmachine:22)

---

### Post by klavslund on 2012-01-08
Hi Galvaston,

Truely appreciate your help. This is what came out of running your examples.

Using ifconfig to ensure fixed ip = 192.168.1.30

Running telnet 192.168.1.30 25 answered

root@HomeServer:~# telnet 192.168.1.30 25
Trying 192.168.1.30...
Connected to 192.168.1.30.
Escape character is '^]'.
220 HomeServer.sitenet.dk ESMTP Postfix powered by Easy Hosting Control Panel (ehcp) on Ubuntu

Also ran this from other machine on same internal network with the same result.

I ran --> netstat -nap | grep 'tcp' -b  with the following result:


151:tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      22787/vsftpd
248:tcp        0      0 192.168.1.30:53         0.0.0.0:*               LISTEN      15718/named
345:tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      15718/named
---> 442:tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1454/sshd
539:tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1060/cupsd
--->636:tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      22890/master
733:tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      15718/named
830:tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      706/smbd
927:tcp        0      0 127.0.0.1:10023         0.0.0.0:*               LISTEN      14196/postgrey.pid
1027:tcp        0      0 127.0.0.1:9000          0.0.0.0:*               LISTEN      12544/main.conf)
1124:tcp        0      0 192.168.1.30:5001       0.0.0.0:*               LISTEN      25376/java
1221:tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      15838/mysqld
--->1318:tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      22890/master
1415:tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      706/smbd
1512:tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      25374/vino-server
1610:tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      5597/apache2
1707:tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1192/perl
--->1804:tcp        0      0 192.168.1.30:22         131.165.77.52:49649     ESTABLISHED 14692/sshd: [accept
1904:tcp        0      0 192.168.1.30:59906      192.168.1.5:139         ESTABLISHED -
2001:tcp        0      0 192.168.1.30:59904      192.168.1.5:139         ESTABLISHED -
--->2098:tcp        0     52 192.168.1.30:22         192.168.1.110:50191     ESTABLISHED 14255/0
2195:tcp        0      0 192.168.1.30:59905      192.168.1.5:139         ESTABLISHED -
2292:tcp6       0      0 :::53                   :::*                    LISTEN      15718/named
--->2389:tcp6       0      0 :::22                   :::*                    LISTEN      1454/sshd
2486:tcp6       0      0 ::1:631                 :::*                    LISTEN      1060/cupsd
2583:tcp6       0      0 ::1:953                 :::*                    LISTEN      15718/named
2680:tcp6       0      0 :::993                  :::*                    LISTEN      22432/couriertcpd
2778:tcp6       0      0 :::995                  :::*                    LISTEN      22462/couriertcpd
2876:tcp6       0      0 :::5900                 :::*                    LISTEN      25374/vino-server
2974:tcp6       0      0 :::110                  :::*                    LISTEN      22444/couriertcpd
3072:tcp6       0      0 :::143                  :::*                    LISTEN      22414/couriertcpd
root@HomeServer:~#


Tried to highlight ---> ports of interest

I only intreped port 22 assigned to ssh

Port 587 - I have assigned using 'submission'. This port answers with postfix both from WAN and LAN side

On my DSL router I only have one NAT route which defines a 'default server' which is the same IP - 192.168.1.30. I assume (?) the route works since any of the virtual domains show up when I enter them in a browser from the outside. 

Cheers Klavs

---

### Post by klavslund on 2012-01-08
Hello again,

Found what can be called a workaround just now. It seemed that the problem was narrowed down to somewhere between WAN and LAN - or it may have something to do with the submission port in postfix. The latter have to be confirmed.

My WAN router is set up to route all calls on any open port to my homeserver as per default. During this process I tried to manually alter this route by setting specific rules for port 25. Inbound on port 25 had to go to homeserver port 25. None of this had the result expected on port 25. The route was still 'replied' to the outside as SSH server on port 22.

While I was speculating on this I tried to figure out how to reassign a port from one to another. In my router port forwarding was not obvious. It looked as if it expected a port range that would be sent to a given ip.

Just for the possibility I tried to imagine that if it worked as I expected I would have a source and destination port and an IP address. What the system showed me was a start and an end port and an IP address.

I took the chance that it was a 'bad' translation - and it paid out. I made a port forward on incoming on port 25 and redirect to port 587. Telnet on the outside now responds on port 25 as well and mails can be sent/received as for the first testing shows.

This is not the right solution for sure. I have not found out why  port 25 is not managed on the outside yet. I would still apreciate any help. My suspision now is now on the submission port in the postfix configuration since port 587 replies correctly.

Cheers Klavs

---

### Post by galvatron408 on 2012-01-08
yea, looks like it is working and looks like it is a routing issue. from the netstat output, I can see postfix listening on 25 and 587 (which is good).

so, why can't you route 25 to 25? I don't understand that.

---

