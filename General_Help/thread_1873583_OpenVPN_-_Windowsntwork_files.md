---
title: "OpenVPN - Windowsntwork files"
date: 2011-11-01
forum: General Help
---

### Post by arturusch on 2011-11-01
Hi,

New to Ubuntu and Linux.  I have searched the internet and found many many ways to approach this issue but with no luck.

I have a simple task ahead of me...
Connect to a VPN server at work
Access windows-folders.

I have vpn adress: vpn.mywork.com  (port 53)
I have drives \\server1\work\Projects which is J: and is named Projects

I installed smbfs
I installed open vpn and I connected to vpn.mywork.com port 53 with:
sudo openvpn --configure client.opvn
I have all certificates within a folder

My question.
How do move on to map all the drives?

I tried with /etc/fstab added line:
//vpn.mywork.com/server1/Projects /media/Work-Projects     smbfs username=myusername,password=mypassword, default 0 0

Of course I created /media/Work-Projects fodler

Then
mount -a

Cant get it to work...

Help needed.

Thanx in advance

---

