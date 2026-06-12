---
title: "SSH RSA Key authorization problem - Location?"
date: 2010-09-09
forum: General Help
---

### Post by jackbrennan2008 on 2010-09-09
***using openssh-server*

Hi there,

I have been planing on organising RSA key authentication to my SSH server for a while, but have come across a problem.

I have created my keys using PUTTYgen and am not sure where to put my public key on the server. The SSHD.conf file points to a directory called %h/.ssh/authorized_keys, but it doesn't exist in my home directory (I checked hidden files, but it is not there).

So i created the folder .ssh and the sub folder authorized_keys and put my public key in there (authorized_keys). I would have presumed that it would work now seeing as the publilc key is in the right place, but i still cannot login. I named the public key id_rsa.pub; should it be renamed to something else?

I have uncommented the following lines in sshd.conf

RSAAuthentication yes
PublickeyAuthentication yes
AuthorizedKeysFile %/.ssh/authorized_keys

I there something i am missing?

Thank you

Jack.

---

### Post by Gunman1982 on 2010-09-09
> **jackbrennan2008 said:**
> ***using openssh-server*
So i created the folder .ssh and the sub folder authorized_keys and put my public key in there (authorized_keys). I would have presumed that it would work now seeing as the publilc key is in the right place, but i still cannot login. I named the public key id_rsa.pub; should it be renamed to something else?

I there something i am missing?


Yes you are, authorized keys is not a folder but has to be a file. Just save your 'id_rsa.pub' as '.ssh/authorized_keys' . If you have more than one key add the next one as a new line in the authorized_keys file.

---

### Post by jackbrennan2008 on 2010-09-10
[S]*Ah, thank you, that makes more sense now!*
* I might also add (for other who come cross this thread) i had to create the public and private key in Ubuntu using the htpasswd command (i had to install apache2) rather than Puttygen for some reason. Either way it's working now.*
* Many thanks.*   [/S]

Edit**
Thanks mate it worked. I also had to use: ssh-keygen -t rsa to create new key pairs seeig as the puttygen keys were incompatible.

---

### Post by CharlesA on 2010-09-10
> **jackbrennan2008 said:**
> Ah, thank you, that makes more sense now!

I might also add (for other who come cross this thread) i had to create the public and private key in Ubuntu using the htpasswd command (i had to install apache2) rather than Puttygen for some reason. Either way it's working now.

Many thanks.

You don't use htpasswd for generate keypairs for ssh, and I don't know how exactly you'd use it to do that anyway.

You use the command ***ssh-keygen***.

Puttygen will create a key that is incompatible with openssh server. You have to convert the key to something that openssh can understand. 

I've always had to create the key on the server and then convert it to a putty key using puttygen.

Now that I've looked at puttygen more thoroughly, I see that you can convert it to an openSSH key from that utility. :)

---

### Post by jackbrennan2008 on 2010-09-10
> **CharlesA said:**
> You don't use htpasswd for generate keypairs for ssh, and I don't know how exactly you'd use it to do that anyway.

You use the command ***ssh-keygen***.

Puttygen will create a key that is incompatible with openssh server. You have to convert the key to something that openssh can understand. 

I've always had to create the key on the server and then convert it to a putty key using puttygen.

Now that I've looked at puttygen more thoroughly, I see that you can convert it to an openSSH key from that utility. :)

I know, i was just coming back here to change what i wrote. I have been organising my web server with .htaccess and .htpasswd and i just got mixed up lol. I was working on it all night after i finished with the ssh server...so yea...bleh.

I used 
ssh-keygen -t rsa; of course.

I spent maybe 5 hours yesterday getting everything working smoothly so my heads running around in circles. :confused:

Needless to say everything is in top shape now!

---

### Post by CharlesA on 2010-09-10
Happens to everyone. :)

I've been playing around with puttygen (thanks!) and you can export an OpenSSH key from it. However, I find it easier just to create the keypair on the server using ssh-keygen and then convert the private key to a PuTTY key (.ppk).

---

### Post by jackbrennan2008 on 2010-09-10
> **CharlesA said:**
> Happens to everyone. :)

I've been playing around with puttygen (thanks!) and you can export an OpenSSH key from it. However, I find it easier just to create the keypair on the server using ssh-keygen and then convert the private key to a PuTTY key (.ppk).

Last night I ended up just creating them on the server and converting the private key using puttygen. I'll have to have a look at creating key pairs through puttygen a little late on. Puttygen is such a nifty program and always handy to keep lying around and it's always good to find new functions for it :).

---

