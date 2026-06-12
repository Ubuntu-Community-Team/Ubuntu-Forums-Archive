---
title: "Working with files on a remote computer"
date: 2011-12-24
forum: General Help
---

### Post by Canaryguy on 2011-12-24
Hello,

I have two computers at home and I'd like to access the files from one of the computers while I'm working with the other. I think this can be done using Nautilus and in File menu you use Connect to server... but apart from that I have no idea what I should do to do it.

---

### Post by collisionystm on 2011-12-24
> **Canaryguy said:**
> Hello,

I have two computers at home and I'd like to access the files from one of the computers while I'm working with the other. I think this can be done using Nautilus and in File menu you use Connect to server... but apart from that I have no idea what I should do to do it.

on your computer install openssh sever

sudo apt-get install ssh

then in nautilus under connect to server, change type to SSH and put in the IP of the machine you want to connect to. Hit connect.

---

### Post by Lars Noodén on 2011-12-24
First you have to have the package OpenSSH-Server installed on the remote machine.

Then in Nautilus, 

File->Connect to Server->Type->SSH

That should do it.

Edit: Fixed type.  Anyway collisionystm got the answer first above!

---

### Post by rjf1 on 2011-12-24
> **Canaryguy said:**
> Hello,

I have two computers at home and I'd like to access the files from one of the computers while I'm working with the other. I think this can be done using Nautilus and in File menu you use Connect to server... but apart from that I have no idea what I should do to do it.

1. Right click on the folder you want to share; select 'sharing options'
2. Select 'Share this folder' and fill out the rest of the dialog box entries according to your preferences, then click 'Create Share'
3. If you have Samba installed, that's it on this machine. If not, it will offer to install Samba for you -- after it installs Samba, you are good on this machine.
4. To access this folder from the other machine, go to the other machine and open any folder -- in the left panel click 'Browse Network' -- networked computers will appear as icons in the right panel
5. Click the name of the computer you want to access, and any shared folders on that machine will show up -- click the folder you want to access, and Bob's your uncle.

---

### Post by collisionystm on 2011-12-24
> **rjf1 said:**
> 1. Right click on the folder you want to share; select 'sharing options'
2. Select 'Share this folder' and fill out the rest of the dialog box entries according to your preferences, then click 'Create Share'
3. If you have Samba installed, that's it on this machine. If not, it will offer to install Samba for you -- after it installs Samba, you are good on this machine.
4. To access this folder from the other machine, go to the other machine and open any folder -- in the left panel click 'Browse Network' -- networked computers will appear as icons in the right panel
5. Click the name of the computer you want to access, and any shared folders on that machine will show up -- click the folder you want to access, and Bob's your uncle.


Ubuntu to ubuntu... use ssh. its faster.

samba was only built to interface with windows. It is not nearly as fast

---

### Post by Canaryguy on 2011-12-24
> **collisionystm said:**
> on your computer install openssh sever

sudo apt-get install ssh

then in nautilus under connect to server, change type to SSH and put in the IP of the machine you want to connect to. Hit connect.

Thank you very much. I installed openssh on both computers and now I can access the files.

---

### Post by collisionystm on 2011-12-24
> **Canaryguy said:**
> Thank you very much. I installed openssh on both computers and now I can access the files.


Cool beans.

If you want to use windows to do the same, install winscp to access ssh servers

---

### Post by Lars Noodén on 2011-12-24
> **Canaryguy said:**
> Thank you very much. I installed openssh on both computers and now I can access the files.

It will also be possible to make it accessible from anywhere in the world should the need arise.

---

### Post by Canaryguy on 2011-12-28
My router assigns an IP 192.168.... let's call it X to one computer and assigns Y to the second computer. But sometimes the second computer is assigned X and the first with the Y IP. Is there any way the computer can keep the same IP? Because everytime I want to access remotely to the other computer I have to see which IP it is using to access it.

---

### Post by Lars Noodén on 2011-12-28
Sometimes the routers will let you associate the IP address with a MAC address on your network adapter.  Another way might be to increase the lease times so that the lease does not expire so soon.

---

### Post by Canaryguy on 2011-12-28
> **Lars Noodén said:**
> Sometimes the routers will let you associate the IP address with a MAC address on your network adapter.  Another way might be to increase the lease times so that the lease does not expire so soon.

How do I do that? From within the router's menu?

---

### Post by Lars Noodén on 2011-12-28
Yes, but exactly where or if it can be done varies from model to model.  You'll have to work through the menus yourself to see if it does have those capabilities.

---

### Post by Canaryguy on 2011-12-28
I think I found it.
So, I just have to make the lease permanent, right? Does this suppose some security issue or something? I mean, making it permanent?

---

### Post by rjf1 on 2011-12-28
Another possibility is to edit the Network Connection and assign one computer a fixed IP address of 192.168 ... X; and the other a fixed IP address of 192.168 ... Y

---

### Post by Canaryguy on 2011-12-28
> **rjf1 said:**
> Another possibility is to edit the Network Connection and assign one computer a fixed IP address of 192.168 ... X; and the other a fixed IP address of 192.168 ... Y

And how do you do it from the Network Connection?

---

### Post by Lars Noodén on 2011-12-28
> **Canaryguy said:**
> And how do you do it from the Network Connection?

Dash->Network Connections->Edit Wired Connection->Method->Manual

You can also edit [font=Courier New]/etc/network/interfaces[/font] directly.

---

### Post by Canaryguy on 2011-12-28
> **Lars Noodén said:**
> Dash->Network Connections->Edit Wired Connection->Method->Manual

You can also edit [font=Courier New]/etc/network/interfaces[/font] directly.

So, from Network Connection I edit the wire or wireless and then go to IPv4 and IPv6 Settings and change them to manual. Then I have to add an Adress Netmask and Gateway. hmmm... is that right?

---

### Post by Lars Noodén on 2011-12-28
Yes.   The end result is that you will have something like the following in [font=Courier New]/etc/network/interfaces[/font]

```

iface eth0 inet static
   address 192.168.222.24
   broadcast 192.168.222.255
   netmask 255.255.255.0
   gateway 192.168.222.1

```

Of course you want the values to match what you are using on your own network.

---

### Post by Canaryguy on 2011-12-28
Thank you for your help Lars and rjf1.

---

### Post by Lars Noodén on 2011-12-28
You're welcome.  

As an afterthought, you might want to make the fixed IP numbers outside the range doled out by DHCP.  That way you can avoid even the possibility of a collision.

---

### Post by Canaryguy on 2011-12-28
Using the command ifconfig I can see which IP I have the Broadcast and Mask, but where can I see the gateway value?
In the router's menu I can see the default gateway but the value is completely different to the IP, it doesn't start by 192.168...

---

### Post by Canaryguy on 2011-12-28
I found it :-)
To get the gateway value you just need to use the command "route"

---

### Post by matza55 on 2012-01-11
Sound nice - I will try....:p

---

### Post by matza55 on 2012-01-11
> **Lars Noodén said:**
> First you have to have the package OpenSSH-Server installed on the remote machine.

Then in Nautilus, 

File->Connect to Server->Type->SSH

That should do it.

Edit: Fixed type.  Anyway collisionystm got the answer first above!

I did what, but what should I fill in? ( see att. picture)

Edit: and that is my IP? how can I find it?

---

### Post by Lars Noodén on 2012-01-11
You have to fill in the ip number of your server.  Do you have the correct one?  If it changes every time then you have to run [ifconfig](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html)

```

/sbin/ifconfig eth0

```

If you don't want it to change each time, you can probably fix that in your switch or router.

---

### Post by matza55 on 2012-01-11
> **Lars Noodén said:**
> You have to fill in the ip number of your server.  Do you have the correct one?  If it changes every time then you have to run [ifconfig](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html)

```

/sbin/ifconfig eth0

```

If you don't want it to change each time, you can probably fix that in your switch or router.

My pc has IP: 192.168.0.103, and the other pc has: 192.168.0.102, it doesn't work?

---

### Post by Vaphell on 2012-01-11
ping it to check if it's reachable from your machine.
```
ping 192.168.0.102
```

---

### Post by matza55 on 2012-01-11
> **Vaphell said:**
> ping it to check if it's reachable from your machine.
```
ping 192.168.0.102
```

Yes, it works fine!

---

### Post by Canaryguy on 2012-01-14
> **matza55 said:**
> I did what, but what should I fill in? ( see att. picture)

Edit: and that is my IP? how can I find it?

In Server you have to indicate the IP of the remote computer and in the last two boxes you have to add the user name of the remote computer and the password that that user uses to log in.

---

### Post by matza55 on 2012-01-14
> **Canaryguy said:**
> In Server you have to indicate the IP of the remote computer and in the last two boxes you have to add the user name of the remote computer and the password that that user uses to log in.

I filled in that, but it don't work. I'm give up....

---

### Post by Canaryguy on 2012-01-14
> **matza55 said:**
> I filled in that, but it don't work. I'm give up....

To make it work you need to install the openssh package on both computers.

sudo apt-get install ssh

---

### Post by matza55 on 2012-01-14
> **Canaryguy said:**
> To make it work you need to install the openssh package on both computers.

sudo apt-get install ssh

Yes, that have I done.

---

### Post by Canaryguy on 2012-01-14
> **matza55 said:**
> Yes, that have I done.

hmmm.. then I don't know why it doesn't work. I'm not an expert. What I only did was to install the openssh on my computer an on the remote one (maybe you have to restart the computers) and what I did too on the remote computer was to share the computer with the Desktop Sharing. (I'm using Ubuntu 11.10)

---

### Post by matza55 on 2012-01-14
> **Canaryguy said:**
> hmmm.. then I don't know why it doesn't work. I'm not an expert. What I only did was to install the openssh on my computer an on the remote one (maybe you have to restart the computers) and what I did too on the remote computer was to share the computer with the Desktop Sharing. (I'm using Ubuntu 11.10)

Ok, that's I should do! Only to test.

---

