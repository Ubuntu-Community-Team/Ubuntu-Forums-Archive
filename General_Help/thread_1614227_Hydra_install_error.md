---
title: "Hydra install error"
date: 2010-11-05
forum: General Help
---

### Post by U_buntu on 2010-11-05
Trying to install hydra 5.8 but I'm getting an error I don't understand after typing "make"

make
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-smtpauth-ntlm.o hydra-firebird.o hydra-afp.o hydra-ncp.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lpq -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib
/usr/bin/ld: cannot find -lpq
collect2: ld returned 1 exit status
make: *** [hydra] Error 1

---

### Post by chronos00 on 2011-01-19
From [here]("http://edwincastillo.com/archives/95") I found an answer to our question:

sudo apt-get install libpq-dev

Regards!

---

### Post by Drezard on 2011-02-20
Good tutorial here on how to install Hydra 6.1  (latest version) the brute forcing tool:

[http://www.rootedbox.net/?p=37]("http://www.rootedbox.net/?p=37")

---

