---
title: "Ubuntu 9.10 Minimal CLI recognizes LAN Port but isn't connected.."
date: 2010-02-21
forum: General Help
---

### Post by gymophett on 2010-02-21
I just installed Ubuntu 9.10 on a hard drive for another computer, then I switched it back to it's original computer and when I try to update or anything, it won't get the packages because it isn't connected.
So I try entering in lspci.
It recognizes:
Ethernet Controller: Intel Corporation 82557/8/9/0/1 Ethernet pro 100 (rev 08)

as one of them. I have the Ethernet cable plugged in, the Ethernet light is on, so it detects the cable. It just won't connect, and I have a valid connection or I wouldn't be able to be on here right now. I've tried 2 cables, still a no go. Is there a way I can connect or will I have to put the HD in the other desktop again and install everything and some drivers?

Thank you. :)

---

### Post by lloyd_b on 2010-02-21
When you say "and when I try to update or anything, it won't get the packages because it isn't connected", what exactly do you mean?  Is it giving you an error?

If so, please post the error.  This may give us a clue.

Lloyd B.

---

### Post by gymophett on 2010-02-21
> **lloyd_b said:**
> When you say "and when I try to update or anything, it won't get the packages because it isn't connected", what exactly do you mean?  Is it giving you an error?

If so, please post the error.  This may give us a clue.

Lloyd B.

I mean when I run ```
sudo apt-get update
```
I get: ```
W: Some index files have failed to download, they have been ignored, or old ones used instead.
```
Thank you.

---

### Post by lloyd_b on 2010-02-21
> **gymophett said:**
> I mean when I run ```
sudo apt-get update
```
I get: ```
W: Some index files have failed to download, they have been ignored, or old ones used instead.
```
Thank you.

Is that *all* you're getting, or is that just the last line?  If the former, please post the full output from "sudo apt-get update".

If it's only one source affected, then it could very well be a problem with that server...

Lloyd B.

---

### Post by gymophett on 2010-02-21
> **lloyd_b said:**
> Is that *all* you're getting, or is that just the last line?  If the former, please post the full output from "sudo apt-get update".

If it's only one source affected, then it could very well be a problem with that server...

Lloyd B.

I'm not able to copy and paste, so the output would be veeerry long. 
But as far as I can see, all of the packages have a failure getting.
It also occurs when just trying to install one package.
It works on the other desktop with this HD, but not on the current desktop.

---

### Post by lloyd_b on 2010-02-21
> **gymophett said:**
> I'm not able to copy and paste, so the output would be veeerry long. 
But as far as I can see, all of the packages have a failure getting.
It also occurs when just trying to install one package.
It works on the other desktop with this HD, but not on the current desktop.

Can you ping the servers in question? For example, what does ```
ping security.ubuntu.com
```respond with?

Try this with each server listed (security.ubuntu.com, us.archive.ubuntu.com, and dl.google.com on my machine).

Here's a sample output from my system:```

lloyd@ubuntu:/proc$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://security.ubuntu.com karmic-security/main Packages        
Hit http://security.ubuntu.com karmic-security/restricted Packages   
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/restricted Sources    
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Ign http://dl.google.com stable/main Translation-en_US                         
Get:2 http://dl.google.com stable Release [2,540B]                     
Get:3 http://dl.google.com stable/main Packages [871B]                         
Get:4 http://us.archive.ubuntu.com karmic Release.gpg [189B]
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 3,978B in 2min 5s (32B/s)
Reading package lists... Done
```

The "Hit" means that it reached the server, but there's nothing to update.  "Get" means it downloaded something.  "Ign" means that it's ignoring that package list.

What are you getting in place of these?  Or is it nothing but those warnings?

Lloyd B.

---

### Post by MinimalBin on 2010-02-21
Stop / start the given interface:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

.. and show us the output of the following command:
```
ifconfig
```

---

### Post by gymophett on 2010-02-22
> **MinimalBin said:**
> Stop / start the given interface:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

.. and show us the output of the following command:
```
ifconfig
```

eth0 isn't found it says. ):
What the heck?

---

### Post by MinimalBin on 2010-02-22
Weird, because it should be detected regardless of the connection state - once the ethernet cable is plugged in, the ethernet ( eth0 ) interface should be available.
What was the output of *ifconfig* ?

---

### Post by gymophett on 2010-02-22
> **MinimalBin said:**
> Weird, because it should be detected regardless of the connection state - once the ethernet cable is plugged in, the ethernet ( eth0 ) interface should be available.
What was the output of *ifconfig* ?

the output of ifconfig is the following

```
lo            Link encap:Local Loopback
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr:  ::1/128 Scope:Host
              UP LOOPBACK RUNNING   MTU:16436  Metric:1
              RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Hmm.

---

### Post by gymophett on 2010-02-23
*bump*

---

### Post by lloyd_b on 2010-02-23
I *think* I've figured it out.  The issue was that the hard drive was in another machine (with a different network card) when you did the install.

Linux "associates" a given interface (such as "eth0") with a given MAC address (from the hardware in the card).  This is done so that regardless of what order different devices initialize, a given network card will always have the same interface.

So, on that drive, "eth0" is now associated with the MAC address of the network device in the machine it was in when you did the installation.

Run "ifconfig -a", and see if it lists an "eth1" interface.  This will be the interface for the network device that's in the machine you have the hard drive installed in.  But odds are you don't have a "/etc/network/interfaces" entry for "eth1" (since you didn't think it'd be needed), so the interface is never brought up.

Take a look in the file "/etc/udev/rules.d/70-persistent-net.rules", and you should be able to see the MAC/interface associations for eth0 and eth1.  If you delete ALL these associations, and then reboot the machine, it should create a new association for the network card in that machine, as "eth0".  Hopefully, at that point everything will then work as expected.

Lloyd B.

---

