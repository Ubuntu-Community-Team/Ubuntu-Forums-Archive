---
title: "How to FTP using command line?"
date: 2010-09-17
forum: General Help
---

### Post by jadonchristensen on 2010-09-17
Hello,

I have a virtual private server that I SSH into. While I am using SSH, I need to be able to FTP from command line to another server. I want to do this in the easiest most sure way possible.

(((I am not using my real IP below for security.)))
I have tried the following commands.
sftp 10.99.99.99

> ssh: connect to host 10.99.99.99 port 22: No route to host
Couldn't read packet: Connection reset by peer

ssh 10.99.99.99

> ssh: connect to host 10.99.99.99 port 22: No route to host

---

### Post by Darkness Des on 2010-09-17
gFTP is a gui solution that I recommend, but if it really has to be on the command line, use ftp. It's preinstalled. Just use the command *man ftp* to read the manual page for it.

---

### Post by llamabr on 2010-09-17
> **Darkness Des said:**
> gFTP is a gui solution that I recommend, but if it really has to be on the command line, use ftp. It's preinstalled. Just use the command *man ftp* to read the manual page for it.

since you didn't ask for a gui, i'll suggest sftp.  I know they lose their entire mind when I suggest a new user read a man page, but man for sftp is not too complicated.

---

### Post by psusi on 2010-09-17
You appear to be trying to ssh to a local address ( 10.*.*.* ).  My guess is that you are trying to have the remote machine ftp back to a local machine in your house behind a NAT router, which is not possible since the rest of the Internet can not reach 10.*.*.*.

Instead go to the other machine on your network, and connect to the remote machine from there rather than trying to do it the other way around.

---

### Post by v1ad on 2010-09-17
ftp should be on port 21. also try username@ipaddress . i wouldn't specify a port, it will use default.

---

### Post by kalos on 2010-09-17
> **jadonchristensen said:**
> I have a virtual private server that I SSH into. 
Let's call this machine A.
> **jadonchristensen said:**
> While I am using SSH, I need to be able to FTP from command line to another server.
And the one you ssh from machine B.

So you ssh from B to A, and then you want to ftp from A to B?

But you get this:
> **jadonchristensen said:**
> 
ssh: connect to host 10.99.99.99 port 22: No route to host

That looks like B is either stealthed (firewall settings) or the IP address is wrong. I'm guessing that A is on a remote network, so your local IP address is inaccessible.

Presumably you could accomplish what you're trying with an SSH tunnel. If you forwarded port 2222 to B when you connect, then you could connect back to A through that port. However, I don't know how to get that to work.

Here's what I tried. It should give you a good google start.
```

# stop ssh server
machine-b:~$ sudo /etc/init.d/ssh stop
# create the tunnel in the background
machine-b:~$ ssh -f jadon@machine-a -L 3322:machine-a:3322 -N
# start ssh server with our alternate port
machine-b:~$ sudo /usr/sbin/sshd -p 3322
# connect to the remote machine
machine-b:~$ ssh jadon@machine-a
# in the remote server
machine-a:~$ ssh -p 3322 localhost
machine-a:~$ scp -p 3322 localhost:~/somefile .
machine-a:~$ sftp -oPort=3322 localhost

```


Another alternative is to make your home machine available to the public, but this makes you vulnerable to foreign users.

---

