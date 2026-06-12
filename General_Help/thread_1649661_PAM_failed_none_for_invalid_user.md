---
title: "PAM failed none for invalid user"
date: 2010-12-20
forum: General Help
---

### Post by wolfgangmcq on 2010-12-20
I am trying to authenticate against an LDAP server using PAM. I've gotten it asking the LDAP sever if the credentials are OK, but it still fails the authentication. In /var/log/auth.log, I get:[INDENT]```
Dec  9 14:47:31 Linux-Test sshd[2339]: Invalid user {{user}} from ::1
Dec  9 14:47:31 Linux-Test sshd[2339]: Failed none for invalid user {{user}} from ::1 port 34571 ssh2
Dec  9 14:47:34 Linux-Test sshd[2339]: pam_unix(sshd:auth): check pass; user unknown
Dec  9 14:47:34 Linux-Test sshd[2339]: pam_unix(sshd:auth):  authentication failure; logname= uid=0 euid=0 tty=ssh ruser=  rhost=linux-test 
Dec  9 14:47:34 Linux-Test sshd[2339]: pam_winbind(sshd:auth): getting password (0x00000388)
Dec  9 14:47:34 Linux-Test sshd[2339]: pam_winbind(sshd:auth): pam_get_item returned a password
Dec  9 14:47:38 Linux-Test sshd[2339]: Failed password for invalid user {{user}} from ::1 port 34571 ssh2
```[/INDENT][FONT=Verdana]Where {{user}} is the username.[/FONT]

---

### Post by luvshines on 2010-12-23
Can you post output of /etc/pam.d/common-auth and common-account file (remove the commented out lines)

Also check if you are able to resolve user on your machine```

id <username>

```

---

### Post by wolfgangmcq on 2010-12-24
I don't have access to the machine right now; when I do I'll check it.

---

### Post by wolfgangmcq on 2011-01-03
```
$ id *<username>*
id: *<username>*: No such user

```(Yes, I did change <username> to the actual username)

common-auth:
```
auth    [success=3 default=ignore]    pam_unix.so nullok_secure
auth    [success=2 default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so
```common-account:
```
account    [success=3 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    [success=2 new_authtok_reqd=done default=ignore]    pam_winbind.so 
account    [success=1 default=ignore]    pam_ldap.so 
account    requisite            pam_deny.so
account    required            pam_permit.so
```

---

### Post by luvshines on 2011-01-04
If user is not resolvable on system, I doubt if he can gain access :(

Can you also post output of following```

cat /etc/nsswitch.conf | egrep "passwd|group|shadow"
```

---

### Post by wolfgangmcq on 2011-01-10
```
$ cat /etc/nsswitch.conf | egrep "passwd|group|shadow"
passwd: files ldap
group: files ldap 
shadow: files ldap
netgroup: files 

```

---

### Post by wolfgangmcq on 2011-01-19
There's been a new development. I changed something (I'm not quite sure what), and now it says, ```

Jan 19 14:25:41 Linux-Test sshd[8926]: Invalid user {{USER}} from ::1
Jan 19 14:25:41 Linux-Test sshd[8926]: Failed none for invalid user{{USER}} from ::1 port 51784 ssh2
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_unix(sshd:auth): check pass; user unknown
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=linux-test 
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan 19 14:25:49 Linux-Test sshd[8926]: Failed password for invalid user {{USER}} from ::1 port 51784 ssh2

```Any clues?

---

### Post by wolfgangmcq on 2011-01-19
There's been a new development. I changed something (I'm not quite sure what), and now it says, ```

Jan 19 14:25:41 Linux-Test sshd[8926]: Invalid user {{USER}} from ::1
Jan 19 14:25:41 Linux-Test sshd[8926]: Failed none for invalid user{{USER}} from ::1 port 51784 ssh2
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_unix(sshd:auth): check pass; user unknown
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=linux-test 
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan 19 14:25:46 Linux-Test sshd[8926]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan 19 14:25:49 Linux-Test sshd[8926]: Failed password for invalid user {{USER}} from ::1 port 51784 ssh2

```Any clues?

---

### Post by wolfgangmcq on 2011-01-19
Sorry about the double post--not sure how that happened.

---

### Post by luvshines on 2011-01-21
Well, if you are trying to configure against LDAP server, why is winbind coming in between.

In my opinion, it should not be there in PAM if you are not using it

How did you configure PAM modules ?
Did you use pam-auth-update for LDAP pam configurations ?

---

### Post by wolfgangmcq on 2011-01-25
I did use pam-auth-update; but I enabled everything because I wasn't sure what I needed. Is this bad?

---

### Post by luvshines on 2011-01-26
I think winbind should not come into picture. Re-configure it with LDAP alone

---

### Post by wolfgangmcq on 2011-01-31
When you say "LDAP alone", do you mean I shouldn't leave Unix Authentication in there either? It seems to me that if I take that one out, it won't let me log on with my local credentials.

---

### Post by luvshines on 2011-01-31
> **wolfgangmcq said:**
> When you say "LDAP alone", do you mean I shouldn't leave Unix Authentication in there either? It seems to me that if I take that one out, it won't let me log on with my local credentials.

Unix Authentication is ofcourse needed :)
I just wanted to get 'winbind' out of PAM files :D

Does it give any option for 'winbind' ?
I think simply purging winbind(if you are not using it) should also chuck winbind out of PAM

---

### Post by wolfgangmcq on 2011-02-03
Got rid of winbind & changed password encryption method to ad, now I get:
```
Feb  3 13:49:43 Linux-Test sshd[27985]: Invalid user {{USER}} from {{0.0.0.0}}
Feb  3 13:49:43 Linux-Test sshd[27985]: Failed none for invalid user {{USER}} from {{0.0.0.0}} port 43892 ssh2
Feb  3 13:49:53 Linux-Test sshd[27985]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 13:49:53 Linux-Test sshd[27985]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost={{host.name}}
Feb  3 13:49:56 Linux-Test sshd[27985]: Failed password for invalid user {{USER}} from {{0.0.0.0}} port 43892 ssh2

```

---

### Post by luvshines on 2011-02-05
Well, now that /etc/nsswitch.conf is correct(files ldap) and PAM is reconfigured for LDAP, it looks to server side issue to me.
Did you setup /etc/ldap.conf correctly ?
Are you able to ldapsearch for that user ?

---

### Post by wolfgangmcq on 2011-02-07
```
$ ldapsearch {{user}}
ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1)

```Which I guess means it can't connect. How do I fix *this*?

---

### Post by luvshines on 2011-02-08
> **wolfgangmcq said:**
> ```
$ ldapsearch {{user}}
ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1)

```Which I guess means it can't connect. How do I fix *this*?

Well, an LDAP server can be setup in many ways for different types of security mechanisms. You'll have to find out how it has been setup.
```

# Basic check on LDAP server
# Check LDAP server is running
service ldap status

# From client/server machines
# Make sure server port is reachable(assuming default port for LDAP is being used)
nc -zv <ldap-server-ip> 389

# If above command fails, maybe server is running in SSL only mode
nc -zv <ldap-server-ip> 689

# Also try ldapsearch with -x (simple bind)
ldapsearch -x -h <ldap-server-ip> -b <ldap-base-dn>
```

If LDAP server is running and for some reason not reachable from client, it will be mostly due client configuration issues

For authentication, you'll have to fix /etc/ldap.conf

For ldapsearch and other utilities, you'll have to fix /etc/ldap/ldap.conf

---

### Post by wolfgangmcq on 2011-02-08
/etc/ldap.conf is fine, but /etc/ldap/ldap.conf was entirely comments. 
```
$ sudo ln -s /etc/ldap.conf /etc/ldap/ldap.conf
$ ldapsearch {{user}}
SASL/EXTERNAL authentication started
ldap_sasl_interactive_bind_s: Unknown authentication method (-6)
    additional info: SASL(-4): no mechanism available: 

```
What now?

---

### Post by luvshines on 2011-02-08
As I said that you would not need /etc/ldap/ldap.conf configurations unless you want to use ldap-utils from the machine.
Did you try ldapsearch with -x parameter ?

---

### Post by wolfgangmcq on 2011-02-17
It just occurred to me--how does pam know where to find the users & groups in the LDAP hierarchy? In the example I was just looking at, an example user was
uid=john,ou=people,dc=example,dc=com
BUT, in our system, it looks more like
CN=Doe\, John,OU=2012,OU=Students,OU=Accounts,DC=example,DC=com

---

### Post by luvshines on 2011-02-17
> **wolfgangmcq said:**
> It just occurred to me--how does pam know where to find the users & groups in the LDAP hierarchy? In the example I was just looking at, an example user was
uid=john,ou=people,dc=example,dc=com
BUT, in our system, it looks more like
CN=Doe\, John,OU=2012,OU=Students,OU=Accounts,DC=example,DC=com

The entry for this user on the LDAP server must also be having an attribute **"uid"**
PAM(by default) will always use **uid** to lookup names from LDAP unless someone has changed the default behavior with parameters in /etc/ldap.conf
When I am bumped with such stuff, I check my /etc/ldap.conf file if it has any issues.
Maybe you want to make sure that if any of the possibles nss_base_* have been defined there, they are pointing to the correct branch of LDAP tree
If you are confident that /etc/ldap.conf is correct, then you can take a tcpdump of the LDAP traffic and check with wireshark what LDAP query is being done by your client and what does server return

---

