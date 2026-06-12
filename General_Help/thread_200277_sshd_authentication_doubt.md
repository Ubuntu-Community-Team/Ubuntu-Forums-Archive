---
title: "sshd authentication doubt"
date: 2006-06-20
forum: General Help
---

### Post by [S|G] on 2006-06-20
I have edited the sshd_config for a server and have set these options:
```

PasswordAuthentication no
RSAAuthentication yes
PubkeyAuthentication yes

```

I did that in order to disable login using passwords and instead use public keys. Whenever I connect to the server, it doesn't allow me to login using conventional password and works when I use my key, which was exactly my intent. 

However, when I do "lastb|more" there are still a lot (and I mean, a LOT) of brute-force attacks trying to login by supplying a username/password. Shouldn't they be unable to even try to give a password? Is there any chance they might login using a password? Did I forget to disable something?

Thanks!

---

### Post by RAOF on 2006-06-20
I just checked my logs; I'm running the same ssh setup (key-based authentication only).  I don't have anything in my lastb, and my auth.log says people have tried brute-force.  So it doesn't look like that's normal.

The only thing I might check is that you've got
"ChallengeResponseAuthentication no"
in your sshd_config.  Apart from that, I can't see any difference in my sshd_config file that might explain the change.

---

### Post by thasheep on 2006-06-20
I also deny all password authentication and have tons of password based login attempts. They all fail. sshd denies all attempts at password logging in (even if they guess a correct username/password) because that how we've configured it. However, it allows people to attempt to log in with password so as not to disclose that a public key is required. The dickheads who try to log into out computer don't know whether they're just guessing the wrong passwords or whether it's pointless to guess a password in the first place. The less they know the better.
btw, 'grep sshd /var/log/auth.log /var/log/auth.log.0' and 'zgrep sshd /var/log/auth.log.?.gz' will show all logged attempts (accepted and rejected) in order of most to least recent. If you want to check just for attempts to log in as a particular user, add '| grep $USERNAME' to the end of it. Eg,
```
grep sshd /var/log/auth.log | grep $USERNAME  # checks for current user
grep sshd /var/log/auth.log | grep thasheep  # checks for attempts as thasheep
```
If you'd like to limit which users can login with ssh, you can add the line AllowUsers to sshd_config. Do not allow root login attempts (user sudo/su if needed) and also, you should only need one of rsa and dsa authentication. Here's my /etc/ssh/sshd_config (usernames changed :p)
```
Port 22
Protocol 2
ServerKeyBits 2048
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 60
PermitRootLogin no
RSAAuthentication no
PubkeyAuthentication yes
PasswordAuthentication no
PermitEmptyPasswords no
Compression yes
KeepAlive yes
ClientAliveInterval 30
ClientAliveCountMax 4
Subsystem sftp /usr/lib/misc/sftp-server #Allow sftp
AllowUsers userone usertwo
```

---

### Post by [S|G] on 2006-06-20
Thanks for both responses :)
I have checked my sshd_config and found that UsePAM was on, and have turned it off now. That might have been the source of lastb messages. I have also set AllowUsers in order to have a bit more of peace of mind.

---

