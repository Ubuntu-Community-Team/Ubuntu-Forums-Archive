---
title: "SSH and Hack Attempts!"
date: 2010-02-06
forum: General Help
---

### Post by Monotoko on 2010-02-06
Hi Guys, i set myself up with an SSH machine a few days ago and i have just checked my auth.log...and im a bit shocked...

```
Feb  5 00:36:19 Katie-II sshd[6724]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:21 Katie-II sshd[6724]: Failed password for root from 61.178.14.125 port 41498 ssh2
Feb  5 00:36:26 Katie-II sshd[6726]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 00:36:26 Katie-II sshd[6726]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:28 Katie-II sshd[6726]: Failed password for root from 61.178.14.125 port 42286 ssh2
Feb  5 00:36:32 Katie-II sshd[6728]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 00:36:32 Katie-II sshd[6728]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:34 Katie-II sshd[6728]: Failed password for root from 61.178.14.125 port 43051 ssh2
Feb  5 00:36:37 Katie-II sshd[6730]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 00:36:37 Katie-II sshd[6730]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:40 Katie-II sshd[6730]: Failed password for root from 61.178.14.125 port 43647 ssh2
Feb  5 00:36:43 Katie-II sshd[6732]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 00:36:43 Katie-II sshd[6732]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:46 Katie-II sshd[6732]: Failed password for root from 61.178.14.125 port 44265 ssh2
Feb  5 00:36:49 Katie-II sshd[6737]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 00:36:49 Katie-II sshd[6737]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:51 Katie-II sshd[6737]: Failed password for root from 61.178.14.125 port 44829 ssh2
Feb  5 00:36:57 Katie-II sshd[6758]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 00:36:57 Katie-II sshd[6758]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125  user=root
Feb  5 00:36:58 Katie-II sshd[6758]: Failed password for root from 61.178.14.125 port 45363 ssh2
```

I'm being attacked?? How do i stop such attacks?
The attack also consisted of failed logins from a few usernames:
```
Feb  5 17:14:32 Katie-II sshd[2831]: Invalid user linux from 61.178.14.125
Feb  5 17:14:32 Katie-II sshd[2831]: pam_unix(sshd:auth): check pass; user unknown
Feb  5 17:14:32 Katie-II sshd[2831]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125 
Feb  5 17:14:34 Katie-II sshd[2831]: Failed password for invalid user linux from 61.178.14.125 port 39222 ssh2
Feb  5 17:14:37 Katie-II sshd[2833]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 17:14:37 Katie-II sshd[2833]: Invalid user fedora from 61.178.14.125
Feb  5 17:14:37 Katie-II sshd[2833]: pam_unix(sshd:auth): check pass; user unknown
Feb  5 17:14:37 Katie-II sshd[2833]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125 
Feb  5 17:14:39 Katie-II sshd[2833]: Failed password for invalid user fedora from 61.178.14.125 port 39634 ssh2
Feb  5 17:14:43 Katie-II sshd[2835]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 17:14:43 Katie-II sshd[2835]: Invalid user ubuntu from 61.178.14.125
Feb  5 17:14:43 Katie-II sshd[2835]: pam_unix(sshd:auth): check pass; user unknown
Feb  5 17:14:43 Katie-II sshd[2835]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125 
Feb  5 17:14:45 Katie-II sshd[2835]: Failed password for invalid user ubuntu from 61.178.14.125 port 40064 ssh2
Feb  5 17:14:49 Katie-II sshd[2837]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 17:14:49 Katie-II sshd[2837]: Invalid user apache from 61.178.14.125
Feb  5 17:14:49 Katie-II sshd[2837]: pam_unix(sshd:auth): check pass; user unknown
Feb  5 17:14:49 Katie-II sshd[2837]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.14.125 
Feb  5 17:14:51 Katie-II sshd[2837]: Failed password for invalid user apache from 61.178.14.125 port 40392 ssh2
Feb  5 17:14:54 Katie-II sshd[2839]: reverse mapping checking getaddrinfo for 125.14.178.61.dail.lz.gs.dynamic.163data.com.cn [61.178.14.125] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  5 17:14:54 Katie-II sshd[2839]: Invalid user tim from 61.178.14.125
```

There are far more, but i shant paste it all

---

### Post by Bachstelze on 2010-02-06
> **Monotoko said:**
> 
I'm being attacked?? How do i stop such attacks?
The attack also consisted of failed logins from a few usernames:


You could use fail2ban, which automatically rejects connections from a host after failed attempts. Personally, though, I don't bother with it. If they enjoy running into a wall, let them, I couldn't care less. ;)

---

### Post by llawwehttam on 2010-02-06
If you have a decent password then don't worry. In fact laugh at them. Also install GUFW as your firewall gui and block port 22 for ssh unless you need it.
Unless you have an unlocked root account then no password will get in to root so you can laugh at their stupidity.

Also for a laugh you could set up a small PC to DOS 61.178.14.125 ( unless its illegal in which case I deny all responsibility)

---

### Post by Bachstelze on 2010-02-06
> **llawwehttam said:**
> If you have a decent password then don't worry. In fact laugh at them.

Hmm, not really. You can if you disabled password-authentication and optionally restricted key-based authentication to trusted IPs.

> **llawwehttam said:**
> Unless you have an unlocked root account then no password will get in to root so you can laugh at their stupidity.

Again, not really. Ubuntu uses sudo by default, and all sudo needs to get root provileges is the *user*'s password.

---

### Post by 2hot6ft2 on 2010-02-06
If you're using keys and have passwords disabled then you should be ok since they are just trying user names and passwords but you may pick up a couple more ways to secure your server here:
[Top 20 OpenSSH Server Best Security Practices]("http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html")

---

### Post by Teunis on 2010-02-06
The moment port 22 (or any port really) is open you'll get attempts to enter, it's a fact of life.

Depending on your use for that ssh access limiting access to a single IP is one of the ways to stop these idiots.(But not 100% water tight)

---

### Post by gmargo on 2010-02-06
You could use a different port from port 22.  That's what I do.  Also definitely don't allow login by password on any outward facing machine.

---

### Post by ushills on 2010-02-06
also you could install denyhosts, by uploading the hacker ip's the community can benefit from you reporting their attempts.

---

### Post by pbrane on 2010-02-06
I had this problem too. Changing sshd default port and using keys instead of password login has made a huge difference. Don't forget to disable password login after setting up ssh keys.

---

### Post by synapsys on 2010-02-06
> **pbrane said:**
> I had this problem too. Changing sshd default port and using keys instead of password login has made a huge difference. Don't forget to disable password login after setting up ssh keys.

Agreed. Use a port higher than 1000 e.g. port #2222
Use RSA key authentication instead of passwords.

---

### Post by _uli on 2010-02-08
I ran across this simple script that is set up to read auth.log every 2 minutes and checks for failed ssh login attempts. If more than four failed attempts are detected it then adds the remote ipaddress in a drop rule to iptables.

[http://www.pbxer.com/simple-shell-script-to-block-failed-ssh-attempts/](http://www.pbxer.com/simple-shell-script-to-block-failed-ssh-attempts/)

I've had it running for a couple of days, and it seems to work like a charm. Still you should have a strong password and disable ssh access from root.

---

### Post by synapsys on 2010-02-10
> **_uli said:**
> I ran across this simple script that is set up to read auth.log every 2 minutes and checks for failed ssh login attempts. If more than four failed attempts are detected it then adds the remote ipaddress in a drop rule to iptables.

[http://www.pbxer.com/simple-shell-script-to-block-failed-ssh-attempts/](http://www.pbxer.com/simple-shell-script-to-block-failed-ssh-attempts/)

I've had it running for a couple of days, and it seems to work like a charm. Still you should have a strong password and disable ssh access from root.

Thanks for the link! Very useful script.

---

