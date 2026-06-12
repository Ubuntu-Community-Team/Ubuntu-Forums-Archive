---
title: "Need help in integrating squid and samba"
date: 2009-08-15
forum: General Help
---

### Post by Avinash.Rao on 2009-08-15
Hi,

I am using Ubuntu 8.04 Server 64-bit edition with Ubuntu Desktop. I have installed samba using apt-get install samba command. 

smb.conf 
    workgroup = abc
    server string = Samba for abc
    log level = 1
    interfaces = eth0
    bind interfaces only = True

    log file = /var/log/samba/log.%m
    max log size = 1000

    domain logons = yes
    os level = 65
    prefered master = yes
    domain master = yes
    local master = yes

    add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody %u
    dns proxy = No
    hosts allow = 127. 10.10.10.
    wins support = Yes
    passdb backend = tdbsam
    
    encrypt passwords = true
    smb passwd file = /etc/samba/smbpasswd
    security = user
    netbios name = human
    ;username map = /etc/samba/smbusers   

[homes]
    comment = Home Dir
    read only = NO
    browseable = NO
    valid users = %S
    path = %H
    directory mask = 0700
    create mask = 0700


dpkg -l | grep samba 
ii  samba 3.0.28a-1ubuntu4.8 a LanManager-like file and printer server fo
ii  samba-common 3.0.28a-1ubuntu4.8 Samba common files used by both the server 
ii  samba-doc 3.0.28a-1ubuntu4.8 Samba documentation

Samba is working properly and am able to login to the domain and access files without any problems! My requirement is to restrict few samba users who login to the domain from accessing the internet through squid on few hours of the day. I read the official how to documentation and it says i have to compile samba with ntlm. Now to do this should i uninstall Samba and compile it?  

Also, i am not able to list users nor get any information using wbinfo command. 

avi@human:~$ wbinfo -t
checking the trust secret via RPC calls failed
error code was NT_STATUS_DOMAIN_CONTROLLER_NOT_FOUND (0xc0000233)
Could not check secret
avi@human:~$ wbinfo -u
Error looking up domain users
avi@human:~$ 


Kindly help
Avinash

---

### Post by Avinash.Rao on 2009-08-15
Can anybody help me with the procedure to compile samba to integrate with squid proxy. I have downloaded squid 3.0.28a from the samba site and am following the instructions given in that site to Verifying Samba's PGP Signature and am getting the following error.

root@human:~/samba-3.0.28a# gpg --verify samba-3.0.28a.tar.asc 
gpg: no signed data
gpg: can't hash datafile: file open error
root@human:~/samba-3.0.28a#

---

### Post by Avinash.Rao on 2009-08-16
Hi,

I would like to know the correct samba binaries that has to be downloaded if i have to compile samba. I have downloaded samba 3.0.28a from  [http://us1.samba.org/samba/ftp/stable/](http://us1.samba.org/samba/ftp/stable/) and even the .asc file from the same location.

I am not able to find any packages in the binary packages directory in this site so i downloaded the samba install files from  [http://us1.samba.org/samba/ftp/stable/](http://us1.samba.org/samba/ftp/stable/) directory.

I am not able to verify the downloaded file.

gpg --verify samba-3.0.28a.tar.asc samba-3.0.28a.tar.gz
gpg: Signature made Saturday 08 March 2008 09:28:28 PM IST using DSA key ID 6568B7EA
gpg: BAD signature from "Samba Distribution Verification Key <samba-bugs@samba.org>"


can anybody help
Avinash

---

### Post by dmizer on 2009-08-16
> **Avinash.Rao said:**
> I read the official how to documentation and it says i have to compile samba with ntlm. Now to do this should i uninstall Samba and compile it? 

The Samba server available by default in the Ubuntu repositories is compiled with ntlm support. No need to compile.

---

### Post by Avinash.Rao on 2009-08-17
thank you, actually i wanted to ask the correct procedure to compile squid to integrate with samba. According to the documentation,
--------
Samba 3.x
---------
Things are much easier under the 3.x versions of Samba. Smbd is no longer required to manage the machine's trust account, and  there is no need to patch any utilities.

The Samba team has incorporated functionality to change the machine trust account password in the new "net" command.  A simple daily cron job scheduling "net rpc changetrustpw" is all that is needed.

My requirement with samba is PDC, winxp clients, users home directories are mapped as they login to the domain, a common share for all users and a printer if needed.  My question, is which is correct version of squid I should download and compile for samba 3.0.28a so that all normal operations with samba and squid work normally.


> **dmizer said:**
> The Samba server available by default in the Ubuntu repositories is compiled with ntlm support. No need to compile.

---

### Post by dmizer on 2009-08-17
> **Avinash.Rao said:**
> thank you, actually i wanted to ask the correct procedure to compile squid to integrate with samba.

I don't know how to help you on that. I only answered what I am capable of answering. Sorry.

---

### Post by Avinash.Rao on 2009-08-17
Hi,

I am trying to get squid working from [http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm](http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm)

The idea is to restrict or allow samba domain users from accessing the internet at certain times. But, the basic winbindd functionality "wbinfo -t": is not successful

wbinfo -t
checking the trust secret via RPC calls failed
error code was NT_STATUS_DOMAIN_CONTROLLER_NOT_FOUND (0xc0000233)
Could not check secret

Even, wbinfo -a mydomain\\myuser%mypasswd is unsuccessful

How do i get this working?

Thanks
Avinash

---

