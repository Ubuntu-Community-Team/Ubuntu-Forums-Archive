---
title: "SSH setup"
date: 2012-04-18
forum: General Help
---

### Post by Alphamonkey on 2012-04-18
Hi, I am trying to set up SSH on my desktop so that I can connect and view files while away with my laptop. I followed a tutorial on Hak5 [http://www.youtube.com/watch?v=yP0asZEIwN8&feature=g-all-u&context=G2635e4dFAAAAAAAABAA](http://www.youtube.com/watch?v=yP0asZEIwN8&feature=g-all-u&context=G2635e4dFAAAAAAAABAA) but after I installed and edited the config file I got some error message I will post below. Could anybody tell me how to resolve these issues. Thanks.

/etc/ssh/ssh_config: line 20: Bad configuration option: AllowTcpForwarding
/etc/ssh/ssh_config: line 23: Bad configuration option: AllowUsers
/etc/ssh/ssh_config: line 24: Bad configuration option: LoginGraceTime
/etc/ssh/ssh_config: line 25: Bad configuration option: ClientAliveInterval
/etc/ssh/ssh_config: line 26: Bad configuration option: ClientAliveCountMax
/etc/ssh/ssh_config: line 27: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: terminating, 6 bad configuration options

---

### Post by wallaroo on 2012-04-19
Looking at my configuration, those commands are not set under 'Host *' in 'ssh_config' but are instead set separately in file 'sshd_config'.

---

### Post by codemaniac on 2012-04-19
Please refer to the community documentation on OpesSSH server .
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

