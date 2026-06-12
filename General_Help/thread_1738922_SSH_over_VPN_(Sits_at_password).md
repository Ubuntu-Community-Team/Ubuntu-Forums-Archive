---
title: "SSH over VPN (Sits at password)"
date: 2011-04-25
forum: General Help
---

### Post by solidus23 on 2011-04-25
Hey all, I have tried searching for information on doing SSH over VPN. All resources I find say that it should be fairly transparent and I should be able to SSH into the local address once I have established a VPN connection. I can ssh into the machine but it will not take my password. I type it correctly hit enter, but it just asks for the password again. It doesn't state that the password is incorrect, just asks for the password again. I can SSH over the internet just fine. Thanks for you help.

---

### Post by btindie on 2011-04-25
You should be able to ssh into servers fine over a VPN provided your VPN is correctly configured.

With the VPN established, type ```
$ telnet <host_ip> 22
``` to verify that it's connecting to the SSH server. If the connection is successful then it should display a string of the form "OpenSSH<version>". Use Ctrl+] then type quit to exit the telnet command. This isn't actually telneting to the server, it's just using the telnet command to establish a TCP connection to the server to check that it can connect correctly.

Have you got any firewall rules that could be blocking it? Any restrictions on the user account you're using? Does it allow passwords or has to been configured to only allow public keys?

Try running ssh with the '-v' option to get some debug output, you can use more v's to increase the verbosity.

---

### Post by solidus23 on 2011-04-25
Well I found out that I can connect to the sever through SSH when connecting with my laptop using L2TP. Whenever I connect on my Windows 7 machine using PPTP it destroys any SSH connection I had with the L2TP connection and as long as my desktop is connected using PPTP I cannot SSH into the server. As soon as I disconnect with the PPTP, I can SSH into the server again using L2TP. I am unsure why this is happening and how to remedy it. Thanks for you help so far.

---

