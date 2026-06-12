---
title: "Newbie can't configure Echolife 520b for ssh"
date: 2010-04-29
forum: General Help
---

### Post by Blackbird_13 on 2010-04-29
I can't configure a talktalk router (Huawei Echolife HG520b) to accept my ssh connection.  
 
**Background**
 I want to connect to my 80 year old father's pc using ssh. Both pc's are running Jaunty and have OpenSSH server installed. I have a BT Home Hub and dad has a talktalk HG520b.
 
 Via the HG520b (dad's pc on eth0 and mine on wlan0) I have successfully connected “locally” to my dad's pc on 192.168.1.60 using RSA authentication on a non-standard port (12345, say). I have also connected from my dad's pc to my own “locally” on 192.168.1.70.  
 
I don't have a static "external" IP address when connecting via a BT Home Hub.  I have setup port forwarding on the BT Home Hub:

```
Protocol    Port Range            Translate To …    Trigger Protocol    Trigger Port
[IMG]http://bthomehub.home/images/spacer.gif[/IMG]TCP          12345 – 12345        12345 – 12345         -                      -
```Whilst trying to resolve this problem my external IP address hasn't changed and my dad's ufw has been configured as follows (IP address illustrative only):

                           ```

To           Action            From 
 --           ------           ---- 
  12345/tcp    ALLOW          99.888.777.666  

```Talktalk allocate a different IP address every time my dad logs on, therefore I always have to change the command I use (port number and IP address Illustrative only):
 
 ```
ssh -v -p 12345 [EMAIL="blackbird@11.222.333.444"]blackbird@11.222.333.444[/EMAIL]
```**HG520b**
 I have setup port forwarding on the HG520b and have followed the instructions on:
 
 [HTML]http://portforward.com/english/routers/port_forwarding/Huawei/EchoLife-HG520b/SSH.htm[/HTML] On researching the problem I found some advice to “Disable” the “SPI” setting on the HG520b Firewall - the narrative says “(all traffics initiated from WAN would be blocked, including DMZ, Virtual Server and ACL WAN side)”. Disabling did not solve my connection problem.
 
Given that ssh works “locally” I am thinking my ssh connection problem must be with the HG520b blocking my connection, but I have been unable to find any useful manual/documentation for the HG520b.  

 When trying to connect from my PC the ssh command quickly hangs. The output is as follows:

                           ```
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: Applying options for * 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 11.222.333.444 [11.222.333.444] port 12345.

```Finally, pinging produced:
4 packets transmitted, 0 received, 100% packet loss, time 3022ms

Given I live 100 miles away from my dad and he is not able to do any configuration his end, it has taken me ages just to get this far! Any advice on how to proceed would be greatly appreciated.

---

### Post by mjbrightfr on 2011-12-25
Hi, thanks your post was useful to me as I was trying to setup SSH access through a 520b router.

I came across another post which suggested disabling SPI (Firewall section) as you do but also using an alternative port such as 8081.

So I set up 8081 as the external port, which is forwarded to the standard port 22.

I then connected using
    ssh -p 8081 user@myip

This worked.
Hope this can help somebody.

---

