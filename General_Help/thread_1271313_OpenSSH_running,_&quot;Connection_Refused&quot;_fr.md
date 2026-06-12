---
title: "OpenSSH running, &quot;Connection Refused&quot; from Visat Putty attempt"
date: 2009-09-20
forum: General Help
---

### Post by darkcabal on 2009-09-20
Hi all. I am running Ubuntu Hardy Heron and am trying to get a putty connection to the OpenSSH service from a Vista laptop.
 
I can run the ssh attempt from the Ubuntu box localhost but every attempt from the Vista laptop ends with a quick "Connection Refused".
 
Linux is a bit rusty.
 
I have made an entry in the allowed.hosts file but I am not sure where to go from here. Thought SSH was supposed to be pretty straight forward. It has been a while since I installed this Ubuntu machine so I can't recall if a firewall was installed by default or running by default? I can't see any GUI tools for controlling one but did notice that running ufw add 2223 command did update a firewall rules set. Does that mean it is running? 2223 is the port I assigned to ssh in the config file.
 
I have a hunch that this is a Vista problem but want to make sure I haven't missed anything?
 
No rush.....any help would be appreciated.
 
Cheers,
 
Travis

---

### Post by bogdan.veringioiu on 2009-09-21
Hi.

How do you connect locally?
ssh user@localhost:2223 ??

Try to stop the firewall:
sudo /etc/init.d/ufw stop

Then try to connect again from your vista machine.
This way you can verify if the firewall is blocking or not the access.
Bogdan

---

### Post by Bachstelze on 2009-09-21
> **bogdan.veringioiu said:**
> 
How do you connect locally?
ssh user@localhost:2223 ??


I think you meant [font=monospace]ssh user@localhost -p 2223[/font].

---

### Post by bogdan.veringioiu on 2009-09-21
Yes, you are right...my mistake.
Cheers.

---

### Post by bacardiandwatermelon on 2009-09-21
Is it really necessary to change the port? Isn't it secure enough just having a ssh key pair? How did you configure your /etc/ssh/sshd_config file?

---

### Post by XCan on 2009-09-21
You could also install gufw to get a simple overview of your rules if it turns out that it was a firewall issue. I think it's good practice to change the port, even if one uses keys, it kills off 99.9999% of the bots hammering the sshd.

---

### Post by darkcabal on 2009-09-22
Yeah I changed the port only because the OpenSSH HOWTO recommended it.
 
I stopped the ufw service as suggested and tried again. Still no joy.
 
"Network Error: Connection Refused"
 
Here is a copy of my ssh_config file:
 
Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
    RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
    Port 2223
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
 
I think that the "Network Error: Connection Refused" means I am not even hitting the box right?
 
I have 2 NIC's but only one of them is plugged in, eth0 and I am using the IP address to ssh not host name.
 
As far as Vista goes, I have attempted the connection after turning off the windows firewall (no 3rd party firewall running) as well as with the firewall on and exceptions for ports 22, 2223, putty.exe. Who knows, maybe turning off the firewall doesn't "really" turn it off?
 
Thanks for the tips so far but I am still stuck.
 
Cheers,
 
Darkcabal

---

