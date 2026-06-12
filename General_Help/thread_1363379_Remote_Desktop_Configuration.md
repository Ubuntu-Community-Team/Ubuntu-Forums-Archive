---
title: "Remote Desktop Configuration"
date: 2009-12-24
forum: General Help
---

### Post by Mistrblank on 2009-12-24
Ok I think I found my problem for odd problem of the year just a week before the end of it.  

I have two systems at home, both are running 9.10.  One is 64-bit and one is only 32.  The 64-bit system is an upgraded version from an initial install of 8.04 that I've upgraded each release (and at one time remote desktop did work).  In both systems, I go to System>Preferences>Remote Desktop and enable remote for viewing and controlling and enable a password for security.  

When I try to connect with my Mac or Tightvnc from my Win7 host on the same network, nothing connects.  I get a "not offering a supported security" message and it will not connect.  I get the same error connecting to either machine.  

I've tried removing the password.  I've tried turning compiz off.  I've tried rebooting.  I've checked for port 5900 and I see it listening:

user@ubuntu-1:~$ netstat -an | grep 5900
tcp6       0      0 :::5900                 :::*                    LISTEN     
user@ubuntu-1:~$ 


So I'm thinking it's a 9.10 issue.  I came into work today and started a 9.10 virtual server on Vbox and download tightvnc.  Enable Remote desktop on the vm and connect right away with tightvnc.  So now I'm really banging my head.  I don't really want to reinstall either system just to see if that fixes it(not that I think it would considering I used the same CD for the 32bit home system as I did to install the VM at work).  

Any ideas at this point would be welcome.

---

