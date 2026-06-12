---
title: "looking for a GUI for SFTP (using my key)"
date: 2009-09-17
forum: General Help
---

### Post by EarlGrey on 2009-09-17
Sorry if my question does make any sence, but I have been tying to google for ages and still nothing.

To connect to one hosting provider, I was required to generate a ssh2 (RSA) key and send them the public key. Now, I need a FTP program, that will allow me to connect to the their server using my key in SFTP. I can't find a way how to do it in fileziila, gftp or others.

(on windows, they recomend WinSCP)

Do yuo please have any suggestions? It would save me!

Thanks alot.

---

### Post by The Cog on 2009-09-17
I use nautilus. Type an address like **sftp://user@1.2.3.4** into the address bar. I use public key to my server this way. It just seems to work.

---

### Post by EarlGrey on 2009-09-19
Thanks alot. But unfortunatelly, that does not solve it. I need to tell the sftp somehow where my key is, right?

I have been trying the command line such as

ssh -i [KEY_PATH] [user]@[server] -p [port]

and that is almost correct - asks me for a passshpere, but thenreturns a error message:

```

This account is restricted by rssh.
Allowed commands: scp sftp

If you believe this is in error, please contact your system administrator.

```

---

### Post by The Cog on 2009-09-19
I believe that the normal place to keep the keys is in ~/.ssh and that nautilus looks there. Here is my ~/ssh
> ls ~/.ssh
authorized_keys  id_rsa  id_rsa.keystore  id_rsa.pub  known_hosts
I think it's the id.* files that are involved this end, but I certainly never get asked for a password when I ssh into my home server. Neither using ssh/sftp on command line, or using nautilus.

---

### Post by Ormente on 2009-09-19
I use sshfs (install via synaptic), and view remote folders like local ones in nautilus.

To mount remote servers you can use command line, but the is some GUI tools also.
I use xsshfs ([http://xsshfs.zici.fr/telechargement](http://xsshfs.zici.fr/telechargement)), the most staightforward.
It's in french, wich is my language fortunately, and i don't know if it's translated in english... but it's realy simple to understand/use.

---

### Post by Tibuda on 2009-09-19
Import your key in Applications > Acessories > Passwords and encryption keys.

---

