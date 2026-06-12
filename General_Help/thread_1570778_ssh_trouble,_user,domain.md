---
title: "ssh trouble, user,domain?"
date: 2010-09-08
forum: General Help
---

### Post by unbuntunewb on 2010-09-08
hello, I am trying to create a socks proxy over ssh from my ipod at home connected to my wifi and make a tunnel to my pc/laptop. I have been using this command

ssh -D12345 [EMAIL="user@domain.com"]user@domain.com[/EMAIL]

however I do not know what the user or domain is, how do I find out? does anyone have an know how on this?

thanks!):P

---

### Post by Calash on 2010-09-08
> **unbuntunewb said:**
> hello, I am trying to create a socks proxy over ssh from my ipod at home connected to my network to my computer. I have been using this command

ssh -D12345 [email]user@domain.com[/email]

however I do not know what the user or domain is, how do I find out? does anyone have an know how on this?

thanks!):P

User is the username you want to connect as on the target system.  Domain is the name or IP address of the target PC.  You need to get this information from the target PC or the admin of that computer if that is not you.

---

### Post by unbuntunewb on 2010-09-08
well I am the admin but i still dont know how to set a name I wish to use, is the user name what I named the computer when I installed ubuntu? and which computer is the target pc, the ipod connected to the network, or the computer I want to create a tunnel to for secure browsing when im away from home?

this is what I get
nunya@nunya-desktop:~$ ssh -D12345 me@(ipod IP)
me@192.168.1.107's password: 
Permission denied, please try again.

how do I know my password?

---

### Post by hudsonl on 2010-09-08
Find out the IP of your home PC ... from your home PC go to  [http://whatsmyip.org](http://whatsmyip.org)

If you are connected to the internet at home using a router ... you will probably have to allow port forward thru your router to your PC

Then ... from the outside you can connect using the ssh command

(username is optional ... if you login as the same user from home and outside)

> ssh  username@myIPaddress

If you setup ssh server at home to use a different port (other than 22) then you will need to specify that on the command line ... as well as make sure you allow port forwarding on THAT port in your router.

> ssh -p xxxx  username@myIPaddress

---

### Post by unbuntunewb on 2010-09-08
I am connected to the internet using a linksys router, how do I allow port fowarding?

---

### Post by hudsonl on 2010-09-08
> **unbuntunewb said:**
> I am connected to the internet using a linksys router, how do I allow port fowarding?

Make sure that you have OpenSSH Server installed on the Ubuntu box you are trying to connect to ...

sudo apt-get install openssh-server

([https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html))

You can test it internally (from home) ... by using the local lan IP address 

> ssh johndoe@192.168.1.107

You should know the password for the username that use to login to the Ubuntu PC

To configure your router to work from the outside ...

Open your browser and go the URL for the router ... from the looks of the IP address you used for your PC ... I would say it's

[http://192.168.1.1](http://192.168.1.1)

Most of the router manufactures ... have intuitive configurations menus

Once that is done ... then you can connect from the outside

> ssh -p xxxx  johndoe@myIPaddress

Again ... the "-p" is only needed if you change the port that OpenSSH server is listening on when you did the installation.

---

