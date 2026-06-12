---
title: "SSH Questions"
date: 2010-03-12
forum: General Help
---

### Post by pjcace on 2010-03-12
I have a project that I'm working on now that is using Ubuntu 8.04LTS to create a reverse SSH proxy for a telnet process.  We have the box logging in with RSA keys so that it can automatically connect to the SSH host on our end.  We are using autossh to keep the connection up and running.

We have rolled out 3 of these and they are working very well.  We ghosted the original, changed the hostname, changed the IP info, and regenerated the SSH keys.  Now I need to clone 35 more.  I want to try to do this as efficiently as possible and can script the changes in the hostname, IP, ect.  

Can I batch create RSA keypairs on my workstation and then copy them over as a part of the batch?  My current other option is to login to each of them and generate the pair.  I would like to just install the drive and ship it and not even have to boot it up.

Thanks

---

### Post by HermanAB on 2010-03-12
Yes, you can copy the key pairs.

---

### Post by pjcace on 2010-03-12
I'm not sure I was clear.  I know I can copy them, but can I generate 35 separate pairs on my machine and dole them out?  How do I create different ones.

Thanks,

---

### Post by tgalati4 on 2010-03-12
That would depend on Ubuntu's "padding" scheme being tied somehow to each individual machine--sort of like how UUID's are assigned to hard disks.  They are unique to each hard disk.  I don't know if Ubuntu's RSA key generator relies on a hardware-specific padding scheme.  If not, then you could generate 35 key-pairs on one machine and then simply copy them over and they should work.  

You would have to test if first on a few machines to verify.

man rsa

---

