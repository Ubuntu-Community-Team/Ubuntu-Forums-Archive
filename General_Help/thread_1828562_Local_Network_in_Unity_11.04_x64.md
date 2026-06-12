---
title: "Local Network in Unity 11.04 x64"
date: 2011-08-19
forum: General Help
---

### Post by tonezone on 2011-08-19
I am trying to connect to the local network at my fraternity house to access a file server and printer both shared by Windows computers. I have mainly been using Smb4k to access network resources and reading up on Samba. I was able to access a shared printer and shared folders at my home where our router acts as the dhcp server, but the way the internet is set up at my fraternity we do not have control of the dhcp server. When I try to scan for network resources nothing comes up. I have tried scanning by using the option to automatically find workgroups, the option to query the current master browser, and the one to scan all ips in with the same first 3 fields, but in all cases nothing shows up from the scan. 

How can I find shares on this network?

---

### Post by CrusaderAD on 2011-08-19
Are you trying to access a shared folder on a local network? Make sure the share is setup right. You can do something like this on the server:

```
sudo nano /etc/samba/smb.conf
```

Then add these lines to fit you situation:

> [PrivateShare]
        comment = Private Share for Me
        writeable = yes
        valid users = myusername,myfriendsusername
        path = /home/me/PrivateShare
        write list = myusername,myfriendsusername

Then restart Samba:

```
/etc/init.d/samba restart
```

---

### Post by tonezone on 2011-08-19
I edited my smb.conf file the way you specified. For myusername I replaced it with the user name I use to log onto my computer(the client) and for myfriendsusername I used the username I need to use to access the shares(the server). I also restarted samba while rooted. I tried using Smb4k again, and the only network option that produced anything was the option to scan selected regions. It returned one computer, but the computer it returned is commented as school and has an ip address ending in 168, so I believe this computer is not on the local network but farther down the line. 

Upon rereading your post I believe there is a misunderstanding here. In this case, the servers that provide the printer and files are running Windows. The client is a linux machine. All the network resources are easy to access from a Windows client, but I cannot find any nearby computers from my linux machine no matter how I have Smb4k scan the network.

---

### Post by tonezone on 2011-08-26
bump

---

### Post by CrusaderAD on 2011-08-26
Ah this makes more sense now. What version of Ubuntu are you running?

---

### Post by e79 on 2011-08-26
Have you tried installing CIFS ?

```
sudo apt-get install smbfs
```and try to use the native network menu from Ubuntu if you can; or if you know the IP address of the server you want to connect to, you could try with the Nautilus option 'Connect to server'.

---

### Post by CrusaderAD on 2011-08-26
> **e79 said:**
> Have you reid installing smbfs ?

```
sudo apt-get install smbfs
```

Good suggestion... I keep forgetting that this isn't installed by default.

---

### Post by tonezone on 2011-09-29
smbfs was already installed:

tony@Tiamat:~$ sudo apt-get install smbfs
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

But using the connect to server option and the ip address I was able to access the file server, Thanks :).
I tried to do the same thing to access the shared printer but it did not work and gave an error saying: Failed to retrieve share list from server.
I noticed that the file server, the one I could connect to, has the exact same ip address as me except for the last field. The computer with the printer attached has the same ip address except for the last two fields. In the past I have noticed at my school that 2 windows computers with different values for the last two fields of the ip address could not communicate.
This method is a little inconvenient as I must always go to the computer and check the ip address from there. Is there a way to match the range of ip addresses near me to computer names?

---

