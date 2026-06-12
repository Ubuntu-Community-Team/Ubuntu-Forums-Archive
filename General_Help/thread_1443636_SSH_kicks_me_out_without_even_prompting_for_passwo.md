---
title: "SSH kicks me out without even prompting for password"
date: 2010-03-31
forum: General Help
---

### Post by Luke771 on 2010-03-31
My multipurpose server (file, freenet, bittorrent) runs headless ubuntu 9.10 server edition, I controlled it with ssh, mostly from my main desktop, which runs ubuntu and windows.

While fiddling with torrentlflux-b4rt I found that I couldnt ssh any more, but I couldnt tell exactly what was the last thing I did. I know that at one point I couldnt sudo any more and I had to boot in recovery mode to chmod /etc/sudoers to 440 as suggested by the sudo error message. After chmod 440 I could sudo again but not ssh.  

Samba works, Freenet works(the anonymous network, not the ISP), and Torrentflux-b4rt also works... well. not really but that's not the point. It is up, and I can access the web interface from the desktop.

SSH on the other hand, still refuses to work. It connects and then I get kicked out without even a password prompt.

Server:
Ubuntu 9.10 Server x86

Client:
WinXP + Putty  "network error: software caused connection abort" => window marked 'inactive'. 

Client:
Ubuntu 9.10 (same machine as Win, dual boot) ssh user@server "Read from socket failed: Connection reset by peer" => back to prompt.

tried to get some info but I don't understand what it means
```

user@box:~$ ssh  -vvvv user@host
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xx [x.x.x.x] port XXX.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

Any ideas?

---

### Post by HermanAB on 2010-03-31
It looks like your network is unreliabale. If you kill the torrents then SSH should work again.

---

### Post by cjhabs on 2010-03-31
Is it possible that the keys were regenerated?
If the key doesn't match what the client is expecting I believe you will get similar behavior.

Remove the entry for that server from the .ssh/known_hosts file on the client and see if that resolves it.

---

### Post by Luke771 on 2010-03-31
solved, thx for help anyway.

for the record, I uninstalled the ssh server and deleted all the config stuff with --purge, then reinstalled and reconfigured it, and it worked... except that it now had a new key. Not a problem for me as this is my own private LAN but it could be different for someone else.
(if the system  has multiple users, accesses over the internet, access from PCs we dont own, etc: make sure that a new server ID wouldnt be a problem before reinstalling Openssh server)

Here's how I did it, someone may find this useful
on the server: 
```

$sudo bash
#apt-get remove openssh-server --purge
#apt-get install openssh-server
#/etc/init.d/ssh stop
#nano /etc/ssh/sshd_config
   <reconfigure ssh server>
#/etc/init.d/ssh start
#exit

```

and then, on the client:
```

$ssh user@server
<output> "OMFG! The pubkey has changed GTFO!(or something of that effect) connection reset by peer 
$ rm -rf .ssh 
$ ssh user@server
user@server password:
login successful blah blah blah blah

```

---

### Post by Iowan on 2010-03-31
So, would you consider this [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

