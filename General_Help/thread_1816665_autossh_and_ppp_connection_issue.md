---
title: "autossh and ppp connection issue?"
date: 2011-08-02
forum: General Help
---

### Post by donalbane on 2011-08-02
I notice that when I attempt to forward ports using autossh over a ppp 
cellular modem connection, that autossh will lose the link within a 
few (typically less than 10) minutes, and get a couple of connection 
refusal errors on 127.0.0.1:1234 before resuming connection. 
Eventually, I reach the limit of AUTOSSH_MAXSTART, and autossh exits. 
The ppp connection remains up the whole time. I do not see this when 
I just use ssh with ServerAliveInterval and ServerAliveCountMax, nor 
do I see it when I use autossh over a LAN (eth0) connection. 
 
Does anyone know of any issues with autossh and pppd? I am unable to 
find any documentation on autossh besides the README and man pages, 
and I couldn't find a forum for autossh. 
 
I would just use ssh, but ssh does not detect a lost connection while streaming data (possible bug for my version of OpenSSH and kernel: [http://marc.info/?l=openssh-unix-dev&m=121081969105167&w=2](http://marc.info/?l=openssh-unix-dev&m=121081969105167&w=2) while autossh does (with AUTOSSH_LOGLEVEL=6, and a specified log file). 
 
Don

---

