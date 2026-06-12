---
title: "vsftpd / PAM / NSS issues"
date: 2011-08-18
forum: General Help
---

### Post by mg9189 on 2011-08-18
OK, I apologize in advance if this is the wrong place for this thread. 
 
I am having a problem getting vsftpd running correctly using PAM and NSS on Ubuntu 10.04.3 Server 64 bit. We use virtual users that are contained in a Postgres database.
 
These libraries do work for SSH, Telnet and our shell console replacement. They worked for everything running on Ubuntu 9.04 Server 32 bit as well.
 
Now, to the symptoms. When I try to ftp to the server using a valid login (works on the console and through telnet), I get this from FileZilla:
 
```
 
Trace: CControlSocket::DoClose(64)
Trace: CControlSocket::DoClose(64)
Status: Connecting to 192.168.30.73:21...
Status: Connection established, waiting for welcome message...
Trace: CFtpControlSocket::OnReceive()
Response: 220 Sentry Power Manager
Trace: CFtpControlSocket::SendNextCommand()
Command: USER admn
Trace: CFtpControlSocket::OnReceive()
Response: 331 Please specify the password.
Trace: CFtpControlSocket::SendNextCommand()
Command: PASS ****
Trace: CRealControlSocket::OnClose(0)
Trace: CControlSocket::DoClose(64)
Trace: CFtpControlSocket::ResetOperation(66)
Trace: CControlSocket::ResetOperation(66)
Error: Could not connect to server
Trace: CFileZillaEnginePrivate::ResetOperation(66)
 

```
 
In the auth.log I see this error:
 
```
 
<date> ubuntu  vsftpd:  PAM unable to dlopen(/lib/security/pam_spm.so): libsasl2.so.2: failed to map segment from shared object: Cannot allocate memory
<date> ubuntu  vsftpd:  PAM adding faulty module: /lib/security/pam_spm.so

```
 
In kern.log (and syslog):
 
```
 
<date> ubuntu kernel: [ 7102.179824] vsftpd[16650]: segfault at 940 ip 00007f1f3fc154e0 sp 00007fff1798fdf0 error 4 in libpthread-2.11.1.so[7f1f3fc10000+18000]

```
 
There is a comment in the source code at each entry point in the shared object, and none of the comments of either the NSS or PAM shared objects print out. However, every other security triggering event works fine.
 
I am at a loss to explain this and would appreciate some advice / help. 
 
I am not a novice at moving around Ubuntu, but the use of PAM and NSS is new to me, so I feel like one at the moment. I am not exactly an expert either ...
 
[SIZE=1][COLOR=#800080]
[/COLOR][/SIZE]

---

### Post by mg9189 on 2011-08-19
I am doing this in a virtual machine, and have increased memory based on some other google search suggestions of similar problems.  I don't think lack of memory is the problem.  
 
I have been playing with /etc/pam.d/vsftpd and have noticed that I change the name of the shared module that claims to not allocate memory.  So, instead of "libsasl2.so.2: failed to map segment from share object:  Cannot allocate memory" errors, I can get libgnutls.so.26 or libk5crypto.so.3 objects producing the exact same error.
 
I suppose that I just don't understand what the difference between using ssh is from ftp with regards to PAM and NSS configurations.
 
```
 
free -m
             total       used       free     shared    buffers     cached
Mem:          2009        307       1702          0         11         79
-/+ buffers/cache:        216       1792
Swap:         5883          0       5883


```

---

### Post by mg9189 on 2011-08-22
I just tried the same code on Ubuntu 9.04 Server 32bit.  IE, the same PAM, NSS libraries using my Postgres database tables for user authentication and I was able to log in using vsftpd. The pam.d configuration files are the same, the vsftpd conf file is the same, the code to build my custom shared objects are the same, other than some versions - the packages loaded to the system are the same.  My objects were compiled with Ubuntu 9.04 for this test.
 
I need this work on Ubuntu 10.04 Server 64bit though.  Based on serious PAM bug earlier this year, I have even tried using "apt-get install libpam-modules=1.1.1-2ubuntu2".  This did not work and I have returned it back to the correct version.  Yes, I used Ubuntu 10.04 64bit to compile the shared objects for this test.
 
I tried using pure-ftpd, but again, I still run into the fact that the PAM library will not load at all.  The error is different as I just get absolutely no logs about PAM instead of the failure.  I also ran into issues creating users, and gave up.
 
I checked the shared objects using ldd to make sure all the dependancies are there, and they are. 
 
Something is causing the pam_spm.so shared object to fail to load.  It appears the shared object libsasl2.so.2 causes the crash with the error "failed to map segment from shared object:  Cannot allocate memory".  I have plenty of memory, so I do not know what to do to solve this problem.
 
Anyone?

---

