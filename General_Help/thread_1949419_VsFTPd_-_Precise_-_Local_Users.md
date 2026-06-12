---
title: "VsFTPd - Precise - Local Users"
date: 2012-03-30
forum: General Help
---

### Post by wightman.p on 2012-03-30
I've been using VsFTPd for a while, and am now attempting to get it working on Precise.  The version of VsFTPd is 2.3.5

Anonymous works fine.

I have set LOCAL_ENABLE=YES, but can't login as a local user - I get the following results


> localuser@precise:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 2.3.5)
Name (localhost:localuser): anonymous
331 Please specify the password.
Password:
[B]230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.[/B]
ftp> 

localuser@precise:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 2.3.5)
Name (localhost:localuser): localuser
331 Please specify the password.
Password:
[B]421 Service not available, remote server has closed connection
Login failed.
No control connection for command: No such file or directory[/B]
ftp> 

---

### Post by jtupulis on 2012-04-18
I have the same.

---

### Post by misterbiskits on 2012-06-29
Me too Ubuntu 12.04 64-bit Server version.  Exactly the same, anonymous works fine, local users connect, but fail after typing in the correct password.
> 
331 Please specify the password.
Password:
421 Service not available, remote server has closed connection
Login failed.
No control connection for command: No such file or directory
What service is unavailable?  Since anonymous works fine, it's got to have something to do with checking the credentials? 

/var/log/auth.log has PAM errors regarding /lib/security/pam_smbpass.so 
> 
Jun 29 11:26:32 HomeServer vsftpd: PAM unable to dlopen(pam_smbpass.so): /lib/security/pam_smbpass.so: cannot open shared object file: No such file or direc$
Jun 29 11:26:32 HomeServer vsftpd: PAM adding faulty module: pam_smbpass.soThis file doesn't exist in that location.  it is actually found at
> /lib/x86_64-linux-gnu/security/pam_smbpass.so

Where to go from here?

---

### Post by misterbiskits on 2012-06-29
from the FAQ [https://security.appspot.com/vsftpd/FAQ.txt](https://security.appspot.com/vsftpd/FAQ.txt)
> Q) Help! Local users cannot log in.> A2) vsftpd tries to link with PAM. (Run "ldd vsftpd" and look for libpam to find out whether this has happened or not). If vsftpd links with PAM, then you will need to have a PAM file installed for the vsftpd service. There is a sample one for RedHat systems included in the "RedHat" directory - put it under /etc/pam.dldd vsftpd gives me the following output:
> user@server:/$ ldd vsftpd
ldd: ./vsftpd: No such file or directory
user@server:/etc$ ldd vsftpd
ldd: ./vsftpd: not regular file
i don't know what that means.
> Is the user's shell in /etc/shells?I think so.
>  If you have shadowed passwords, does your system have a "shadow.h" file in the include path?I don't know what shadowed passwords are but "shadow.h" does not exist on my system.

> A4) If you are not using PAM, then vsftpd will do its own check for a valid user shell in /etc/shells. You may need to disable this if you use an invalid shell to disable logins other than FTP logins. Put check_shell=NO in your /etc/vsftpd.conf.Done and restarted. No effect.

---

### Post by misterbiskits on 2012-07-02
Been hammering away at this for days and days.  All solutions have failed until:

[http://unix.stackexchange.com/questions/37539/vsftpd-fails-pam-authentication](http://unix.stackexchange.com/questions/37539/vsftpd-fails-pam-authentication)

> Whew.  I solved the problem.  It amounts to a config but within [COLOR=Red]/etc/pam.d/vsftpd[/COLOR]
  Because ssh sessions succeeded while ftp sessions failed, I went to
  /etc/pam.d/vsftpd, removed everything that was there and instead  placed the contents of ./sshd to match the rules precisely.  All worked!
  By method of elimination, I found that the offending line was:
      [COLOR=Red]auth       required     pam_shells.so   [/COLOR]
Removing it allows me to proceed.  
  Tuns out, "pam_shells is a PAM module that only allows access to the  system if the users shell is listed in /etc/shells."  I looked there and  sure enough, no bash, no nothing.  This is a bug in vsftpd  configuration in my opinion as nowhere in the documentation does it have  you editing /etc/shells.  Thus default installation and instructions do  not work as stated.  
I commented out the offending line (shown above) in /etc/pam.d/vsftpd and now it works.  I am not very good at this, obviously - are there any security issues with commenting out this line that I should be aware of?

---

