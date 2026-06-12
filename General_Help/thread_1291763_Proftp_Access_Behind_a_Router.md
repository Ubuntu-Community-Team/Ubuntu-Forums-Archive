---
title: "Proftp Access Behind a Router"
date: 2009-10-15
forum: General Help
---

### Post by age99 on 2009-10-15
Hi, I am trying to setup FTP for sharing large files with some clients on my Ubuntu box.  I downloaded and installed poftpd, and even grabbed GADMIN.  I followed the instructions, created a user and directory and generated the following config file:

```

ModulePath /usr/lib/proftpd
LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c
LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
LoadModule mod_dynmasq.c
LoadModule mod_ifsession.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTP Server"
ServerAdmin email@example.org
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 60000 60100
MasqueradeAddress XX.XX.XXX.XXX
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
#TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
#TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
#TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser crappy
  DenyALL
</Limit>

<Anonymous /projects/antamina/anta_sub/anta_ftp>
User crappy
Group ftpuser
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>


```

I updated the generic config with:
```
PassivePorts 60000 60100
MasqueradeAddress XX.XX.XXX.XXX
```

XX.XX.XXX.XXX being my IP address that I confirmed with ichicken.com.

I can access it no problem with other machines on the LAN, but nothing outside.  I also forwarded the PassivePorts on my DI-625 router, but without success.
Firstly, I want to know if I am accessing the the address correctly through ftp:

```
ftp XX.XX.XXX.XXX
```

Is that correct?

If so, what else am I doing wrong?

Thanks

---

### Post by P4man on 2009-10-15
Are passive ports the port(s) the ftp server is listening too? I though TCP ports where capped at 16000 something. You have yours at 60000. Try a lower port ?

To access it you would have to add the nonstandard port:

ftp 123.456.789.012:11111

where 11111 would be your port and the rest your public IP obviously.

---

### Post by ded3d44 on 2009-10-15
Not an answer to your question but I would advice you to use secure FTP as when using normal FTP passwords are send in plain text across the internet.

Just my paranoia 2 cents.

---

### Post by age99 on 2009-10-15
I tried a lower port, but without any change.  When I try to specify a specific port with a colon (ex: 123.456.789.012:11111) there is an immediate response saying "Unknown Host".  Am I doing something wrong?

If I try to use any number of port, including 21, it just waits a while then fails.  


ded3d44, I am hoping to get it working first, then worry about improving the security.

---

### Post by P4man on 2009-10-15
> **age99 said:**
> I tried a lower port, but without any change.  When I try to specify a specific port with a colon (ex: 123.456.789.012:11111) there is an immediate response saying "Unknown Host".  Am I doing something wrong?


If your'e testing locally, you have to use the local IP address. I assume you're behind a router, so the machine will have a local IP address such as 192.168.1.65 or something. (find out by right clicking the network manager, and click connection info.

---

### Post by age99 on 2009-10-15
I tested it locally and was able to logon and view the files in the directory I had setup.  I (or others) am not able to access it remotely.

I was trying with FileZilla as well, without any luck.

---

### Post by P4man on 2009-10-15
> **age99 said:**
> I tested it locally and was able to logon and view the files in the directory I had setup.  I (or others) am not able to access it remotely.

I was trying with FileZilla as well, without any luck.

for it to work remotely, you need a few things.
1. it has to work locally :)
2. you need port forwarding on your router. Forward whatever port you configured for your FTP server to the local IP address of the FTP server. You should do that in the web interface of your router.
3. Your ISP may not block that port. Many ISPs block inbound ports below 1024, so select one above 1024 (but below 16000).

4. you need to access the server remotely using the public IP your ISP assigned you. You can find out using [www.whatismyip.com](www.whatismyip.com).

---

### Post by P4man on 2009-10-15
edit: by locally I mean a computer connected on the same network. I dont mean on the same computer!

---

### Post by age99 on 2009-10-15
I was testing it on a separate machine, behind the same router and using the local IP address.  

I have now managed to access it using the external IP address.  The only thing I changed was to comment out the line:

Passiveports

Now I am able to access with FileZilla, and it is using port 21, which was already being forwarded through the router.

Thanks for your help.

---

### Post by djliamtate on 2009-10-23
> **P4man said:**
> for it to work remotely, you need a few things.
1. it has to work locally :)
2. you need port forwarding on your router. Forward whatever port you configured for your FTP server to the local IP address of the FTP server. You should do that in the web interface of your router.
3. Your ISP may not block that port. Many ISPs block inbound ports below 1024, so select one above 1024 (but below 16000).

4. you need to access the server remotely using the public IP your ISP assigned you. You can find out using [www.whatismyip.com](www.whatismyip.com).

I have all of this working but still not cannot FTP to the linux box. I have Proftpd set up on ubuntu server and can access it using the private 192.xxx ip address but not using the hostname or external ip address. All PC's and Mac's are on the same network, I have been unable to test externally. Can anyone help at all? It has been driving me nuts now. Port forwarding is set up from my NetGear WRN2000 to port 1980 and I have passiveports 10000 to 111000 open but still no joy.

All I get is:

[R1] Connect to House
[R1] Connection refused
[R1] Connection lost.
[R1] Reconnect #19 to House in 30 seconds.

---

