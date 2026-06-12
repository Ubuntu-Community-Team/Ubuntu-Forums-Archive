---
title: "SSH problems"
date: 2010-10-29
forum: General Help
---

### Post by U_buntu on 2010-10-29
I'm having a hard time getting connected to other computers on my home network through SSH. Says connection refused. I have added the availability of the ports to the computers, and have had access once before through ssh. But now I'm getting the "connection refused" statement. Any idea's?

---

### Post by hwttdz on 2010-10-29
From the machine to which you hope to connect run "ssh -v 127.0.0.1" and please share the output.

---

### Post by U_buntu on 2010-10-29
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 127.0.0.1 [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host 127.0.0.1 port 22: Connection refused

---

### Post by CharlesA on 2010-10-29
That means SSH isn't installed on the machine you are trying to connect to.

---

### Post by matt_symes on 2010-10-29
Hi 

install openssh-server on the machine you want to connect to.

sudo apt-get install openssh-server.

Kind regards

---

### Post by U_buntu on 2010-10-29
I don't want to be argumentative, but I have installed that on all my machines two days ago

---

### Post by CharlesA on 2010-10-29
Make sure that ssh is listening on the target machines with ***netstat -ln***.

---

### Post by U_buntu on 2010-10-29
I ran that but don't understand what I am looking at

---

### Post by efflandt on 2010-10-29
Do you see ssh if you do **netstat -tl** (the t is for tcp and the small L is for listening) on a computer you are trying to connect to?

Have you done anything with a firewall (ufw?)?

---

### Post by U_buntu on 2010-10-29
I have some, but I usually just edit the iptables

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN

---

### Post by CharlesA on 2010-10-29
If those are the results of netstat -tl, then SSH isn't running. Are you doing that on the client or the server?

---

### Post by matt_symes on 2010-10-29
Hi

Dont worry. You are not being argumentative. We are just trying to make sure all the bases are covered. There are some clever people here to help but i am off to sleep.

Kind regards

---

### Post by U_buntu on 2010-10-29
client I guess, not running a server base that I am aware of. lol But this is not making any sense, I have downloaded the ssh and opened the port 22 in which I test out the ssh on all computers.

---

### Post by CharlesA on 2010-10-29
> **U_buntu said:**
> client I guess, not running a server base that I am aware of. lol But this is not making any sense, I have downloaded the ssh and opened the port 22 in which I test out the ssh on all computers.

I think you may be confused.

Do you have openSSH-server installed on each machine?

You need to have the ssh server installed to be able to connect.

---

### Post by U_buntu on 2010-10-29
yes I do

---

### Post by CharlesA on 2010-10-29
What does this say when you run this on a machine with ssh-server installed?

```
service ssh status
```

---

### Post by U_buntu on 2010-10-30
* could not access PID file for sshd

---

### Post by CharlesA on 2010-10-30
Try it with sudo. If ssh was installed, you'd get a different error.

```
sudo service ssh status
```

You can also use ***ps aux | grep sshd*** to see if sshd is running:

```
charles@atlantis:~$ ps aux | grep sshd
root       683  0.0  0.1  49260  1080 ?        Ss   Oct20   0:00 /usr/sbin/sshd
```

---

### Post by U_buntu on 2010-10-30
yeah its not running, but I do have ssh installed

---

### Post by CharlesA on 2010-10-30
If sshd is not running, how do can you connect via ssh?

What happens if you run this:

```
sudo apt-get install openssh-server
```

---

### Post by U_buntu on 2010-10-30
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 eclipse-rcp libswt-gtk-3.5-jni java-common
  libaccess-bridge-java-jni libaccess-bridge-java icedtea-6-jre-cacao
  eclipse-platform-data libequinox-osgi-java default-jre
  openjdk-6-jre-headless tzdata-java openjdk-6-jre openjdk-6-jre-lib
  default-jre-headless libswt-gtk-3.5-java ca-certificates-java
  linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by CharlesA on 2010-10-30
Then start it up with:

```
sudo service ssh start
```

---

### Post by issih on 2010-10-30
EDIT..actually it has already been mentioned ...ignore me :)

Apologies if this is obvious, but no one has explicitly mentioned an important detail.

You need to install the openssh-server on the machine you want to connect to, not the machine you are connecting from.

The ssh server software runs as a daemon (read runs continuously) on the machine it is installed on. Other machines can then run an ssh client to connect to the server software on that machine.

Installing the server software on the machine you are trying to connect from will mean that you can connect to that machine from others, not that you can connect to other machines.

Hopes that helps

---

### Post by U_buntu on 2010-10-30
like I said, its installed on all machines. I ran sudo service ssh start, says its "ok" but nothing after that

---

### Post by CharlesA on 2010-10-30
What does it say if you try to stop it?

When I stop and start ssh on my server it says this:

```
sudo service ssh stop
ssh stop/waiting
```

```
sudo service ssh start
ssh start/running, process 2665
```

---

### Post by U_buntu on 2010-10-30
says nothing. when i try to connect to another computer it just hangs there after the connect line, never does anything. 

* Stopping OpenBSD Secure Shell server sshd                             [ OK ] 
* Starting OpenBSD Secure Shell server sshd                             [ OK ]

---

### Post by CharlesA on 2010-10-30
Should be running then.

Is ssh listed in netstat now?

```
netstat -l
```

---

### Post by U_buntu on 2010-10-30
Something else I found interesting and confusing, I usually go about connecting username@IP address. If I try to connect [email]username@localhost...it[/email] wants to connect, asks for password as usual but, apparently I don't know the passwords (sarcasm lol) . So whats up with that?

---

### Post by U_buntu on 2010-10-30
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN  


among many other things listed

---

### Post by CharlesA on 2010-10-30
By using localhost, it means that you can connect from the machine you are physically at now.

Are you able to connect from one of the machines like so:

```
ssh user@localhost
```

EDIT: It's listening now. Try to connect again.

---

### Post by U_buntu on 2010-10-30
no, it wont take my password. Makes no sense to me.

---

### Post by U_buntu on 2010-10-30
EDIT: It's listening now

how do I do that?

---

### Post by CharlesA on 2010-10-30
Check /var/log/auth.log for why it's not authenticating.

You could try to connect in verbose mode to see if it's throwing any errors:

```
ssh -v user@host
```

---

### Post by U_buntu on 2010-10-30
That did not work either, the logs talking about a public-key alot. and of course the password issue

---

### Post by CharlesA on 2010-10-30
If you cannot authenticate, then that's your problem now.

Are you using a private key or just passwords?

---

### Post by U_buntu on 2010-10-30
just passwords which at the moment, each computer has one password for everything.

---

### Post by U_buntu on 2010-10-30
This is weird, bit of trial and error just to make sure I didn't miss anything, now i'm able to connect with user@IP and it went right through on "one" computer. Still just sits there on the other.

---

### Post by CharlesA on 2010-10-30
Create a new user and try to connect with those credentials.

---

### Post by U_buntu on 2010-10-30
It works now, but I still don't know why it was not working.

Thanks for all the help

---

### Post by U_buntu on 2010-10-30
oh but I do have to use -v other wise it just sits there

---

### Post by CharlesA on 2010-10-30
Strange.

The only thing -v does is turn debugging on so you can see what's going on "behind the scenes"

---

### Post by efflandt on 2010-10-30
Not sure why it was not working before.  But for ssh you need to use the name and password (or keys configured) of a user account on the machine you are trying to connect TO.  sshd would refuse connection if there is no such user (or you do not use correct password) for the user account on the server.

So if username is different than your local user, you have to include a ***username on the server*** in **ssh username@IP**

That could get confusing if you have a different username or password on each computer.

---

### Post by U_buntu on 2010-10-30
Yes strange indeed. Yeah I understand the different usernames and passwords and how they can get missed up. I'm pretty sure I have them in the right order though lol. Like I said, it works with -v.

---

### Post by CharlesA on 2010-10-30
I guess if it works with -v but not without -v, you can just use -v. *shrug*

---

### Post by U_buntu on 2010-10-30
doesn't need -v now. I don't know whats up with it. oh well

Thanks

---

