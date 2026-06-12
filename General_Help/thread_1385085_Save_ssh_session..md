---
title: "Save ssh session."
date: 2010-01-19
forum: General Help
---

### Post by ppp0 on 2010-01-19
Hello everybody!
I've been searching for program which can save ssh session (like SecureCRT) and manage them. but... I've found only [http://embraceubuntu.com/2007/08/17/ssh-menu-save-and-open-ssh-connections-from-the-panel/](http://embraceubuntu.com/2007/08/17/ssh-menu-save-and-open-ssh-connections-from-the-panel/). 
Is there any alternative for this ? SSH Menu doesn't seem for noobs...

---

### Post by Brandon Williams on 2010-01-19
I haven't used it on Linux, but putty is the ssh client that I use on Windows, and it has support for saving sessions. The Linux version is in the standard Ubuntu repositories.

---

### Post by ppp0 on 2010-01-22
> **Brandon Williams said:**
> I haven't used it on Linux, but putty is the ssh client that I use on Windows, and it has support for saving sessions. The Linux version is in the standard Ubuntu repositories.

Oh god thanx! It solved me many problems and i didn't know that putty has linux version...

---

### Post by Lars Noodén on 2010-01-22
@ ppp0 : can you explain a little more what you mean by 'saving' ssh sessions?

Pretty much any terminal allows logging, if that's what you are after.

---

### Post by nothingspecial on 2010-01-22
If you detatch the session, it will save it, and continue any processes you have running. Aslong as you dont reboot.

Is this what you mean?

---

### Post by ppp0 on 2010-01-23
> **Lars Noodén said:**
> @ ppp0 : can you explain a little more what you mean by 'saving' ssh sessions?

Pretty much any terminal allows logging, if that's what you are after.

I mean that i would like to save login and password when i connect to a server using for example "sudo ssh 127.0.0.1" like it does SecureCRT on win platform.

---

### Post by ppp0 on 2010-01-23
> **nothingspecial said:**
> If you detatch the session, it will save it, and continue any processes you have running. Aslong as you dont reboot.

Is this what you mean?

Oh yeah i know it

---

### Post by Lars Noodén on 2010-01-25
> **ppp0 said:**
> I mean that i would like to save login and password when i connect to a server using for example "sudo ssh 127.0.0.1" ...

One way to do way you are describing is done by using the ssh-agent, which ubuntu launched automatically for you.  

Once you have key-based authentication working, you can load the key into the agent using [ssh-add](http://manpages.ubuntu.com/manpages/karmic/en/man1/ssh-add.1.html)

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

Another way would be to multiplex your ssh-sessions.  Probably the easiest way to do that would be to set up something specific for that host in your ssh_config file.

The following is an example for ~/.ssh/ssh_config which sets up multiplexing for connections to the host *xx.yy.zz.aa* if they are made using a shortcut, 'ssh daserva'  Subsequent connections should then pop up a dialog box and confirm (Y/N) the connection, but need no further password entry.  Additionally, the connection is multiplexed over the same TCP connection as the first so that there is no additional problem for the firewall or server if it has connection limits.

```

Host *daserva*
  HostName *xx.yy.zz.aa*
  ControlPath ~/.ssh/controlmasters/%r@%h:%p
  ControlMaster autoask

```

---

### Post by ppp0 on 2010-01-25
> **Lars Noodén said:**
> One way to do way you are describing is done by using the ssh-agent, which ubuntu launched automatically for you.  

Once you have key-based authentication working, you can load the key into the agent using [ssh-add](http://manpages.ubuntu.com/manpages/karmic/en/man1/ssh-add.1.html)

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

Another way would be to multiplex your ssh-sessions.  Probably the easiest way to do that would be to set up something specific for that host in your ssh_config file.

The following is an example for ~/.ssh/ssh_config which sets up multiplexing for connections to the host *xx.yy.zz.aa* if they are made using a shortcut, 'ssh daserva'  Subsequent connections should then pop up a dialog box and confirm (Y/N) the connection, but need no further password entry.  Additionally, the connection is multiplexed over the same TCP connection as the first so that there is no additional problem for the firewall or server if it has connection limits.

```

Host *daserva*
  HostName *xx.yy.zz.aa*
  ControlPath ~/.ssh/controlmasters/%r@%h:%p
  ControlMaster autoask

```



Yes i know this dancing with ssh-add uploading pub key on remote server ) 
If'll have a dosens of servers? 

BTW i found gnome-connection-manager ([http://kuthulu.com/gcm/](http://kuthulu.com/gcm/)) and this really solves generation keys etc...

---

### Post by Lars Noodén on 2010-01-25
> **ppp0 said:**
> Yes i know this dancing with ssh-add uploading pub key on remote server ) 
If'll have a dosens of servers? 


ssh-add does nothing with the remote server.  It loads the key into memory on your *local* machine so that you can use that key repeatedly.  So if you are connecting to the same server many times, it works.  Or if you are connecting to multiple servers that all have that key in their set of authorized keys, it works.

If you have dozens of servers, then multiplexing will not help you if you are connecting straight to the servers.  For that you can use keys and, if you want, the same key for more than one server.  Before you can do that, you have to copy the public key to the authorized_keys file in your account on each server. One way to do that is use [ssh-copy-id](http://manpages.ubuntu.com/manpages/karmic/en/man1/ssh-copy-id.1.html) 



Please say more about what actual task you need to accomplish and that might make it easier to come up with an easy and efficient solution.

---

### Post by kuthulu on 2010-02-23
give this a try, 
[http://kuthulu.com/gcm](http://kuthulu.com/gcm)

you can autologin to your hosts, export server list, split screen... like securecrt

hope this helps

---

### Post by ppp0 on 2010-02-23
oh yes i'm using it !)

---

