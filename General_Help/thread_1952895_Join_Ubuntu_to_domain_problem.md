---
title: "Join Ubuntu to domain problem"
date: 2012-04-05
forum: General Help
---

### Post by teriyaki-89 on 2012-04-05
Hi everybody i can't join to domain. I installed and configured samba, winbind, kerberos 
and when i execute on termainal **net join -S 10.2.1.4 -U Administrator**

Enter Administrator's password:
Failed to join domain: Failed to set account flags for machine account (NT_STATUS_ACCESS_DENIED)
ADS join did not work, falling back to RPC..

I looked over google and can't find possible solution for this, help please

---

### Post by wyliecoyoteuk on 2012-04-05
There could be a lot of reasons.
A couple of common ones that catch people out:
domain, workgroup and netBIOS computer names need to be enterd in Uppercase in /etc/samba/smb.conf (I think the Kerberos realm as well, can't remember)
LDAP entries are sometimes case sensitive too.
The time on the pc must be within a few minutes of the server.

---

### Post by teriyaki-89 on 2012-04-05
hi thanks for reply. 
I watched in smb.conf for domain, workgroup and netBIOS computer entries are in UPPERCASE
date offset is  0.000563
[B]where to look for ldap entries in my computer ?
[/B]kinit also works

---

### Post by wyliecoyoteuk on 2012-04-05
If you aren't using LDAP authentication, not a problem.

Must be something else.

could be the username, windows 2008 etc needs domainname\username or username@domainname for logins.

e.g. mydomain\user, or [email]user@mydomain.local[/email]

---

### Post by teriyaki-89 on 2012-04-05
**i think there is no problem with authentification cause the password passes well**
And when i type wrong password i get like this 
Could not connect to server 10.2..1.4
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE

---

### Post by wyliecoyoteuk on 2012-04-05
what version of windows? 2003 or 2008?
does the computer account exist on the server?

---

### Post by teriyaki-89 on 2012-04-05
windows server 2008
from the side of AD the computer account was created, anyway i can change my computer name to another

---

### Post by teriyaki-89 on 2012-04-06
now i do this like ** net  join -U Administrator  -S 10.2.1.4 -d 10 **

and my error is like 


netr_ServerReqChallenge: struct netr_ServerReqChallenge
          out: struct netr_ServerReqChallenge
              return_credentials       : *
                  return_credentials: struct netr_Credential
                      data                     : 0000000000000000
              result                   : NT_STATUS_INVALID_COMPUTER_NAME


What is the problem with my computer name?? I have installed samba4 on ubuntu 11.10

---

### Post by wyliecoyoteuk on 2012-04-06
It might require the full name, or the name might differ in some way from the account on the server.

e.g. COMPUTER.DOMAIN.LOCAL or COMPUTER.DOMAIN.COM


also administrator should be all lowercase, and might need to be Fully Qualified, e.g  [email]administrator@yourdomain.local[/email] or yourdomain\administrator

---

### Post by teriyaki-89 on 2012-04-15
the error is still present (((

**net  join -U Administrator -S 10.2.1.4  -d 10**

.......
[2012/04/16 09:25:42.409354,  1] utils/net_rpc.c:205(run_rpc_command)
  rpc command function failed! (NT_STATUS_INVALID_COMPUTER_NAME)
[2012/04/16 09:25:42.410817, 10] rpc_client/rpc_transport_np.c:81(rpc_transport_np_state_destructor) 
.......
Can give the full log
** smbd -V**
Version 3.5.11

kinit works well

**cat /etc/hostname** 
MY-DESKTOP

127.0.1.1 MY-DESKTOP.DOMAIN.LOCAL MY-DESKTOP
10.7.59.45 MY-DESKTOP.DOMAIN.LOCAL MY-DESKTOP

so what is the problem with samba? I Have already joined windows machine. Same problem with likewise

Why is it so tough with my ubuntu?

---

### Post by dcstar on 2012-04-16
> **teriyaki-89 said:**
> 
..........
Why is it so tough with my ubuntu?

Did you read this?:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by wyliecoyoteuk on 2012-04-16
I found some info about NetBIOS name syntax.(SMB is based on NetBIOS and WINS)
Apparently hyphens do not always work.

---

### Post by teriyaki-89 on 2012-04-16
i ve joined one windows one one redhat machine with hyphens and it worked. But my ubuntu 11.10 seems not to understand. So i changed my hostname and netbios names to MYDESKTOP and i got another error like 
[B]
[2012/04/16 15:27:35.580170, 10] libads/ldap.c:62(ldap_open_with_timeout)
  Opening connection to LDAP server 'DC.DOMAIN.LOCAL:389', timeout 15 seconds
Failed to join domain: failed to connect to AD: Server not found in Kerberos database[/B]

I watched the link [https://help.ubuntu.com/community/Ac...ryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")
and didn't understand if i have to install kadmin to connect to ad with server not user account?
Something's wrong with my kerberos ? kinit and klist seem to work

What's interesting [B]
net ads join [/B]and** net join **returned error
 [B]Failed to join domain: failed to connect to AD: Server not found in Kerberos database
[/B]and** net rpc join **returns
 [B]rpc command function failed! (NT_STATUS_INVALID_COMPUTER_NAME)
rpc_pipe_destructor: closed \netlogon
[/B]

---

### Post by wyliecoyoteuk on 2012-04-16
Sorry, but this is getting way out of my knowledge base.

---

### Post by teriyaki-89 on 2012-04-16
thanks guys for all i was able to use **net ads join DOMAIN.LOCAL** now i am reading how to let domain users login

---

### Post by madverb on 2012-04-16
Why didn't you use PowerBroker or Centrify? [http://www.beyondtrust.com/Products/PowerBroker-Identity-Services-Open-Edition/](http://www.beyondtrust.com/Products/PowerBroker-Identity-Services-Open-Edition/) [http://www.centrify.com/express/free-active-directory-tools-for-linux-mac.asp](http://www.centrify.com/express/free-active-directory-tools-for-linux-mac.asp)

---

### Post by teriyaki-89 on 2012-04-16
i tried that but got error with computer name i suppose hyphens in computer names sometimes make errors so i cancelled that. I'l try likewese-open5 later

---

