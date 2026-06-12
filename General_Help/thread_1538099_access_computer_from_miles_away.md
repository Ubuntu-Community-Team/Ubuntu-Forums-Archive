---
title: "access computer from miles away"
date: 2010-07-24
forum: General Help
---

### Post by philipballew on 2010-07-24
hi, i am moving to college and have two computers both with ubuntu. i will be leaving a desktop here and taking a laptop. i want to be able to access the desktop with my laptop from collage to get files and also accsess the thing to still use it. any help would be great.

---

### Post by Bachstelze on 2010-07-24
Use SSH for command-line access and file transfers, and VNC for graphical access.

For bonus geek points, you can setup a VPN between both machines. :p

---

### Post by philipballew on 2010-07-24
how would i go about doing this and what is it exactly?

---

### Post by Tylerjd on 2010-07-24
SSH and VNC! 
With SSH you can do remote command line things like updating your system, and you can also do secure file transfers. VNC is a desktop sharing solution so you can view and control you desktop from anywhere. Make sure to forward port 22 for ssh and 5900 (usually) for VNC. If you have a dynamic IP, be sure to use a service such as DynDNS so you can have a DNS name to connect you computer to.

And as Bachstelze said, you can do a VPN, by using software such as OpenVPN [[http://openvpn.net/]](http://openvpn.net/]) to VPN between the two computers, and then you only have to forward one or two ports to have access to every service you desktop serves.

---

### Post by Bachstelze on 2010-07-24
For SSH it's simple, just install the package [font=monospace]openssh-server[/font] on your computer at home, then you can access it with

```
ssh IP_ADDRESS
```

from anywhere (if your home computer is behind a router, you will need to forward port 22 in it).  You can also transfer files to/from it using for example FileZilla.

For graphical access, you'll have to use VNC: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

The VPN part was more of a joke. ;)  VPN stands for Virtual Private Network, it basically creates an encrypted channel between two machines, allowing you to use them as if they were on the same LAN.  Using it you can for example make all your Internet traffic go through the VPN, so that your school can't monitor the websites you visit or the email you send.  It is a bit complicated to set up, though.

---

### Post by Tylerjd on 2010-07-24
> **philipballew said:**
> how would i go about doing this and what is it exactly?
To start with SSH, on your desktop install the OpenSSH server ([https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)) and for VNC ([https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)).

For VPN, it may be a little more difficult as it requires a bunch of upfront configuration, but you can follow a guide such as the one on OpenVPN's Website ([http://openvpn.net/index.php/access-server/installation-overview.html](http://openvpn.net/index.php/access-server/installation-overview.html))

---

### Post by philipballew on 2010-07-24
so in laymens terms what will openvpn do?

---

### Post by philipballew on 2010-07-24
and will this allow me to use my computer at home as a place to do  things such as back up files from my laptop?

---

### Post by Bachstelze on 2010-07-24
> **philipballew said:**
> so in laymens terms what will openvpn do?

What I said above.  It can't really be made any simpler, but don't worry too much about it, I wasn't really serious when I mentioned it.

> **philipballew said:**
> and will this allow me to use my computer at home as a place to do  things such as back up files from my laptop?

Yes.  As I said, using SSH you can transfer files to and from your home computer using FileZilla, or even Ubuntu's file manager.

---

### Post by Tylerjd on 2010-07-24
> **philipballew said:**
> so in laymens terms what will openvpn do?
In laymans terms open vpn will make your computer (laptop) believe it is on the same computer network as your desktop. You can also whats known as tunnel your traffic (make you internet requests) go through you network at home instead of the school's. So lets say that you want to grab a file from your desktop, which has file sharing turned on, instead of forwarding the SMB port and making your home network unsecured, a VPN will make the file share show up under Network

---

### Post by Tylerjd on 2010-07-24
> **philipballew said:**
> and will this allow me to use my computer at home as a place to do  things such as back up files from my laptop?
For backup, I would use an external USB or firewire drive, much faster and simpler. But, yes it could. I do it, but only when I'm not sitting at home connected directly to a Ethernet plug

---

### Post by philipballew on 2010-07-24
so thats the best way to be able to use my desktop at home as a way to store files?

---

### Post by Tylerjd on 2010-07-24
> **philipballew said:**
> so thats the best way to be able to use my desktop at home as a way to store files?
If you are talking about OpenVPN, yes and no, If you understand installing packages and running scripts from the command line, and are comfortable with it, then dive in.

Using SSH, VNC, and port forwarding is simpler (with no VPN), but not as expandable, and it may be slow (from my experiences). VNC is also a relatively unsecure connection, so malicious *may* be able to see your VNC password and what the IP address of the desktop is. If you want, however, you could tell VNC to use a SSH connection to make it secure.

---

### Post by philipballew on 2010-07-24
in your opinion if what i want to do is use my desktop as a server and occasionally access the desktop what is the best option

---

### Post by Tylerjd on 2010-07-24
> **philipballew said:**
> in your opinion if what i want to do is use my desktop as a server and occasionally access the desktop what is the best option
Both options are perfectly fine, I would say it depends on how comfortable you are with using the command line (Terminal). If you are comfortable, and know your way around, then go ahead and use the VPN. (I forgot to mention, with the VPN, you will still need to install services like SSH and VNC, it will just make configuring those services a lot easier, and less port forwarding). 

If you aren't as comfortable with command line, then you may just want to use VNC and SSH.

---

### Post by philipballew on 2010-07-24
i dont mind the cl but would rather use a gui type method

---

### Post by jackhadrill on 2010-07-24
An easier way to do this would be to log in to your home router.
You then have to find a DMZ option and set it to your desktops internal ip address.
If you have a static external ip, skip the next step.
Next use DYNDNS, sign up and set up your router to use this.
Then from your laptop, you can vnc or ssh using either the static ip or you DYNDNS address. Hope this helps:popcorn: :) !

If you need help finding the sewttings in your router or on setting up vnc then google them.

---

### Post by Tylerjd on 2010-07-24
> **philipballew said:**
> i dont mind the cl but would rather use a gui type method
With OpenVPN, once you get past the initial setup, there is a Web-base front end that will be used to continue the setup. For an in depth reference, there is a internet TV show called Hak5, and it can walk you through the setup procedure... [http://revision3.com/hak5/vpnsandkindleconsole#seek=1705](http://revision3.com/hak5/vpnsandkindleconsole#seek=1705)

---

### Post by jackhadrill on 2010-07-24
> **Tylerjd said:**
> With OpenVPN, once you get past the initial setup, there is a Web-base front end that will be used to continue the setup. For an in depth reference, there is a internet TV show called Hak5, and it can walk you through the setup procedure... [http://revision3.com/hak5/vpnsandkindleconsole#seek=1705](http://revision3.com/hak5/vpnsandkindleconsole#seek=1705)

Personally, I prefer DMZ. It lets you do a lot of things and access it from any computers with any OS. I refer to my previous post.

---

### Post by Tylerjd on 2010-07-24
> **jackhadrill said:**
> Personally, I prefer DMZ. It lets you do a lot of things and access it from any computers with any OS. I refer to my previous post.
DMZ is defiantly an interesting piece of networking, however, DMZ and VPN's are used for two different purposes, one is to keep an internal network secure, and the other is to be able to have access in behind a firewall. I keep my XAMPP/SSH/Mail/external DNS server on a DMZ, but my LDAP, VPN, and internal DNS along with client computers on a separate subnet.

---

### Post by jackhadrill on 2010-07-24
> **Tylerjd said:**
> DMZ is defiantly an interesting piece of networking, however, DMZ and VPN's are used for two different purposes, one is to keep an internal network secure, and the other is to be able to have access in behind a firewall. I keep my XAMPP/SSH/Mail/external DNS server on a DMZ, but my LDAP, VPN, and internal DNS along with client computers on a separate subnet.

I agree, however itsn't tricky to setup passwords/ firewall.

---

### Post by Tylerjd on 2010-07-24
[philipballew]("http://ubuntuforums.org/member.php?u=748757"), if you could, can you mark this topic as solved if we have successfully answered your question?

---

### Post by randumnumber on 2010-08-01
I use dyndns.com go check it out. you can get a DNS address like blahblah.homelinux.com then have it routed to your home ip address for free. 

Then you have to set up your firewall to route incoming ssh requests to be sent to your home server computer.(google portforwarding for whatever kind of router your using) Then I use sftp i can get on nautilus type in sftp://blahblah.homelinux.com:21 and it will send me to the root folder of my home linux box. its great for file transfer, it uses SSH though nautilus, so you dont have to worry about command line stuff just drag and drop. You might also want to take a look at ubuntuone.com it is free cloud storage for ubuntu users, it comes standard with 10.04 but you can use it with any ubuntu distro(i think).

---

