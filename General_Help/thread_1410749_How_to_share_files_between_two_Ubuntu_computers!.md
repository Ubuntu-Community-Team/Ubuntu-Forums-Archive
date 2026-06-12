---
title: "How to share files between two Ubuntu computers!"
date: 2010-02-19
forum: General Help
---

### Post by demonic_crow on 2010-02-19
I can't seem to figure out how to even share files between my laptop and desktop.  They are both Ubuntu 9.10.  I thought maybe samba was the way but couldn't figure it out.  I was looking at the ssh that comes with Ubuntu and been trying to get it to work but don't know what I'm doing wrong.  I type:
ssh username@computername  and it give me a little info.  Don't know what I'm suppose to do then.  I looked at the network folder on my laptop and it seem to see it but everytime I click on it ask for a password and I can't get in since I don't know the right password.  I'm not sure if this is the best software to use or not.  Just wanted something to look at and transfer from my desktop to my laptop and vice versa.  Thanks

---

### Post by wojox on 2010-02-19
Go to Places > Connect to Server
Pick ssh
Enter ip address and use name 
Hit Enter
Fill in password and user
Then you can drag and drop files from each of you /home folders.

---

### Post by demonic_crow on 2010-02-19
what would be the ip address.  Is it the one it show after I did the ssh username@computername or your internet.  If its the ssh one it only showed it once and not sure where to find it. Thanks alot

---

### Post by cong06 on 2010-02-19
Often if you type 'computername.local' in place of the ip address, it should work.

If you're using the terminal the 'computername' can be found:
```

cat /etc/hostname

```

But it's the name you set to your computer when you installed if that helps.

Finding the IP address though:

For guis:
System > Preferences > Network Tools
Click the drop down "Network Device"
In the table you'll see both your IPv4 and IPv6 ip address

for command prompt:
```

ifconfig

```

---

### Post by demonic_crow on 2010-02-19
awesome that work, is there a way to make sure just these two computer can connect to each other only.  I don't want someone to easily to get in my computer, or is it pretty safe this way.

---

### Post by gjoellee on 2010-02-19
> **demonic_crow said:**
> I can't seem to figure out how to even share files between my laptop and desktop.  They are both Ubuntu 9.10.  I thought maybe samba was the way but couldn't figure it out.  I was looking at the ssh that comes with Ubuntu and been trying to get it to work but don't know what I'm doing wrong.  I type:
ssh username@computername  and it give me a little info.  Don't know what I'm suppose to do then.  I looked at the network folder on my laptop and it seem to see it but everytime I click on it ask for a password and I can't get in since I don't know the right password.  I'm not sure if this is the best software to use or not.  Just wanted something to look at and transfer from my desktop to my laptop and vice versa.  Thanks

You can quite easily share files on LAN with a program galled "giver" (made by the Linux Mint developers I think):
```
sudo apt-get install giver
```

---

### Post by cong06 on 2010-02-19
> **demonic_crow said:**
> awesome that work, is there a way to make sure just these two computer can connect to each other only.  I don't want someone to easily to get in my computer, or is it pretty safe this way.

If you used the 'connect to server' option, then you're using ssh. Which is encrypted, but only as safe as your password.
If you have a very secure password, then no one can even read information as you request it. If you have a lax password they can jump into your box and hijack stuff.

---

### Post by Ordes on 2010-02-19
> **demonic_crow said:**
>  is there a way to make sure just these two computer can connect to each other only.  I don't want someone to easily to get in my computer, or is it pretty safe this way.

configure your firewall. e.g firestart is a nice and easy gui tool for that.

further in /etc/ssh/sshd_config you can change the default port, e.g 1234

than configure your firewall, incoming permissions
e.g ssh port 1234 for 192.168.1.1 (change with the internal IP of your other PC). if you dont have static IPs, you can set a range of IP. But i would rather use static IPs on a network. 

>> network connections  >> automatic to manual (enter the need info, IP which is your choice; dns, gateway, etc)

---

### Post by TheFu on 2012-02-14
I know this is an old thread, but thought I should point out that using **fail2ban** and a non-standard port for ssh will prevent almost all ssh-based attacks.  For systems inside a firewall, I leave ssh on port 22, but for access over the internet, I use the router's port forwarding + translation capability to make the public IP + port something nonstandard - perhaps 30022 and translate that port to 172.16.2.44:22 on the internal machine.

To help me remember which port I use, there's a ~/.ssh/config file that make connecting easy. No need to remember the port.

Also, so you aren't tempted to have a trivial password that can be hacked, disable use of passwords and force ssh-keys to be used instead outside your internal LAN.  ssh-copy-id makes this trivial to setup.   [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has more information.

---

### Post by nothingspecial on 2012-02-14
Please do't bump old threads to the top.

Closed.

---

