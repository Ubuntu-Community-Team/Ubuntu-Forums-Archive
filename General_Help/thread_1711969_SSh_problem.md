---
title: "SSh problem"
date: 2011-03-22
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-22
Hi All,


I have installed ssh in my system. i try connect some other system i am getting this error
ssh root@192.168.7.140
ssh: connect to host 192.168.7.140 port 22: Connection refused

how to fix this problem

Thank you,

Regards,
Suresh

---

### Post by jerome1232 on 2011-03-22
Make sure an ssh server is running on the computer you are connecting to.

Make sure if you have a firewall enabled, to allow traffic on port 22.

If that server is an Ubuntu server by default root is locked, plus ssh is configured by default to not allow ssh logins to the root account.

---

### Post by suresh_vandiyur on 2011-03-22
> **jerome1232 said:**
> Make sure an ssh server is running on the computer you are connecting to.

Make sure if you have a firewall enabled, to allow traffic on port 22.

If that server is an Ubuntu server by default root is locked, plus ssh is configured by default to not allow ssh logins to the root account.

sudo /etc/init.d/ssh restart * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 

chidambar@192.168.7.140
ssh: connect to host 192.168.7.140 port 22: Connection refused
Still i am getting is error

Thank you,

Regards,
Suresh

---

### Post by jerome1232 on 2011-03-22
> **suresh_vandiyur said:**
> sudo /etc/init.d/ssh restart * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 

chidambar@192.168.7.140
ssh: connect to host 192.168.7.140 port 22: Connection refused
Still i am getting is error

Thank you,

Regards,
Suresh

Ok so you have computer A and Computer B

Your on computer A (the client), Computer B (the server) is 192.168.7.140, Computer B is the one you installed SSH Server correct? Does computer B have a firewall enabled? What's the output of the following command on computer B?

```
sudo netstat -tnlp
```

---

### Post by suresh_vandiyur on 2011-03-22
> **jerome1232 said:**
> Ok so you have computer A and Computer B

Your on computer A (the client), Computer B (the server) is 192.168.7.140, Computer B is the one you installed SSH Server correct? Does computer B have a firewall enabled? What's the output of the following command on computer B?

```
sudo netstat -tnlp
```

sudo netstat -tnlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3061/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1177/cupsd      
tcp6       0      0 :::139                  :::*                    LISTEN      817/smbd        
tcp6       0      0 :::22                   :::*                    LISTEN      3061/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      1177/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      817/smbd        
I have installed sudo apt-get install ssh it is client software or server. because computer A is the Server. Ok

Thank you,

Regards,
Suresh

---

### Post by jerome1232 on 2011-03-22
So your on the server atm? What happens if you try to ssh to localhost?

edit in case that wasn't clear

```
ssh localhost
```

sounds to me like there's a firewall enabled, have you ever at any point turned on iptables or ufw?

If iptables has rules setup let's see them, make sure to highlight all of this output and click the # symbol to wrap it in code tags for ease of reading.

```
sudo iptables -L
```

---

### Post by suresh_vandiyur on 2011-03-22
> **jerome1232 said:**
> So your on the server atm? What happens if you try to ssh to localhost?

edit in case that wasn't clear

```
ssh localhost
```

sounds to me like there's a firewall enabled, have you ever at any point turned on iptables or ufw?

If iptables has rules setup let's see them, make sure to highlight all of this output and click the # symbol to wrap it in code tags for ease of reading.

```
sudo iptables -L
```

ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is 1e:0e:17:a7:95:f8:a7:17:ff:fc:df:75:3c:51:61:ad.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
root@localhost's password: 
Permission denied, please try again.
root@localhost's password: 
Linux notionink62-Veriton-Series 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
#sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

it shows like this.. it s ok for the server side.

Thank you,

Regards,
Suresh

---

### Post by vivek.pandey on 2011-03-22
do you have an account in the computer you are trying to ssh?like a user by name chidambar?

---

### Post by suresh_vandiyur on 2011-03-22
> **vivek.pandey said:**
> do you have an account in the computer you are trying to ssh?like a user by name chidambar?


Chidambar is the user name. i have installed in my system apt-get install ssh it is the ssh client for software. please help

Thank you,

Regards,

Suresh

---

### Post by vivek.pandey on 2011-03-22
> **suresh_vandiyur said:**
> Chidambar is the user name. i have installed in my system apt-get install ssh it is the ssh client for software. please help

Thank you,

Regards,

Suresh

no what i meant is you are trying to ssh a system with its ip address 192.168.7.140... do you have an account in this system ie with ip 192.168.7.140?

---

### Post by Script Warlock on 2011-03-22
try

ssh  server_ip -p 22

or you can post your sshconfig

---

### Post by jerome1232 on 2011-03-22
> **Script Warlock said:**
> 
or you can post your sshconfig

Seconding the ssh config. Also is there anything in hosts.deny? Based on the output of netstat we know you have an ssh server running and listening on all interfaces for connections from anywhere. Are you sure you have the correct ipaddress?


```
cat /etc/ssh/sshd_config 
cat /etc/hosts.deny
ifconfig | grep "inet addr"
```


and PLEASE make sure you are in advanced mode, highlight all of the output and press the # button to make it appear in a code window so that it is easy for us to read.

---

