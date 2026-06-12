---
title: "su hanging, Login hanging (SSH)"
date: 2012-02-06
forum: General Help
---

### Post by dougreed765 on 2012-02-06
We have a server (HP Proliant) running  Ubuntu 9.04 (server). It is running Zabbix and has the Postgres database.

All was running fine until about a week ago but the following things started to happen;

- When trying to log in using putty, after entering the password, the session hangs

  -  When logged in and trying to su to another user, the session hangs

  -  Cronjobs for certain users fail to run

  -  Commands are slow to start

The problem can be fixed with a re-boot but the problem will re-occur hours or days later.

Zabbix and the database both continue to run and the system is accessible using FTP

Oh and telnet has not been enabled




Any assistance will be gratefully appreciated

---

### Post by 2F4U on 2012-02-06
Did you look into the system log files? Are there any errors recorded? What is the resource usage, e. g. CPU, memory?

---

### Post by dougreed765 on 2012-02-07
[FONT=&quot]Running top shows nothing significant[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]The slowness is from when you type in the command to when it starts execution. [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]One interesting thing was when running netstat –a, the data scrolled up the screen for about 10 lines and then paused for several minutes before completing.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Interesting error that occurred in one of the older logs related to binding to port 22;[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]A similar error message occurred when I was trying to run;[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]/usr/sbin/sshd -d[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]sshd re-exec requires execution with an absolute path[/FONT]
  [FONT=&quot]root@uksysmon:/var/log# /usr/sbin/sshd -d[/FONT]
  [FONT=&quot]debug1: sshd version OpenSSH_5.1p1 Debian-5ubuntu1[/FONT]
  [FONT=&quot]debug1: read PEM private key done: type RSA[/FONT]
  [FONT=&quot]debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048[/FONT]
  [FONT=&quot]debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048[/FONT]
  [FONT=&quot]debug1: private host key: #0 type 1 RSA[/FONT]
  [FONT=&quot]debug1: read PEM private key done: type DSA[/FONT]
  [FONT=&quot]debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024[/FONT]
  [FONT=&quot]debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024[/FONT]
  [FONT=&quot]debug1: private host key: #1 type 2 DSA[/FONT]
  [FONT=&quot]debug1: rexec_argv[0]='/usr/sbin/sshd'[/FONT]
  [FONT=&quot]debug1: rexec_argv[1]='-d'[/FONT]
  [FONT=&quot]debug1: Bind to port 22 on 0.0.0.0.[/FONT]
  [FONT=&quot]Bind to port 22 on 0.0.0.0 failed: Address already in use.[/FONT]
  [FONT=&quot]debug1: Bind to port 22 on ::.[/FONT]
  [FONT=&quot]Bind to port 22 on :: failed: Address already in use.[/FONT]
  [FONT=&quot]Cannot bind any address.[/FONT][FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Looking through the logs (/var/log) there is only one logfile that has been updated recently, syslog which shows just the – Mark – message.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  :confused:

---

### Post by Khayyam on 2012-02-07
> **dougreed765 said:**
> [FONT=&quot][/FONT][FONT=&quot][/FONT][FONT=&quot]Bind to port 22 on :: failed: Address already in use.[/FONT]

dourgreed765 ..

Not all symptoms are related, there may be seperate reasons why user cronjobs fail to run, why logins and 'su username' hang, and why the tty is unresponsive.

However, the above error doesn't help as I'd bet my pants its simply a case of sshd already being bound to the port, initd being responsible for starting services at boot. So, unless sshd had been killed then the port 22 will be "in use".

```
netstat -l --tcp |grep -e 'ssh\|;LISTEN'
```

That being the case, its unrelated to the other problems your experiencing. The only way to troubleshoot a problem like this is via a process of elimination, isolating causes from effects. Can you ssh using something other than PuTTY, does the login still hang, etc, etc.

Some of the symptoms you describe sound like symptoms I've experienced with a failing NIC, and it may well be that some of problems you've had **could** have hardware as its cause .. but without isolating the problem in some way who can tell.

HTH ...

---

### Post by dougreed765 on 2012-02-07
[FONT=&quot]Netstat –l –tcp hung – I left it for about an hour;[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]netstat -l --tcp[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]root@uksysmon:/var/log# netstat -l --tcp[/FONT]
  [FONT=&quot]Active Internet connections (only servers)[/FONT]
  [FONT=&quot]Proto Recv-Q Send-Q Local Address           Foreign Address         State[/FONT]
  [FONT=&quot]tcp        0      0 *:imaps                 *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 uksysmon.d:zabbix_agent *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 uksysmon.dl:zabbix_trap *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 *:pop3s                 *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 localhost:submission    *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 *:netbios-ssn           *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 *:pop3                  *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 *:imap2                 *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 *:www                   *:*                     LISTEN[/FONT]
  [FONT=&quot]tcp        0      0 *:ftp                   *:*                     LISTEN[/FONT][FONT=&quot][/FONT]
  [FONT=&quot]Stopped here[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I ran lsof against port 22[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]lsof –i :22[/FONT][FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]COMMAND  PID   USER   FD   TYPE DEVICE SIZE NODE NAME[/FONT]
  [FONT=&quot]sshd    3219   root    3u  IPv4   6143       TCP *:ssh (LISTEN)[/FONT]
  [FONT=&quot]sshd    3219   root    4u  IPv6   6145       TCP *:ssh (LISTEN)[/FONT]
  [FONT=&quot]sshd    4152   root    3u  IPv4  13340       TCP uksysmon.dlink.co.uk:ssh->dlws81.dlink.co.uk:1895 (ESTABLISHED)[/FONT]
  [FONT=&quot]sshd    4179 oracle    3u  IPv4  13340       TCP uksysmon.dlink.co.uk:ssh->dlws81.dlink.co.uk:1895 (ESTABLISHED)[/FONT][FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I tried to connect from another machine using ssh –vvv and got the following (last few lines to hang point shown – password was entered and then it hung)[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Tail of message;[/FONT]
  [FONT=&quot]debug1: Authentications that can continue: publickey,password[/FONT]
  [FONT=&quot]debug3: start over, passed a different list publickey,password[/FONT]
  [FONT=&quot]debug3: preferred publickey,keyboard-interactive,password[/FONT]
  [FONT=&quot]debug3: authmethod_lookup publickey[/FONT]
  [FONT=&quot]debug3: remaining preferred: keyboard-interactive,password[/FONT]
  [FONT=&quot]debug3: authmethod_is_enabled publickey[/FONT]
  [FONT=&quot]debug1: Next authentication method: publickey[/FONT]
  [FONT=&quot]debug1: Trying private key: /home/oracle/.ssh/identity[/FONT]
  [FONT=&quot]debug3: no such identity: /home/oracle/.ssh/identity[/FONT]
  [FONT=&quot]debug1: Trying private key: /home/oracle/.ssh/id_rsa[/FONT]
  [FONT=&quot]debug3: no such identity: /home/oracle/.ssh/id_rsa[/FONT]
  [FONT=&quot]debug1: Trying private key: /home/oracle/.ssh/id_dsa[/FONT]
  [FONT=&quot]debug3: no such identity: /home/oracle/.ssh/id_dsa[/FONT]
  [FONT=&quot]debug2: we did not send a packet, disable method[/FONT]
  [FONT=&quot]debug3: authmethod_lookup password[/FONT]
  [FONT=&quot]debug3: remaining preferred: ,password[/FONT]
  [FONT=&quot]debug3: authmethod_is_enabled password[/FONT]
  [FONT=&quot]debug1: Next authentication method: password[/FONT]
  **[FONT=&quot]user@servname's password:[/FONT]**
  [FONT=&quot]debug3: packet_send2: adding 64 (len 58 padlen 6 extra_pad 64)[/FONT]
  [FONT=&quot]debug2: we sent a password packet, wait for reply[/FONT]
  [FONT=&quot]debug1: Authentication succeeded (password).[/FONT]
  [FONT=&quot]debug1: channel 0: new [client-session][/FONT]
  [FONT=&quot]debug3: ssh_session2_open: channel_new: 0[/FONT]
  [FONT=&quot]debug2: channel 0: send open[/FONT]
  [FONT=&quot]debug1: Entering interactive session.[/FONT][FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]

---

### Post by Khayyam on 2012-02-07
> **dougreed765 said:**
> 
[SNIP]
  [FONT=&quot]tcp        0      0 *:netbios-ssn           *:*                     LISTEN[/FONT]
[SNIP]

  Doug ..

Is this machine is a local server or world accessable? Are the various services you are offering (ftp, www, imap, pop, samba, etc) behind some filewall? Samba should only every be run within private networks, and I would not recommend running it on the same machine you are using to serve mail/www/ftp.

Given that you had written that this problem started a week or so ago then I would be suspicious of any unusual activity that can't be traced to explicit changes you've made to the system.

If the machine has been hacked than you can't rely on 'top', 'lsof', 'ps' of many of the standard tools you'd use to detect whats running and using system resources, rootkits will replace all of these with versions that hide processes from admins prying eyes. Also rootkits often affect 'login' (also 'su') as it is often replaced with a 'key grabber', rootkits might also tamper with the password files. I've seen stray fields in password files caused by clumsy edits that prompted login failure, so I mention this as a possible reason for one of your problems.
  
  > **dougreed765 said:**
> [FONT=&quot][SNIP]
sshd    3219   root    3u  IPv4   6143       TCP *:ssh (LISTEN)[/FONT]
[SNIP]

.. as I said sshd is listening on port 22, and so if you '/usr/sbin/sshd -d' its obvious what'll happen .. "[FONT=&quot]Bind to port 22 on :: failed: Address already in use."

[/FONT]   > **dougreed765 said:**
> [FONT=&quot]I tried to connect from another machine using ssh –vvv and got the following (last few lines to hang point shown – password was entered and then it hung)[/FONT]
  
  [SNIP]
  [FONT=&quot]debug1: Entering interactive session.[/FONT]

Yes, so sshd succeeds and passes it over to $SHELL (the "interactive session"). Why this is failing could be for any number of reasons, the shell could exit because there is some garbage in its .bashrc or .bash_profile. Does this effect all users?

I'm not saying "you've been hacked" .. I'm only point out that so far I'm having a hard time tying all of the reported symptoms to to one cause. The two obvious candidates at this point are a). hardware failure of some sort, and b). hacking.

HTH ...

---

### Post by dougreed765 on 2012-02-08
[FONT=&quot]The machine is used for monitoring and is on a private LAN (all of our outside services are the other side of the firewall). FTP access is password protected[/FONT]
  
[FONT=&quot][/FONT]
Some of the apps should have been disabled
[FONT=&quot][/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]It is running Zabbix and PostgreSQL (both apps are still running)[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]No users can log in although if it is re-booted it will most likely be back to normal for a few days/hours[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I’ve checked the startup files (.bashrc etc) there appears to be nothing ???[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Worth noting that the machine has two NIC’s (this may be relevant)[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Could fping cause issue?[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]We’ll look at re-booting sometime and I’ll keep an eye on the log files[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Regards[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]

---

### Post by Khayyam on 2012-02-08
> **dougreed765 said:**
> [FONT=&quot]The machine is used for monitoring and is on a private LAN (all of our outside services are the other side of the firewall). [...][/FONT] Some of the apps should have been disabled

OK, good .. by "apps" I assume you mean services (imap, pop3, etc), yes, disable any that you don't use. 

  > **dougreed765 said:**
> [FONT=&quot]I&#8217;ve checked the startup files (.bashrc etc) there appears to be nothing ???[/FONT]

You mean the file(s) are empty .. or the files appear OK? If they are empty then remove them (bash will then use the global bashrc/profile in /etc). To rule them out as the casue of the shell exiting rename them (mv .bashrc bashrc), then logout and back in.

I take it your not always logged out as in the 'ssh -vvv' example above (otherwise you wouldn't have been able to post netstat, lsof, etc, output). When behaviour is erratic we can start ruling out causes. If it doesn't **always** happen then most probably the cause is unrelated to that particular symptom.    
  
  > **dougreed765 said:**
> [FONT=&quot]Worth noting that the machine has two NIC&#8217;s (this may be relevant)[/FONT]

Ahhhh .. yes, it is. How are they configured, are they [bonded]("http://www.linux-corner.info/bonding.html"), using the same subnet, or routing traffic between two subnets? You should be aware that routing ([ARP]("http://en.wikipedia.org/wiki/Address_Resolution_Protocol")) tables need to be configured for multiple NIC's on the same subnet otherwise Linux's Networking stack will overlap the interfaces. ARP will go to both interfaces and both will try to respond (and that is not what you want).

I'm not going to give you a tutorial on routing but you should get some idea of whats happening with the following (using Class C subnet addressing, change the IP's to reflect your eth0 eth1 addresses):

```
% sudo apt-get install arping
% hash -r
% arping -I eth0 -c 1 192.168.1.1
% arping -I eth0 -c 1 192.168.1.2
```If in the second aping you see it reply with the MAC of the first then [arptables]("http://en.wikipedia.org/wiki/Arptables") are not setup correctly.

Unless there is some reason for having two NIC's on the same subnet (unlikely) then disable/disconnect one and see if your problems persist. 
[FONT=&quot]
[/FONT]> **dougreed765 said:**
> [FONT=&quot]Could fping cause issue?[/FONT]

Unlikely, but that depends on the duration and ICMP intensity. It also depends on how the host is configured to deal with them, I (using iptables) limit to 1/s. Ping flooding the machine might have a substancial effect if the routing table is not configured correctly.

Also tcp_syncookies can be enabled ..

```
% cat /proc/sys/net/ipv4/tcp_syncookies 
0
% echo "1" > /proc/sys/net/ipv4/tcp_syncookies
```HTH ...

---

### Post by dougreed765 on 2012-02-16
We think that we have found the cause

Because this server was running Zabbix, it was running fping which may have been making a lot of calls that blocked the system also one of the NICs may have not been configured correctly?

After fping was turned off and one of the NIC's removed the server seems to be running OK and accepting SSH connections

Many thanks folks

Regards:D

---

### Post by Khayyam on 2012-02-16
> **dougreed765 said:**
> Because this server was running Zabbix, it was running fping which may have been making a lot of calls that blocked the system also one of the NICs may have not been configured correctly?

After fping was turned off and one of the NIC's removed the server seems to be running OK and accepting SSH connections.

Basically, the problem was how the NIC's were configured, I doubt fping on its own would create that level of disruption. Remember that ping is an ICMP echo request and so the sender will receive an equal number of packets in reponse. So, if its sending out pings and reciving them on both eth0 and eth1 .. double wham.
   
Anyhow, pleased your back to ssh normality ..

> **dougreed765 said:**
> Many thanks folks

Your welcome ...

---

