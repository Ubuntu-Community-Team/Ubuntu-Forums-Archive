---
title: "Accidentaly removed Python on my Ubuntu"
date: 2010-05-17
forum: General Help
---

### Post by cusri2004 on 2010-05-17
Hi,

First of all I don't know whether this post is posted in the right category. So, excuse me if its not. 

I kind of screwed up my laptop today. Accidentally removed python!! During this process I realized thats its removing packages like evince, gstream etc...so I used force quit but the damage was done already. 

Rebooting the computer initially complained that it is running on low graphics and tried various combinations which were listed but didn't work. Later on while I tried to boot it several times, it never reached the login screen. 

I tried to reboot my computer in recovery mode. Tried to update the system from there. For example

sudo apt-get update 

it spits these lines 

Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg
Could not resolve 'archive.canonical.com'

Err [http://nz.archive.canonical.com]("http://nz.archive.canonical.com/") lucid Release.gpg
Could not resolve 'nz.archive.canonical.com'

Err [http://nz.archive.canonical.com]("http://nz.archive.canonical.com/") lucid-updates Release.gpg
Could not resolve 'nz.archive.canonical.com'

Err [http://nz.archive.canonical.com]("http://nz.archive.canonical.com/") lucid-security Release.gpg
Could not resolve 'nz.archive.canonical.com'

Reading package lists.....Done

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...id/Release.gpg]("http://nz.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg") Could not resolve 'nz.archive.ubuntu.com'

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...es/Release.gpg]("http://nz.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg") Could not resolve 'nz.archive.ubuntu.com'

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...id/Release.gpg]("http://nz.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg") Could not resolve 'nz.archive.ubuntu.com'

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...ty/Release.gpg]("http://nz.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg") Could not resolve 'nz.archive.ubuntu.com'

W: Somed index files failed to download, they have been ignored, or old ones used instead. 

My computer is behind the university proxy. None of the suggestions on google worked to solve this issue. 

I am skeptical whether I can fix this without reinstalling.

Any suggestions will be of great help.

---

### Post by DawieS on 2010-05-17
The message '**Could not resolve xxxxxxx xxxx**' means that your computer is unable to obtain a valid route/IP address to the update servers. If you use a normal Internet connection, it should work.:smile:

---

### Post by 3rdalbum on 2010-05-17
You may need to try running:

```
sudo dhclient
```

to get DHCP information from the network and connect.

As for your proxy, I'm sure there's a way of specifying the proxy for Apt on the command-line, but I don't know anything about it.

If you do get a connection and be able to use Apt through the command-line, you should be able to run:

```
sudo apt-get install ubuntu-desktop
```

and everything will work again.

---

### Post by flameproof on 2010-05-20
> **3rdalbum said:**
> You may need to try running:

```
sudo dhclient
```

to get DHCP information from the network and connect.



How do I actually connect then from black screen command line?

I have the same problem on my (no old) 9.04 harddrive but I like to make it work again to get some files and setups.

---

