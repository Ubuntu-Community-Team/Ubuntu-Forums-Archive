---
title: "scp, unable to resolve hostname"
date: 2011-10-13
forum: General Help
---

### Post by orrymr on 2011-10-13
Hi

I just tried to copy a file from a remote terminal using the following command (after sshing in):

```

scp filename user@hostname:/home/username/directory

```

Where user@hostname is my account on my machine (I verified this using the commands hostname and whoami)

Unfortunately I got the following error:
ssh: Could not resolve hostname

I'm not sure why this is. Any help would be greatly appreciated, thanks.

Oh, I eventually resolved the situation by copying the file on the remote machine into a dropbox folder.
Still, I'd like to know why the above didn't work.

---

### Post by prodigy_ on 2011-10-13
> **orrymr said:**
> Where user@hostname is my account on my machine (I verified this using the commands hostname and whoami)
Doesn't mean you'll be able to resolve it remotely. There are various approaches to name resolution but in a small LAN using **/etc/hosts** file would be the easiest way. (For more info run **man hosts** command.)

Alternatively you can use user@IP notation (e.g. user@192.168.0.1). In this case you won't need name resolution at all.

---

### Post by orrymr on 2011-10-13
I'm actually trying to do the copy over the internet. I went to whatsmyip.org, got the IP address, and substituted it for the hostname part. Now, it simply hangs and I have to ^C to stop scp. :confused:

Edit: I think I know what the problem is; the ip address on whatsmip.org refers to my router's external IP address. My machine is sitting at 192.168.0.3, in the LAN. I'm just not sure how to resolve this issue.

---

### Post by prodigy_ on 2011-10-13
> **orrymr said:**
> I'm actually trying to do the copy over the internet. I went to whatsmyip.org, got the IP address, and substituted it for the hostname part. Now, it simply hangs and I have to ^C to stop scp. :confused:
I see. To access a host that is behind NAT over the Internet you need:

1) Either a real domain name (you can get a free 3-rd level domain on a site like [DynDNS.com](http://dyn.com/dns/dyndns-free/) or [No-IP.com](http://www.no-ip.com/)) or a public IP address (your router has one). A domain name is easier to remember and services like DynDNS provide tools for auto-updating DNS records in case if your ISP assigns dynamic IP addresses.

2) Port forwarding. For security reasons exposing samba shares to untrusted networks might be a bad idea. Your best bet is to install the [SSH server](https://help.ubuntu.com/community/SSH) package (I believe you already did that since you tried to use scp) and configure [forwarding for TCP port 22](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding) via your router.

Then you'll be able to transfer files using sftp, scp or sshfs.

P.S. It looks like a lot of work to do but in reality it's not that hard. :)

---

