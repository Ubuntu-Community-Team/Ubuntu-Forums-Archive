---
title: "Sharing files over the Internet to a Windows 7 Machine"
date: 2010-09-02
forum: General Help
---

### Post by 2New on 2010-09-02
Hi  I've just come from Windows 7, I used to be quite adept with Linux about 5 years ago (saying that, I was much more adept overall with computers in general back then than I am now - fallen off the bandwagon quite considerably since my career took a different direction).   I'm trying to setup a PC from which I wish to access files over the network, both from elsewhere on my LAN and over the Internet.

I'd like the connection to be encrypted, and when either connecting via LAN or the Internet I'd like files to be cached at the other end.   So far, I've configured an (as yet, empty) folder located at home\username\documents as Shared (which involved downloading a couple of packages) and then changed the permissions to permit the sambashare group to read/write the folder.

I've then setup several user accounts and added them to the sambashare group.   I've also downloaded ddclient and linked it to a dynDNS account.

From my Windows 7 PC elsewhere on the Internet, if I try to add [http://xxx.dyndns.org/](http://xxx.dyndns.org/) or \\xxx.dyndns.org\ as a network place it tells me the address cannot be resolved, am I simply entering the dyndns address incorrectly, or perhaps I need to reconfigure the router, or perhaps I need to change something within Ubuntu.

Thanks very much for any assistance you can lend, I'm going to have a poke around and see if I can help anyone else on here whilst waiting for assistance (I've just spent over an hour trying to fix this particular problem myself..).

EDIT: I can see this question hasn't garnered much interest in the last 20 minutes, I suppose you get pretty fed up with newbies. I've just provided an answer with references to another thread which hadn't received any replies: [http://ubuntuforums.org/showthread.php?p=9797575](http://ubuntuforums.org/showthread.php?p=9797575), and a quick response to [http://ubuntuforums.org/showthread.php?p=9797614](http://ubuntuforums.org/showthread.php?p=9797614), please help me out.

---

### Post by Autodidact on 2010-09-02
The best way to share files (for newbies) is probably FTP.
Or better sFTP, the secure version of FTP.

Steps:
- Install an FTP sever on your Ubuntu system (hint: ProFTPD)
- Install an FTP client on your Windows system (hint: FileZilla)

Now you can access the Ubuntu system from any computer by:
- Open FIleZilla
- Connect to address: ftp://<IP address of Ubuntu system>

This only works within your local network.
To access the sever over the internet, open the correct port on your router.
The FTP sever is by default listed on port 21 (and sFTP on 22).

---

### Post by 2New on 2010-09-02
I'll give that a go now thanks very much :).

---

### Post by sikander3786 on 2010-09-02
> **Autodidact said:**
> 
This only works within your local network.
To access the sever over the internet, open the correct port on your router.


And to connect to the server over the internet you need to get a domain name.

[http://www.dyndns.com/](http://www.dyndns.com/)

Its free :p

---

