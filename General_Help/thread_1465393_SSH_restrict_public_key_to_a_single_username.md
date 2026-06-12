---
title: "SSH restrict public key to a single username"
date: 2010-04-29
forum: General Help
---

### Post by Altay_H on 2010-04-29
I set up SSH on a server running Ubuntu using rsa key authentication. I want to allow a friend of mine to log into the server with restricted access, so I created a user account named "guest" with its own home directory and ensured that it has no root access. I created a new pair of keys and added the public key to my authorized_keys, but when I was testing SSH I noticed that not only could I not log in as guest, I could use the key to log in as my own account and gain root access via sudo. How can I restrict specific private keys to only be able to log in as certain users?

---

### Post by limey_rick on 2010-04-29
Here is a post I found that I used to set up my SSH server in a similar fashion. Its not specifically for Ubuntu, but it worked for me/

[http://fedorasolved.org/post-install-solutions/securing-ssh](http://fedorasolved.org/post-install-solutions/securing-ssh)

---

### Post by Leppie on 2010-04-29
you have to use the sshd_config file to restrict access. when using the keys, the machine you install the key on will always have access even if the guest account is disabled.
open the sshd_config file with a text editor:
```
gksudo gedit /etc/ssh/sshd_config
```
and add the following line somewhere:
```
AllowUsers guest
```
save and exit the file, restart the ssh service:
```
sudo service ssh restart
```

---

### Post by psusi on 2010-04-29
Umm... you can't NOT do it that way.  To log in as user x with the key, the key must be in user x's .ssh/authorized_keys file.  If you were able to log in as either user with the same key then you must have put the key in both users' authorized_keys... don't do that.

---

### Post by Altay_H on 2010-04-29
That tells me how to allow guest to log in using the key, but I don't see how to restrict the key to *only* allow it to be used for logging in as guest. I'll still be able to use the key to log in as my own username even if I add guest to the AllowUsers in sshd_config. Is there no way to associate keys with user accounts?

> **psusi said:**
> Umm... you can't NOT do it that way.  To log in as user x with the key, the key must be in user x's .ssh/authorized_keys file.  If you were able to log in as either user with the same key then you must have put the key in both users' authorized_keys... don't do that.
I see now. Thanks for clarifying! I forgot that each user has a separate authorized_keys file.

---

### Post by Leppie on 2010-04-29
the authorized keys are in no way a security measure.
whenever i start a session from a new machine or after having removed the authorized key, the file will be regenerated.

---

### Post by psusi on 2010-04-29
> **Leppie said:**
> the authorized keys are in no way a security measure.

I fail to see any meaning in this statement.


> **Leppie said:**
> whenever i start a session from a new machine or after having removed the authorized key, the file will be regenerated.

Sure, an empty one.

---

