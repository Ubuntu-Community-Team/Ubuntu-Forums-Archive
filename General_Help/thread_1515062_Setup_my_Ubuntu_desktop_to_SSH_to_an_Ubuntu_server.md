---
title: "Setup my Ubuntu desktop to SSH to an Ubuntu server"
date: 2010-06-21
forum: General Help
---

### Post by mbates on 2010-06-21
I have just migrated my desktop envirornment from Windows to Ubuntu and can't figure out how to get SSH working properly.

I have an Ubuntu Server (on the Amazon cloud) and I had been using putty. The Amazon tools created the public private keypair, and I added the private key to putty so I could ssh into the server.

I have my .pem file copied to the ssh folder. But I can't work out how to tell my Ubuntu desktop to use it as an identity file when opening the connection.

Thanks for any help,
Mike

---

### Post by Leppie on 2010-06-21
did you copy the .pem file to your own .ssh folder (hence, ~/.ssh), or the ssh folder?

---

### Post by mbates on 2010-06-21
my own folder, ~/.ssh ( /home/username/.ssh/ )

---

### Post by Leppie on 2010-06-21
have you checked the settings in /etc/ssh/ssh_config?

---

### Post by mbates on 2010-06-21
Thanks for the pointers, they helped me get it working.
Here is what I did:

edited the ssh_config to add an IdentityFile for my private key.
ssh [user]@[ip] still gave a permission denied

I then used ssh -i and gave the full path to the .pem file
This gave me the error 'WARNING: UNPROTECTED PRIVATE KEY FILE!'

I chmoded the .pem to 0600 and tried ssh -i [user]@[ip] and I got in.

I tried the ssh without the -i again but that one still doesn't work, so I'll have to keep playing with the ssh_config to see if anything there gets it going. But I can get in with -i so I'm happy.

Cheers.

---

### Post by Leppie on 2010-06-21
glad it's working, even though in a kinda of hackish way.
i'm sorry i don't have experience with the pem files for ssh.

---

### Post by efflandt on 2010-06-22
Look at setting up various hosts in ~/.ssh/config in your client PC, for example

Host mainpc
HostName 192.168.1.1
User efflandt
ForwardX11 yes

Then you could simply **ssh mainpc** even if your username is different on your client PC and mainpc did not resolve in DNS.

Common options for all connections (which apply unless countered in the specific Host section) can use a wildcard Host section:

Host *
Compression yes
KeepAlive yes
RhostsAuthentication no
RhostsRSAAuthentication no
RSAAuthentication yes

---

### Post by mbates on 2010-06-22
thanks, that worked perfectly, the only other thing I had to do was add in RSAAuthentication yes as Amazon created an RSA key, not sure why I need that lione in there as I though it defaulted to yes.

It's working now anyway, I just have to use ssh [myserver]

Host [myserver]
HostName [ip]
User [user]
IdentityFile /home/mike/.ssh/dev.pem
RSAAuthentication yes

---

