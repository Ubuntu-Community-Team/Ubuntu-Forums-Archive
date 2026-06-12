---
title: "ssh client conf file"
date: 2011-02-12
forum: General Help
---

### Post by qwertyjjj on 2011-02-12
I am trying to change the ssh conf file so I don;t have to type in the server ip address evrytime I want to connect. Also, these server does not use port 22.
I went to edit this file but there is nothing inside it:
nano ~/.ssh/config

Is that the correct location?
Also, how can I add a port to that file?

---

### Post by runeh76 on 2011-02-12
[http://manpages.ubuntu.com/manpages/hardy/man5/ssh_config.5.html]("http://manpages.ubuntu.com/manpages/hardy/man5/ssh_config.5.html")

---

### Post by qwertyjjj on 2011-02-12
> **runeh76 said:**
> [http://manpages.ubuntu.com/manpages/hardy/man5/ssh_config.5.html]("http://manpages.ubuntu.com/manpages/hardy/man5/ssh_config.5.html")

ssh_config is for the server isn;t it?
I want to edit the client file

This does not exist on my system:
 2.   user&#8217;s configuration file (~/.ssh/config)

---

### Post by runeh76 on 2011-02-12
ssh_config - OpenSSH SSH **client** configuration files

U need to install openssh-client

```
sudo apt-get install openssh-client 
```


FILES
     ~/.ssh/config
             This is the per-user configuration file.  The format of this file
             is described above.  This file is used by the SSH client.
             Because of the potential for abuse, this file must have strict
             permissions: read/write for the user, and not accessible by
             others.  It may be group-writable provided that the group in
             question contains only the user.

     /etc/ssh/ssh_config
             Systemwide configuration file.  This file provides defaults for
             those values that are not specified in the user&#8217;s configuration
             file, _and for those users who do not have a configuration file._
             This file must be world-readable.

---

### Post by qwertyjjj on 2011-02-12
> **runeh76 said:**
> ssh_config - OpenSSH SSH **client** configuration files

U need to install openssh-client

```
sudo apt-get install openssh-client 
```


FILES
     ~/.ssh/config
             This is the per-user configuration file.  The format of this file
             is described above.  This file is used by the SSH client.
             Because of the potential for abuse, this file must have strict
             permissions: read/write for the user, and not accessible by
             others.  It may be group-writable provided that the group in
             question contains only the user.

     /etc/ssh/ssh_config
             Systemwide configuration file.  This file provides defaults for
             those values that are not specified in the user’s configuration
             file, _and for those users who do not have a configuration file._
             This file must be world-readable.

the client already works though - I have used ssh to connect through the terminal to the server.

---

### Post by runeh76 on 2011-02-12
Oh..maybe u need just create that config file to **~/.ssh/**

---

### Post by The Cog on 2011-02-12
If you just want to save typing, I would suggest using a command alias.
If you use a command like this:
> alias xxx ssh 11.22.33.44 99
then when you enter the command "xxx" it will run the command "ssh 11.22.33.44 99". xxx becomes an alias for the ssh command.
You can make this alias permanent by adding the quoted line to the file ~/.bashrc which is a set of commands that run every time you log in.

---

### Post by qwertyjjj on 2011-02-12
> **The Cog said:**
> If you just want to save typing, I would suggest using a command alias.
If you use a command like this:

then when you enter the command "xxx" it will run the command "ssh 11.22.33.44 99". xxx becomes an alias for the ssh command.
You can make this alias permanent by adding the quoted line to the file ~/.bashrc which is a set of commands that run every time you log in.

hmm, do I have to install something?

j@j-Inspiron-9300:~$ alias pp ssh [email]j@xx.xxx.xxx.xxx[/email] -p xxxx
bash: alias: pp: not found
bash: alias: ssh: not found
bash: alias: [email]j@xx.xxx.xxx.xxx[/email]: not found
bash: alias: -p: not found
bash: alias: xxxx: not found

---

### Post by qwertyjjj on 2011-02-12
got it, i HAVE TO USE DOUBLE QUOTES

---

### Post by gmargo on 2011-02-12
You can do this by creating **$HOME/.ssh/config** with contents similar to the following:
```

Host grandma
  HostName 192.168.1.7
  Port 222

Host poppa
  User user
  HostName pappy.example.com
  Port 333

Host momma.example.com
  Port 444
  
Host *
  ForwardAgent yes
  ForwardX11 yes
  ServerAliveInterval 300

```Now just type "ssh grandma" and it goes to the specified IP address of 192.168.1.7 on port 222.  Options under the "Host *" section apply to all hosts.  All of the options you can set are documented in the **ssh_config(5)** man page.

---

### Post by The Cog on 2011-02-12
> **qwertyjjj said:**
> got it, i HAVE TO USE DOUBLE QUOTES
My stupid mistake. Sorry.
```
alias pp="ssh j@xx.xxx.xxx.xxx -p xxxx"
```

---

### Post by [RMC]Pip on 2011-07-27
Hi,
my problem is that the system cannot resolve the host name in the configuration file located in $HOME/.ssh
```
##.ssh/config##
Host hostName
    HostName 1.2.3.4
    User Pip
    Port 33
    ForwardX11 yes
    LocalForward 3389 5.6.7.8:3389
    LocalForward 5900 5.6.7.8:5900
    LocalForward 22 5.6.7.8:22
```I can ping the remote host without any problem, but:
```
ssh hostName
ssh: Could not resolve hostname hostName: Name or service not known
```Some more relevant info, maybe important:
```
netstat -natp | grep sshd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3328/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      3328/sshd

ps -ef | grep sshd
root      3328     1  0 10:19 ?        00:00:00 /usr/sbin/sshd -D
1000      5882  4166  0 15:29 pts/0    00:00:00 grep --color=auto sshd
```On the side note, from terminal this command is ok, no errors:
```
ssh -p 33 hostName@1.2.3.4
```My ultimate goal would be file transfer with secure copy.
Thanks a lot!

---

