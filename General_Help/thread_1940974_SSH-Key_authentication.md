---
title: "SSH-Key authentication"
date: 2012-03-14
forum: General Help
---

### Post by tuX9th on 2012-03-14
Hi,
today I wanted to try out ssh-keys to speed up the logintimes on a root server.
But I can't seem to get it to work.
I did everything as described in the wiki:

[LIST]
[*]ssh-keygen
[*]ssh-copy-id -i ~/.ssh/id_rsa.pub <user>@<host>
[/LIST]
but it didn't work
I post the log here.
A friend of mine can connect via ssh key onto the server. he's using mac os x though. (so its not the server its me)
Does anyone know what the problem is?


[http://paste.ubuntu.com/883973/](http://paste.ubuntu.com/883973/)

greets
btw. i'm using ubuntu 11.10. Can't change my details anymore

---

### Post by sp-1070 on 2012-03-15
try to remove the files from youre client so that when you trie to connect to ssh it will say do you accept the rsa thingy.
Also trie connecting using putty

---

### Post by tuX9th on 2012-03-15
Did that too. Didn't help

how should i use putty?

---

### Post by matt_symes on 2012-03-15
Hi

> debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/alex/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/alex/.ssh/id_dsa
debug3: no such identity: /home/alex/.ssh/id_dsa

The server does not like your rsa public hash by the looks of it.

You are on the authorised keys list on the server ? You have RSA key encryption enabled on the server in the config file ? Your public key is on the server in the correct place on the server ?

Check on the server. That's where i would be looking first.

Kind regards

---

### Post by tuX9th on 2012-03-15
the authorised keys list is on the server, the public key on the server is in the correct place, can't answer about the RSA key encryption, because i don't really know what you mean by that.
#edit encryption thing didn't change a thing

#edit2
```

debug2: we sent a publickey packet, wait for reply 
debug1: Server accepts key: pkalg ssh-rsa blen 277

```a friend of mine authed with his key and sent me the log. its all the same until those lines.
my log just says:
```

debug2: we sent a publickey packet, wait for reply 
debug1: Authentications that can continue: publickey,password
```

---

### Post by matt_symes on 2012-03-15
Hi

This is what you would expect to see.

```
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/matthew/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277
```

Your permissions are set correctly on the ~/.ssh directory and files on the client ? 

You're looking for permission the same as these (don't worry about their location on my system) ..

```
matthew@matthew-Aspire-7540:~$ ls -ld  /home/matthew/my_documents/ssh_keys/
drwxr-xr-x. 3 matthew matthew 4096 Mar 14 23:40 /home/matthew/my_documents/ssh_keys/
matthew@matthew-Aspire-7540:~$ ls -l  /home/matthew/my_documents/ssh_keys/
total 28
-rw-------  1 matthew matthew  142 Dec  5 21:40 config
-rw-------. 1 matthew matthew 1675 Apr 19  2011 id_rsa
-rw-r--r--. 1 matthew matthew  404 Apr 19  2011 id_rsa.pub
-rw-------  1 matthew matthew 5348 Feb 20 00:38 known_hosts
-rw-r--r--. 1 matthew matthew 5180 Feb 20 00:18 known_hosts.old
matthew@matthew-Aspire-7540:~$
``` 

Not sure if this is the problem,  but this is worth checking as a matter of course.

Kind regards

---

### Post by tuX9th on 2012-03-16
```
drwxr-xrwx  2 alex alex 4,0K 2012-03-15 17:00 .
drwxr-xr-x 76 alex alex 4,0K 2012-03-16 08:16 ..
-rw-------  1 alex alex 1,7K 2012-03-15 17:00 id_rsa
-rw-r--r--  1 alex alex  390 2012-03-15 17:00 id_rsa.pub
-rw-r--r--  1 alex alex  444 2012-03-15 17:00 known_hosts

drwxr-xrwx   2 alex alex 4,0K 2012-03-15 17:00 .ssh

``````

drwx------  2 alexz alexz    4.0K Mar 16 08:19 .
drwxrwxrwx 12 alexz www-data 4.0K Mar 16 08:19 ..
-rw-------  1 alexz alexz     390 Mar 16 08:19 authorized_keys

```this is not it :S
but thanks

#edit
changed the permissions on the .ssh dir to what you have. still no change

---

### Post by matt_symes on 2012-03-17
Hi

What do the log files on your server say ?

Have you set any allowed or denied IP addresses ?

EDIT:

What about running sshd with the debug flag on the server. This assumes port 22. Check the man page for sshd.

```
ssh -d -D -p 22
```

Kind regards

---

