---
title: "best remote apps for ubuntu client to ubuntu server?"
date: 2012-07-07
forum: General Help
---

### Post by Jorel on 2012-07-07
Hi guys,,

just wanna know if Openssh is the best apps to use for ubuntu client to remote my ubuntu server?? because im having trouble configuring and remoting my server at the office while im at home.... hoping for any advice..

Thanks in advance....

---

### Post by Jorel on 2012-07-14
help please..... or kindly redirect me to a post same like this,, 
 
 
thanks.

---

### Post by Cheesemill on 2012-07-14
SSH should be the only thing you need.

If you actually describe the problem you are having then we might be able to help.

---

### Post by codemaniac on 2012-07-14
> **Jorel said:**
> Hi guys,,

just wanna know if Openssh is the best apps to use for ubuntu client to remote my ubuntu server?? because im having trouble configuring and remoting my server at the office while im at home.... hoping for any advice..

Thanks in advance....

You can follow the below guide and configure the Openssh server on your office Ubuntu server .

[https://help.ubuntu.com/12.04/serverguide/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/openssh-server.html)


One thing you need to be sure is you do have VPN access to your offices private network .Else the nodes in your private office netwirk wont be visible to your home pc (Ubuntu client) .

PS:Organizations often adhere to strict security policies while giving access to their private network to employees .

---

### Post by Jorel on 2012-07-14
thanks cheesemill and codemaniac..
 
well that will be my next problem, the office is a mess with the previous technician, and we're just using dynaic IP add with our provider, so everytime i restarted the router, our IP is changing, so thats why i build my Ubuntu file server for better file sharing and as well as maintaining the connection, and also just to mention my dilemma, i dont have the passwords to our router and Access Points,, so i may need also to crack the password using my server...
 
Thats why i needed to access my server while im at home to fix the mess.. :(

---

### Post by markbl on 2012-07-14
> **Jorel said:**
> so everytime i restarted the router, our IP is changing, ..
A free dyndns account solves that problem.

---

### Post by Jorel on 2012-07-14
Hi Markbl,

due that the management is not giving me any fund for this project, i look for a free one, i tried No-IP,  i'll try  setting this for openssh or maybe putty...

wish me luck..:)

---

### Post by codemaniac on 2012-07-14
Earlier dyndns used to give away free accounts , I am not sure if they are still providing the services for free .

No-Ip offers you free services for a limited period of time , i guess teh trial period is 30 days .

---

### Post by Cheesemill on 2012-07-16
> **Jorel said:**
> i dont have the passwords to our router and Access Points,, so i may need also to crack the password using my server...
It would be easier to perform a factory reset than to crack the passwords.

---

### Post by Jorel on 2012-07-17
Thanks Cheesemill,

Reseting to its default is really my 1st choice but when i look for the CD and some of the accessories that's included with the package, all are missing, all i have is the device itself, probably just want to play with it....

Hi Codemaniac,

as i look for that  free dyndns, its not free anymore... and as i investigate on our company, i found out that we have a VPN server,, but currently looking for it, nobody here knows what it is and who build it,, (thats why they put me in-charge here).....

Thanks

---

### Post by Cheesemill on 2012-07-17
> **Jorel said:**
> Reseting to its default is really my 1st choice but when i look for the CD and some of the accessories that's included with the package, all are missing, all i have is the device itself, probably just want to play with it....
No need for the CD, it's probably out of date anyway, any of the software that you could possibly need will be on the manufacturers website.
Most of the time you don't actually need any of the provided software to set up routers and access points it's all done through a web interface.

If you perform a factory reset then it will set everything back to default, including the usernames and passwords. You then just point a browser at the IP address of the device and log on with the default credentials which are easily available on the internet.

If you let me know the makes and models of the hardware you're having trouble with I could give you more specific instructions.

---

### Post by Jorel on 2012-07-17
Hi cheesemill,

i have a **Cisco Aironet 1240AG Series** and **Cisco 800 Router Series**,, as of now im studying these : [http://www.cisco.com/en/US/products/hw/routers/ps380/products_password_recovery09186a00800942c2.shtml](http://www.cisco.com/en/US/products/hw/routers/ps380/products_password_recovery09186a00800942c2.shtml) .

Thanks...:P

---

### Post by Jorel on 2012-07-19
Hi guys,,

I dont know if this post is related to my topic,, but anyway, 

Im studying Open VPN as indicated in:

[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

I know its the basic, but is this also the thing that ill be needing to control my Ubuntu Server at the office while im at Home?

Thanks in advance...

---

### Post by greenpeace on 2012-07-19
> **Jorel said:**
> is this also the thing that ill be needing to control my Ubuntu Server at the office while im at Home?

VPN connections would be a way of securing your connection to the office, but are not essential.

SSH is what you will need to access remotely.  If it is set up securely you won't have problems.  Don't connect to the server as a root user... only connect as a user with "sudo" privileges.

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

You will want to follow the instructions for "Disable Password Authentication"

If you are worried about attack, then consider installing DenyHosts.  There are a large number of tutorials available for that.

---

### Post by Jorel on 2012-07-19
Hi Greenpeace,

sorry im slowly digesting things here,, because im not really sure how VPN really works and also OpenSSH works in a Dynamic IP add (like what im trying to figure out in my early posts),,, so im still trying to patch up things here... 

so if this works even a sudden change in my IP add (as Dynaimc IP always happen when i restarted my router), then i would go for that, but if i really needed a VPN to bridge from outside world into my office, then i probably needed a VPN,,

feel free to correct me (coz im always wrong hehehehe)

thanks again..

---

### Post by markbl on 2012-07-19
> **Jorel said:**
> 
I know its the basic, but is this also the thing that ill be needing to control my Ubuntu Server at the office while im at Home?
ssh is far and away the ideal tool for remotely accessing a linux server. It is also the easiest to install, use, and secure. Ultimately ssh provides more flexbility once you learn about static/dynamic tunnels, proxycommand, using it with screen/tmux/vnc etc.

---

### Post by greenpeace on 2012-07-23
Hi Jorel, 

DynDNS is no longer free, but you can get a free account with these guys to give you a domain that is updated automatically to your IP address:

[http://freedns.afraid.org/](http://freedns.afraid.org/)

RE: updating IP address: [http://freedns.afraid.org/faq/#2](http://freedns.afraid.org/faq/#2)

I'm still not sure why you think you need a VPN... Is there one already set up?

best bet will be to 
1. set up your SSH server on the server.
2. set up port forwarding from your router to your server so that (eg.) port 2222 on your router is pointed at port 22 on your server.
3. set up the dynamic DNS from afraid.org

then you can just:
```
ssh user@mydomain.org -p2222 
```

to connect to your server.

---

### Post by Jorel on 2012-07-23
Hi greenpeace,

thanks for pin-pointing me the way caoz im studying the " Local port forwarding, Remote port forwarding, Dynamic port forwarding": 

[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

--there is a VPN server here at the office but they are not giving the password and configurations, and its really an eye-opener that i dont really need a VPN to remote my server at home...

thanks men,,,

---

### Post by greenpeace on 2012-07-23
> **Jorel said:**
> im studying the " Local port forwarding, Remote port forwarding, Dynamic port forwarding"

Sorry, that's not it.  You want to set the port forwarding on your router at home, it is not part of the SSH configuration.

This seems to be a good guide: [http://www.wikihow.com/Set-up-Port-Forwarding-on-a-Router](http://www.wikihow.com/Set-up-Port-Forwarding-on-a-Router)

> **Jorel said:**
> there is a VPN server here at the office 

You can't use a VPN to connect to something that's not in a network secured by a VPN!  :)

---

### Post by Jorel on 2012-07-23
Hi greenpeace,

this maybe spoon feeding, but i remember that i did not input a domain name while im setting up my server,  so what i did at afraid.com is i input the ipadd of my ubuntu server as a domain same, as the output is 

ssh "username"@"IPadd".strangled.net -p 22

and the username is what im using to log into my server, but the connection is asking for a password ( public key, password) that i know i needed to copy, im getting confused with that step...

hope you can help me with that,

thanks...

---

### Post by greenpeace on 2012-07-24
> **Jorel said:**
> the username is what im using to log into my server, but the connection is asking for a password ( public key, password)

You should be using your username and password for the server... whatever you normally use to log in!


Once that is working, then look at SSH keys and password-less logins.  But promise me that you won't touch that until you have a working login with username/password.

If you have the ability to return and change your domain name, I would recommend you do so... words are much easier to remember than numbers.

Finally, make sure that you have a script that is updating the IP address on that *.strangled.net domain.  There instructions in the afraid.org pages for that!

---

