---
title: "Mounting NAS that has dynamic IP?"
date: 2009-11-07
forum: General Help
---

### Post by varanasi on 2009-11-07
I have an NAS on our LAN.  It must be assigned an IP from DHCP, so the IP changes.  How can I mount it by "name" rather than by IP.  

When I try

```
sudo mount -t cifs //DiskStation/home /media/win -o nounix,username=varanasi,password=####,file_mode=0777,dir_mode=0777
```

I get this error:

```
mount error: could not find target server. TCP name DiskStation/home not found
No ip address specified and hostname not found
```

I seem to remember that I did something to fix this before, but I am completely blanking.

---

### Post by falconindy on 2009-11-07
Step 1: Login to your router.
Step 2: Pull up the DHCP client list and find your NAS's IP.
Step 3: Using this IP, login to your NAS and set a static IP (reboot it if necessary).
Step 4: Make an entry in your /etc/hosts file to point to your NAS.

A device like a NAS should **never** rely on DHCP.

---

### Post by varanasi on 2009-11-09
> **falconindy said:**
> Step 1: Login to your router.
Step 2: Pull up the DHCP client list and find your NAS's IP.
Step 3: Using this IP, login to your NAS and set a static IP (reboot it if necessary).
Step 4: Make an entry in your /etc/hosts file to point to your NAS.

A device like a NAS should **never** rely on DHCP.

That's what I have done.  

Until I read your post I was planning on trying this: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

But, now I'm wary.  Why I shouldn't use DHCP to assign an IP to an NAS?  Not arguing, just don't know.  Thanks.

---

### Post by StuartN on 2009-11-09
> **varanasi said:**
> When I try

```
sudo mount -t cifs //DiskStation/home /media/win -o nounix,username=varanasi,password=####,file_mode=0777,dir_mode=0777
```

I get this error:

I use mount name:share, for example my_nas.local:stuartn, rather than //my_nas.local/stuartn - the .local on the end of local hosts seems to help.

---

### Post by shaggy999 on 2009-11-09
I just want to point out that just because there is a DHCP server on your network doesn't mean your NAS has to have an IP handed out by said DHCP server. For example, I roommate with a bunch of people and we share a linksys router that hands out IP's with the final number starting at 100 (ex: 192.168.1.100, 192.168.1.101, etc). The last number of the router's IP starts at 1. That means the numbers 2 - 99 will never be assigned by the DHCP server and I can manually set up a system to use those numbers. In fact I have a linux server that I did just that with. I set it up to have a static IP and gave it 192.168.1.50 and carried over all the DNS/Gateway/etc settings that the DHCP router normally hands out because that information is static).

The end result is a DHCP network, but with one system set up w/ a static IP. Everything works perfectly.

---

### Post by bacardiandwatermelon on 2009-11-09
I'm sure most routers these days have a function to reserve ip adresses for certain mac addresses. I'm pretty sure that this sort of setup at home is fine :-)

---

### Post by michaelzap on 2009-11-09
If you're using Gnome you can also mount them using GVFS:
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

