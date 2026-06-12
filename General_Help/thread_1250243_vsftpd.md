---
title: "vsftpd"
date: 2009-08-26
forum: General Help
---

### Post by gh0stc1pher on 2009-08-26
Hello All, 

This is my first post and I'm not exactly sure or comfortable with where I should mention this but here it goes. I have an Ubuntu VM running on top of CentOS and I installed vsftpd in ubuntu and followed the configuration details, a few online tutorials and read the man page (not all of it though :) ). I cannot get a connection to work, I flushed the iptables rules and tried just using "ftp localhost" but it keeps saying connection refused.

I have the vsftpd configuration info here....

anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=NO
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=ftpsecure
ftpd_banner=Access is Restricted
listen=YES
pam_service_name=vsftpd
userlist_enable=YES
tcp_wrappers=YES
pasv_enable=YES
pasv_promiscuous=YES
pasv_min_port=6000
pasv_max_port=7000
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=YES
rsa_cert_file=/etc/vsftpd/vsftpd.pem
rsa_private_key_file=/etc/vsftpd/vsftpd.pem

I used the local client of ftp and externally. I forwarded the ports from the router to the box and am using dyndns to get to the router. I created the ftpsecure user, created the ftpusers group added users to that group and added the appropriate users to the ftpusers_list. I see seomthing in the config about a pam module? I looked at the logs but I can't find any specific entry that really helps me.  Any suggestions on where I should look next?

Thanks and I'm happy to be a part of the forums :D

---

### Post by MartinEve on 2009-08-26
Here's some generic tips, because I don't know the specifics of your setup at the mo.

1.) Is vsftpd *definitely* running?

```

ps ax | grep vsft

```

2.) If you want vsftpd to listen on port 21 it will need to be launched with root permissions as this is a priveleged port

3.) Is vsftpd being launched via inetd or standalone? If inetd, check if any other net daemons can receive connections. If standalone, see point 2 above.

---

### Post by gh0stc1pher on 2009-08-26
I created ftpsecure as an unprivelaged user, but I didn't think about the lower port rights.  I'll look at that and see if that changes it. 

As far as if its running I am sure and I added it with inetd. I'll attempt changing the account permissions and post back.

Thanks a lot

---

### Post by uDavis on 2009-10-27
[QUOTE=MartinEve;7849316]Here's some generic tips, because I don't know the specifics of your setup at the mo.

1.) Is vsftpd *definitely* running?

```

ps ax | grep vsft

```

I try this command and what I get back is.

27850 tty1   S+  0:00 grep vsft.


I have no idea what it means.

---

