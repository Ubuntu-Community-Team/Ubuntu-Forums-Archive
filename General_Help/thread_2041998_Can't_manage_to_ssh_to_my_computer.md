---
title: "Can't manage to ssh to my computer"
date: 2012-08-13
forum: General Help
---

### Post by Zorgoth on 2012-08-13
I am about to go on vacation and will need to ssh into my desktop at home to run some code for my research. I know nothing about networking; I have successfully set up ssh before, but not on this network.  I set up a domain name (I used the default DNS Host(A) but also tried Port 80 redirect to 22; I have not got a clue what these mean) on no-ip.org. I have openssh-server installed, sshd is running, and i can log in using my local IP address from my network, but I can't log in from outside my network, even if I turn off my firewall. I don't know if it might have to do with a firewall on the router; I do not have control over it.

Note: I havea dynamic network with multiple computers on the same IP address. I installed the no-ip software that automatically updates my IP address.

I have tried:
ssh my_no-ip_hostname.no-ip.org
ssh [email]username@my_no-ip_hostname.no-ip.org[/email]
ssh [email]hostname@my_no-ip_hostname.no-ip.org[/email]
ssh my_IP_address
ssh username@my_IP_address
ssh hostname@my_IP_address,

but nothing works. I don't know exactly what happens because I'm not testing it myself; I am feeding the commands to another person who is outside my network. If you have specific question about it I can try to ask. I think it just times out, but I'm not sure.

Does anyone have any ideas, or is there something wrong with the format of the commands I am using?

Thank you!

---

### Post by Primefalcon on 2012-08-13
routers are configured to drop anyt connections that they did not initiate....

What you'll want to do is go into routers settings and forward port 22 (or whatever) to your computers local ip address (the options in the router will be called port forwarding), you'll also need to allows connections on that on your local computer

---

### Post by marlow59 on 2012-08-13
you should also create a static ip address for you computer to redirect connection from the router settings : [https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html)

---

### Post by Zorgoth on 2012-08-13
I managed to get into my router (the information was on a fridge magnet) and set up port forwarding to 22, and now it works perfectly. Thanks all!

---

