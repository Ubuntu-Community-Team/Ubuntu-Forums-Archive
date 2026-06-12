---
title: "VPN to Corporate share basic help"
date: 2009-07-27
forum: General Help
---

### Post by aharrod on 2009-07-27
I am a Ubuntu Noob who has installed on my thinkpad T61.  I really love Linux so far, but I have  a few problems to iron out.  I am hoping someone can help me.  My laptop is used for work, where I have  2 basic needs that I can figure out.
 
1) in Windows I use PPTP VPN to our server.  The information I have to have to set this up was: gateway: companyname.com, Username: [EMAIL="name@emailaddress"]name@emailaddress[/EMAIL], password: userpassword.  I have managed to set up Ubuntu to connect to the VPN after I turned encryption on.
 
After I connect to VPN in windows I have  windows mounted network drive from the server I am attached to. //servername is what I had to have in windows to mount and access.  How do I accomlish this in Ubuntu?
 
Also I access a remote desktop to use quickbooks and again I just have to have the //servername and gateway which is the same as the servername.
 
Can anyone tell me how to do these 2 basic tasks in ubuntu?  
 
Thanks,
 
Alex

---

### Post by jonobr on 2009-07-27
Hello


You could try installing vpnc from the synaptic package manager as well as a program called kvpnc which is the gui front end.

I use it for connecting through a cisco firewall, and all I have to do is load up my cisco pcf file and nothing more.


For your situation though, you will have to configure a new connection.

In kvpnc, select create new profile and will give you a wizard that allows you to setup the connection. You may need the help of you IT person to figure out how your authenticating, (PAP CHAP) and if there are any additional settings which need to be setup.
One thing you should know is that there are known issues AFAIK with MSCHAP which are unresolved.

Once you connect with the VPN, remote desktop should work as if you were just connecting to a machine on the same network,
go to
applications->internet-> terminal services client.

This will allow you to remote destkop to your remote machine to do your quickbooks

If your having problems connecting to the remote machine, make sure its pingable across your vpn connection.

---

### Post by aharrod on 2009-07-27
What about mapping windows share drives from the server I am VPN'ed into?

---

### Post by jonobr on 2009-07-27
[Samba]("http://us1.samba.org/samba/")

Its available in the repos through synaptic

---

### Post by aharrod on 2009-07-28
i don't think this is something that can be setup by a basic user, which means I can't get rid of Windows completely. 

Is there any basic help on how to set Samba up for being a client and connecting to a windows share?

---

### Post by zzzBrett on 2009-07-28
> **aharrod said:**
> i don't think this is something that can be setup by a basic user, which means I can't get rid of Windows completely. 

Is there any basic help on how to set Samba up for being a client and connecting to a windows share?

Instead of \\server (windows), try smb:\\server\ in Nautilus.

---

### Post by jonobr on 2009-07-28
hello


[heres a ]("http://industriousone.com/mounting-windows-shares-linux") quick guide of someone doing what you want.


I would work on your vpn connectivity first though.

If you dont get that working then theres no need to worry about Samba:D

---

### Post by aharrod on 2009-07-31
thanks or all the comments.  from the advice here and a judicious amount of futzing about on my own I was able to get it to work.  the key seemed to be entering the share servers IP address.  for some reason Linux was not able to resolve the address for me.  
works like a charm now.

Thanks again,

alex

---

### Post by bodhi.zazen on 2009-07-31
> **aharrod said:**
> thanks or all the comments.  from the advice here and a judicious amount of futzing about on my own I was able to get it to work.  the key seemed to be entering the share servers IP address.  for some reason Linux was not able to resolve the address for me.  
works like a charm now.

Thanks again,

alex

Probably because it is not a public IP

You can add the server in /etc/hosts and then use the server host name if you wish.

---

### Post by jonobr on 2009-07-31
Actually you could resolve that by putting in the name in your hosts file


Ie if your connecting to the machine foo which has an IP address of 10.10.10.10


Then you would edit the /etc/hosts file

```
sudo gedit /etc/hosts 
```
and add a line in there that has 
10.10.10.10   foo


Then when you ping foo it resolves to that IP address.

What happens is that when you ping foo, it looks at the hosts file, and then if there is no match to an IP address, it will look at the dns.

Here you are adding the ip address in the hosts file so it doesnt go to dns.

Im thinking though, if your connecting VPN to your network, you should be resolving to your dns though

---

