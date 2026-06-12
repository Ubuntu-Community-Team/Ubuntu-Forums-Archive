---
title: "SSH Server Problems"
date: 2006-01-30
forum: General Help
---

### Post by simonjbale on 2006-01-30
Hi,
 
I'm having a problem with the OpenSSH server. I have bound the server to port 80, changed the login grace time to 20 and enabled password authentication. Whenever I try and connect from an external host I get a message asking me to add the host key to my local database and then a second message telling me that the connection is reset by the peer. I am using cygwin ssh as the client. The auth.log file tells me that the failed connection attempts timed out however no where near 20 seconds passes before the connection is reset. Any ideas, could this have something to do with an incorrect authentication scheme setup.
 
I would also like to force the server to always use interactive password based authentication, similar to the standard Linux login scheme. Is setting the PasswordAuthentication and UsePAM options the correct way to do this? How do I disable the public key schemes? I've had a read of the sshd_config man pages but they are not very clear regarding the function of certain options, an example sshd_config file would be greatly appreciated :-)
 
Best Regards, Simon Bale.

---

### Post by mrcbrown on 2006-01-30
[QUOTE=simonjbale]Hi,
 
I'm having a problem with the OpenSSH server. I have bound the server to port 80, changed the login grace time to 20 and enabled password authentication. Whenever I try and connect from an external host I get a message asking me to add the host key to my local database and then a second message telling me that the connection is reset by the peer. I am using cygwin ssh as the client. The auth.log file tells me that the failed connection attempts timed out however no where near 20 seconds passes before the connection is reset. Any ideas, could this have something to do with an incorrect authentication scheme setup.
 
I would also like to force the server to always use interactive password based authentication, similar to the standard Linux login scheme. Is setting the PasswordAuthentication and UsePAM options the correct way to do this? How do I disable the public key schemes? I've had a read of the sshd_config man pages but they are not very clear regarding the function of certain options, an example sshd_config file would be greatly appreciated :-)
 
Best Regards, Simon Bale.[/QUOTE]

Why port 80? Not going to avoid you any port scans as it'll be a common thing people are scanning for to see what version of Apache your running - try changing the port to something higher above the normal port range scans.

I used more or less the stock ubuntu setup with a few changes, key ones being PermitRootLogin to No and some tweaked things for remote X within my home office - try a different port though, might give you better results from Windows.

---

### Post by Peter76 on 2006-01-30
Like mrcbrown says, definetely go for a higher port > 4000 is fine; I don't know that much about tcp/ip, but I assume sshd interferes with you webtraffic on port 80 ( can someone say something about this? ) Also you might give putty a try as a client for windows; works fine for me

---

