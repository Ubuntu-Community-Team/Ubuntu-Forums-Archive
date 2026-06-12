---
title: "Unable to access POP3 SSL from outside"
date: 2011-08-30
forum: General Help
---

### Post by phinole on 2011-08-30
Hello -
I am an experienced UNIX user.  I've written shell scripts, PERL, and developed Java apps running on everything from Sun Solaris to RedHat.  This is my first attempt at managing a UNIX server and I am not a sysadmin by trade, so I apologize if my questions are elementary in nature.

I recently setup a Ubuntu 11 web server using the howtoforge "perfect server" guide.  Courier and Postfix are handling the mail, and internal IMAP with squirrelmail works just fine, but I can't access POP3 over SSL.   I was successful with regular POP3 on port 110 but don't want to use that going forward.  Fail2ban is running, as is the Bastille firewall.  I've configured Bastille to open port 995 for POP3 SSL (using the config in /etc) and iptables looks like this:
```

Chain PUB_IN (4 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:ftp-data
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:ftp
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:ssh
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:smtp
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:domain
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:www
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:imap2
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:https
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:pop3s
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:mysql
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:http-alt
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:tproxy
PAROLE     tcp  --  anywhere             anywhere            tcp dpt:webmin
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     udp  --  anywhere             anywhere            udp dpt:mysql
DROP       icmp --  anywhere             anywhere
DROP       all  --  anywhere             anywhere

```

If I look at the ports currently available on the machine, I see port 995 is open for all IP addresses.  It doesn't matter if I change the availability to 127.0.0.1, I still can't access POP3-SSL:

```

 sudo netstat -avn | grep tcp
netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.
tcp        0      0 127.0.0.1:143           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN
tcp        0      0 172.21.0.56:53          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:993           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
tcp        1      0 127.0.0.1:53090         127.0.0.1:3306          CLOSE_WAIT
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN

```

I generated my certs according to a courier/postfix guide I found online and can connect (from the same server, of course):

```

sudo openssl s_client -connect 127.0.0.1:995
CONNECTED(00000003)
depth=0 /C=US/ST=FL/L=xxxxxxxxxx/O=xxxxxxxxx/OU=xxxxxxxxxx Webmaster/CN=mail.xxxxxxxxxx.com/emailAddress=webmaster@xxxxxxxxxxx.com
**verify error:num=18:self signed certificate**
verify return:1
depth=0 /C=US/ST=FL/L=xxxxxxxxxxx/O=xxxxxxx/OU=xxxxxxxxxxxxxx Webmaster/CN=mail.xxxxxxxxxxx.com/emailAddress=webmaster@xxxxxxxxxxxxx.com
verify return:1
---
Certificate chain
 0 s:/C=US/ST=FL/L=xxxxxxxxxxxxx/O=xxxxxxxxxxxxx/OU=xxxxxxxxxxxxxxWebmaster/CN=mail.xxxxxxxxxxxxxx.com/emailAddress=webmaster@xxxxxxxxxxxxxx.com
   i:/C=US/ST=FL/L=xxxxxxxxxxxx/O=xxxxxxxxxx/OU=xxxxxxxxxxxxxxxx Webmaster/CN=mail.xxxxxxxxxxx.com/emailAddress=webmaster@xxxxxxxxxx.com
---
Server certificate
-----BEGIN CERTIFICATE-----
cert key here
-----END CERTIFICATE-----
subject=/C=US/ST=FL/L=xxxxxxxxxxx/O=xxxxxxxxxxxx/OU=xxxxxxxxxxxxWebmaster/CN=mail.xxxxxxxxxxx.com/emailAddress=webmaster@xxxxxxxxxxxx.com
issuer=/C=US/ST=FL/L=xxxxxxxxx/O=xxxxxxxxxxx/OU=xxxxxxxxxxx Webmaster/CN=mail.xxxxxxxxxxxxxx.com/emailAddress=webmaster@xxxxxxxxxxxxxx.com
---
No client certificate CA names sent
---
SSL handshake has read 1117 bytes and written 293 bytes
---
New, TLSv1/SSLv3, Cipher is AES256-SHA
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: zlib compression
Expansion: zlib compression
SSL-Session:
    Protocol  : TLSv1
    Cipher    : AES256-SHA
    Session-ID: 1EBC9841113D206EE58C6FA3FF0DB4D17F63469FBB3FC389CE01903903B0B04D
    Session-ID-ctx:
    Master-Key: 3B0D21F3460B35E28EEE22428D4E06431B70CD8386A85D106A42D68FF92E5F0455B27E2BA7E0D9E73AFC9407A345D650
    Key-Arg   : None
    TLS session ticket:
    0000 - 42 99 4d 9f 52 4e 11 4f-dc 6d 66 56 41 55 43 b9   B.M.RN.O.mfVAUC.
    0010 - 2c 86 fb 5d 57 bd 55 f7-1c f9 6b 11 c4 86 e3 6a   ,..]W.U...k....j
    0020 - 82 84 2a c0 ac 5d c1 51-53 0e 26 b0 b8 b4 bb b4   ..*..].QS.&.....
    0030 - 39 90 c1 47 2f b2 bf 1e-6a d9 64 3d 00 dc 5f 71   9..G/...j.d=.._q
    0040 - c9 15 54 2c 88 c5 71 0d-49 15 12 44 a0 f0 b2 e7   ..T,..q.I..D....
    0050 - c0 b1 f1 77 60 2e c5 30-2f d6 11 cb 96 0c ba 7b   ...w`..0/......{
    0060 - d6 54 e2 40 80 7a f5 a4-87 49 df 8e 5d 8f 4d 0b   .T.@.z...I..].M.
    0070 - 13 b4 d5 cd 32 7d 6d c2-5c 27 c4 ea 03 8e 87 bc   ....2}m.\'......
    0080 - 70 7f b3 57 84 b7 e7 57-12 82 fc 3a 54 ea fa 68   p..W...W...:T..h
    0090 - 6e 7c f0 de 2b c0 e8 81-07 b6 b9 8a 3d e6 bc da   n|..+.......=...

    Compression: 1 (zlib compression)
    Start Time: 1314710719
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
+OK Hello there.

```

Not sure if the self-signed cert (error code 18) is a problem but none of my research online says that it should be, so I don't know.

I can telnet to my host from another box using port 995, but Outlook 2010 and the iPhone will not connect to my mail server using POP3 SSL.

I've tried disabling Bastille and changing the pop3-ssl config for Courier quite a bit.  I'm not familiar enough with iptables to know if those rules look incorrect and haven't tried to use IMAP from the outside yet.  Any help is greatly appreciated as I need to get SSL email working for my clients.  Thank you.

---

### Post by zero2xiii on 2011-08-30
Hay,

I have setup numerous file based servers (web servers, and FTP and such).

The first thing that pops to mind, (since it seems that everything LOCALY is working fine) is what is your NAT configuration?

This is the configuration of the network router, connected between you and the internet. You need to forward the internet port 995 to the internal network (lets say the server ip is 192.168.1.10) server on port 995.

The rule should be something such as (only an example for a basic idea)

RDR 000.000.000.000:995 192.168.1.10:995


This is also true on some routers for wireless networks (the wireless and wired networks are virtualy seperated).

Hope this helps

---

### Post by phinole on 2011-08-30
> **zero2xiii said:**
> Hay,

I have setup numerous file based servers (web servers, and FTP and such).

The first thing that pops to mind, (since it seems that everything LOCALY is working fine) is what is your NAT configuration?

This is the configuration of the network router, connected between you and the internet. You need to forward the internet port 995 to the internal network (lets say the server ip is 192.168.1.10) server on port 995.

The rule should be something such as (only an example for a basic idea)

RDR 000.000.000.000:995 192.168.1.10:995


This is also true on some routers for wireless networks (the wireless and wired networks are virtualy seperated).

Hope this helps

Thanks for the response.  My understanding of NAT is not really where it should be, but I'm using a Ubuntu installation that's a VM on a Windows machine.  The machine is behind the rackspace's firewall and NAT does occur.  I have a public IP address that gets NAT'd to an "inet addr" as shown by the ifconfig command.  I will check with the provider to see if this specific port needs to be forwarded manually, but I dismissed that as a possible cause since connecting via port 110 (regular POP3) was fine.

Where would I create this rule or edit port forwarding on the Ubuntu machine?

Thanks again.

---

### Post by zero2xiii on 2011-08-30
> **phinole said:**
> Thanks for the response.  My understanding of NAT is not really where it should be, but I'm using a Ubuntu installation that's a VM on a Windows machine.  The machine is behind the rackspace's firewall and NAT does occur.  I have a public IP address that gets NAT'd to an "inet addr" as shown by the ifconfig command.  I will check with the provider to see if this specific port needs to be forwarded manually, but I dismissed that as a possible cause since connecting via port 110 (regular POP3) was fine.  Thanks again, I will check on this.


Ah that adds another level of problems (connection wise) especialy from the internet.

Haha im just going to point out those I have experienced before, so IF you bump into them, you wont go "wtf??":

1. NAT after a NAT is suicide!... The NAT of the router RDRs (redirects) to the HOST of the virtual machine, thus, no connection. UNLESS the virtual NAT (If your virtual machine's network setup uses a NAT settup which is the default for vmware) is setup to RDR all connections to the HOST : PORT to the VIRTUAL : PORT, then, you loose that port on the HOST.

2. Host-only: this will cause the VIRTUAL to be COMPLETELY isolated from the network.. ONLY the HOST can access the VIRTUAL.

3. Bridged mode (suggested): Make sure to use the "Replicate Physical network connection state" or simmilar option, ESP if the VM is running in windows (windows being the HOST of the VM). If you dont use it, drivers begin playing a role. Either there is 2 IPs, one being the HOST's and the other being the VIRTUAL. OR.. there is only one, the HOST and then windows effectively takes over the role of the NAT server, then you will be chewing on your wrists...

Just a quick overview of some of the things I have had happen to me before. It might be completely unrelated to what you are experiencing. But sooner or later you might have something bugging, then this might give you a nudge in the right direction

Cherz

---

### Post by phinole on 2011-09-01
I've resolved what I think are all connectivity problems to this machine from the outside world.  I can telnet to the domain on port 995 from multiple servers around the country and get a connection, so I know the port is open and I'm listening.  Getting an email client to actually use POP3 over SSL is still another matter.

I now believe the problem is related to using a self-signed certificate, which causes Outlook 2010 and the iPhone to suffer what appears to be a time-out, despite all the "proper" settings, ports, login/password being used to connect.  I got a trial cert from Geotrust and am going to see if that solves the problem.  I hope I'm not wasting my time with that route.

Any thoughts/input on my diagnosis is greatly appreciated.

---

### Post by zero2xiii on 2011-09-01
> I now believe the problem is related to using a self-signed certificate, which causes Outlook 2010 and the iPhone to suffer what appears to be a time-out, despite all the "proper" settings, ports, login/password being used to connect. I got a trial cert from Geotrust and am going to see if that solves the problem. I hope I'm not wasting my time with that route.

Try that. If the problem is the "self signed" certificate, it's weird. Normaly you will get a prompt if you wish to add the site/domain to your trusted list since the certificate is not reconised or something simmilar. Atleast that is in my experience what happens. (espesialy on routers with VPN)

But maybe you are lucky and that solves your problem. If that doesn't solve it for you, then I am out of suggestions. Maybe there is someone with more SSL experience which will be able to assist you further in the matter. 

Good luck :)

---

### Post by phinole on 2011-09-02
Well, the iPhone connects, although it asked me to verify my certificate first, but it's working just fine.  Outlook 2010 (64-bit) refuses to connect though.

This message is popular in the logs whenever Outlook tries to connect:

pop3d-ssl: Unexpected SSL connection shutdown.

If anyone has thoughts on this, I would appreciate it.  Should I only use the 32-bit version of Office 2010?

---

### Post by zero2xiii on 2011-09-02
Hay,

Glad to hear you got the iPhone working.

> Should I only use the 32-bit version of Office 2010?

I doubt it has anything to do with the architecture? I can't see how that will play any part. Especialy if I take the log into considiration:

> pop3d-ssl: Unexpected SSL connection shutdown.

What is your TTL settings? Might they be the cause of the problem? Are Outlook configured to use the correct auth method?

I am wondering why no one else is replying.. It is good manners to not intefare when some one else is already helping, I understand that, but You guys are more than welcome to jump in, I am just making suggestions that seems logical to me.

Cherz again

---

### Post by phinole on 2011-09-02
> What is your TTL settings? Might they be the cause of the problem? Are Outlook configured to use the correct auth method?

Here are the relevant settings from /etc/courier/pop3d-ssl:

```
SSLPORT=995
SSLADDRESS=0.0.0.0
POP3DSSLSTART=YES
POP3_STARTTLS=YES
POP3_TLS_REQUIRED=1
TLS_STARTTLS_PROTOCOL=SSL23
TLS_PROTOCOL=SSL23
TLS_CERTFILE=/etc/ssl/mail.mydomain.com.pem
TLS_TRUSTCERTS=/etc/ssl/intermediate.geotrust_cert.txt
TLS_VERIFYPEER=PEER
TLS_EXTERNAL=emailaddress
```

Note:  I've also tried TLS_STARTTLS_PROTOCOL=TLS1 and I've also tried both TLS_STARTTLS_PROTOCOL and TLS_PROTOCOL to be set to SSL3 exclusively, which makes no difference to Outlook 2010.

Outlook 2010 is configured to use SSL on port 995 for the correct mail server.  Oddly enough I'm able to send from Outlook using my SMTP server, which according to the postfix config, requires TLS.  However, it just refuses to connect to the POP3 server with SSL.

Since I'm new at server admin, is it absolutely necessary to use encrypted POP3, or can I get away with using straight POP3 on port 110?  (This does work for me from Outlook 2010)

Thanks for all your help, I really do appreciate your input.

---

### Post by e79 on 2011-09-02
> **phinole said:**
> I can telnet to my host from another box using port 995, but Outlook 2010 and the iPhone will not connect to my mail server using POP3 SSL.

I might be wrong, but unless you import your self-signed certificate into your Windows, machine, Outlook 2010 would refuse to connect as it is not signed by a valid 3rd party authority. It happened to me during some tests I was conducting for implementing an Exchange 2010 server.

> **phinole said:**
> Since I'm new at server admin, is it absolutely necessary to use  encrypted POP3, or can I get away with using straight POP3 on port 110?   (This does work for me from Outlook 2010)


You can always use PoP3 unsecured if you want, but all command and passwords are passed in clear text, so anyone sniffing your connection would be able to have your password.

Hope this helps

---

### Post by phinole on 2011-09-02
> I might be wrong, but unless you import your self-signed certificate into your Windows, machine, Outlook 2010 would refuse to connect as it is not signed by a valid 3rd party authority. It happened to me during some tests I was conducting for implementing an Exchange 2010 server.

Yes, I originally suspected a self-signed cert as the culprit also, which is why the iPhone wouldn't connect either.  However, now that I have a valid trial cert from Geotrust (which by my estimation is a trusted 3rd party authority), Outlook 2010 should accept it just like the iPhone.  Is there some sort of manual process I need to perform to import that cert into Windows 7 so Outlook will actually connect?

Thank you!

---

### Post by e79 on 2011-09-03
Yeah you need to manually import it if Outlook still complains:

[http://windows.microsoft.com/en-US/windows-vista/Import-or-export-certificates-and-private-keys](http://windows.microsoft.com/en-US/windows-vista/Import-or-export-certificates-and-private-keys)

P.S: sorry for the delay, I was out for a couple of hours  ;)

---

### Post by phinole on 2011-09-03
I solved the problem.  I'm not 100% sure *how*, but it works.

Just screwing around with it and not intending to actually solve the problem, I changed the settings on the account in Outlook to use a 3 minute timeout and the SMTP encrypted connection to &#8220;auto&#8221; (which should have no bearing on POP3, so I assume the timeout change did the trick?).

It then connected and asked to validate my certificate, issued by "my name".  It said to validate the cert, I should contact &#8220;my name&#8221;, which made me laugh.  Anyway, I went through the import process and elected "auto", so Windows placed the cert in "Trusted Root Certification Authorities".

It works!!!!  Please feel free to inquire if you want further details on my Courier config or anything else.  I'd be happy to help someone else navigate this maze.  THANK YOU for taking the time to contribute to this thread.

---

### Post by e79 on 2011-09-03
Indeed, as long as you can import your certificate (in any way) to the "Trusted Root Certification Authorities", you should be home free.

I'm glad you could solve your issue,

Cheers

---

