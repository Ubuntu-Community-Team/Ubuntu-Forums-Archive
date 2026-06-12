---
title: "Problem with ssh"
date: 2009-09-15
forum: General Help
---

### Post by juzar on 2009-09-15
Hello Everyone,
This is stupid but I made a typo error several times when I tried to ssh into my univ. computer. Now I can't ssh into that particular computer. My ssh is working fine since I can ssh into other computers. 
I tried to remove hosts.deny and then restart the denyhosts daemon. I also re-installed ssh from scratch but these options dnt seem to work. I get the following error when I try to ssh into that computer:
[I]
"ssh -v <computer_ip@domain_name>
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to <domain_name> [<computer_ip>] port 22.
debug1: Connection established.
debug1: identity file ~/.ssh/identity type -1
debug1: identity file ~/.ssh/id_rsa type -1
debug1: identity file ~/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host"[/I]

Any help would be appreciated.
I'm sorry if a similar query has been posted somewhere else. I'm unable to find it so if you know please post the link.

Regards,
Juzar

---

### Post by Yannick Le Saint kyncani on 2009-09-15
Looks like your ~/.ssh/id_rsa.pub is not in the _distant_ ~/.ssh/authorized_keys, so if you cannot connect using a password instead of public key authentification, you will have to add your id_rsa.pub in the server authorized_keys by login locally.

There are excellent ssh docs on the web for that.

---

### Post by juzar on 2009-09-15
Please can you explain how do I do this...

Regards,
Juzar

---

### Post by Yannick Le Saint kyncani on 2009-09-15
> **juzar said:**
> Please can you explain how do I do this...

Google -> id_rsa.pub authorized_keys scp

Might be a good start.

---

### Post by juzar on 2009-09-15
> **Yannick Le Saint kyncani said:**
> Looks like your ~/.ssh/id_rsa.pub is not in the _distant_ ~/.ssh/authorized_keys, so if you cannot connect using a password instead of public key authentification, you will have to add your id_rsa.pub in the server authorized_keys by login locally.

There are excellent ssh docs on the web for that.

I don't have these particular files that you mentioned. ~/.ssh/authorized_keys and ~/.ssh/id_rsa/pub the only file I have in ~/.ssh is known_hosts

---

### Post by Yannick Le Saint kyncani on 2009-09-15
Oh, so you were using ssh with password authentification instead of public key authentification ?

Well, I guess your account may have been locked and that would suck. So it may be unlocked at some point in time automatically (try later) or you would have to ask the admins to unlock it.

And once you have it working, you could setup public key authentification, which is easier than using a passwords.

---

### Post by juzar on 2009-09-15
Yes I was using it with password authentification. Sorry forgot to mention it. Thanks for the help.

---

