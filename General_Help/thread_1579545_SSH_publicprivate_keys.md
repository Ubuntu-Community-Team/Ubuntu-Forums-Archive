---
title: "SSH public/private keys"
date: 2010-09-22
forum: General Help
---

### Post by Abadon125 on 2010-09-22
Ok so I am trying to learn to use SSH with rsa keys.  I have two virtual machines, one has ubuntu 10.04 server and is called ubuntuserver.  The other has ubuntu 10.04 and is called ubuntuclient.

On ubuntu server I installed OpenSSH and have successfully created public and private keys as well as disabling logon with just username/password.  I have also copied the keys to a windows machine and connected with putty.

What I am trying to do now is connect to ubuntuserver from ubuntuclient.  I would think this would be easier but for some reason I just can't find the right steps.  Could someone either give me a quick run through of what I should be doing or just link to a working guide for me?

Thanks!

---

### Post by Abadon125 on 2010-09-22
Anybody have any experience with this?  I found this guide but it doesn't seem to be working for me.
[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by CharlesA on 2010-09-22
Were you able to create the keypair using ssh-keygen?

You can test it by trying to ssh into localhost:

```
ssh user@localhost
```

If it prompts you for the passphrase, type it in and see if you can connect.

If it lets you connect, try the same thing from the other ubuntu box after placing id_rsa in ~/.ssh:

```
ssh user@host
```

It'll prompt for the passphrase of the key, or say key rejected, depending if it's set up or not.

For Putty, you need to add the key under Connection > SSH > Auth > Private key for authentication.

---

### Post by Abadon125 on 2010-09-22
I was able to successfully SSH in from Windows using Putty after I using PuttyGen to convert the key file for windows.  On ubuntu though even with the key file I could not log in.

---

### Post by CharlesA on 2010-09-22
> **Abadon125 said:**
> I was able to successfully SSH in from Windows using Putty after I using PuttyGen to convert the key file for windows.  On ubuntu though even with the key file I could not log in.

Can you post the output please.

---

### Post by luvshines on 2010-09-22
The steps given in the link looks fine.

So, the passwordless ssh b/w ubuntuserver and ubuntuclient is not working, right ??

What does ssh with -v (or -v/-vv, more debuggin) says ?

---

### Post by luvshines on 2010-09-22
You can also see if ssh-copy-id commands does any gud for you.

I generally use it for creating my setup. [ I use empty passphrase ]

---

### Post by Abadon125 on 2010-09-22
I am setting up another fresh test environment to try again.  I probably just messed something up the first time around.  I'll reply in just a bit with how it goes.

---

### Post by Abadon125 on 2010-09-23
Ok, I have this working.  I have just a few questions about the guide however.  In the guide, host is the client and remotehost is the server correct? 

If this is the case then why does the host generate their own keys?  It seems like anyone could then generate their own keys and add them to the server?  Or is that what disabling password login does?

I was under the assumption that the keys were generated on the server and then you gave the public key to the client to use but I guess I had it exactly backwards.

---

### Post by CharlesA on 2010-09-23
> **Abadon125 said:**
> Ok, I have this working.  I have just a few questions about the guide however.  In the guide, host is the client and remotehost is the server correct? 

Remote host is the machine you are trying to connect to. Host is the machine you are connecting from (I'd prefer if they called it a client, but to each their own).

> If this is the case then why does the host generate their own keys?  It seems like anyone could then generate their own keys and add them to the server?  Or is that what disabling password login does?

You can do it on another machine and copy the keys using: ssh-copy-id. I normally create the keys on the same machine I want to secure, but that's just personal preference.

> I was under the assumption that the keys were generated on the server and then you gave the public key to the client to use but I guess I had it exactly backwards.

You leave the public key on the server, in the authorized_keys file and use the private key to connect.

---

### Post by Abadon125 on 2010-09-23
> **CharlesA said:**
> Remote host is the machine you are trying to connect to. Host is the machine you are connecting from (I'd prefer if they called it a client, but to each their own).



You can do it on another machine and copy the keys using: ssh-copy-id. I normally create the keys on the same machine I want to secure, but that's just personal preference.



You leave the public key on the server, in the authorized_keys file and use the private key to connect.

Awesome, thanks guys.  I just tested from windows again on the new VM I set up and was easily able to get that working too.  yay

---

