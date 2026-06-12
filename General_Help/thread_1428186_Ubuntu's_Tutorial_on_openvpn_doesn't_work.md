---
title: "Ubuntu's Tutorial on openvpn doesn't work?"
date: 2010-03-12
forum: General Help
---

### Post by bone2006 on 2010-03-12
I was following this tutorial step by step and even repeated it on a virtual machine to make sure nothing was missing that I might have missed.

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

I'm running the latest ubuntu server with all the updates.

sudo vi /etc/openvpn/server.conf

No such file

---

### Post by bone2006 on 2010-03-12
It appears that the ubuntu tutorial is missing some steps, which I found a link on the bottom to another tutorial that shows me where the server.conf file is.

My problem now is that it's asking me for the hostname of the client.  I'm going to probably have a few clients connect to the server, so I'm not sure what to do.

[http://ubuntuguide.org/wiki/OpenVPN_server](http://ubuntuguide.org/wiki/OpenVPN_server)

---

### Post by Iowan on 2010-03-12
If the tutorial is wrong/incomplete - it would be helpful to file a bug on Launchpad.

---

### Post by akakingess on 2010-03-12
I could be wrong, but I think you just need to create the file (server.conf) yourself and then configure it as you see fit. You may be able to search to see some other peoples examples of what they have as a config file for the openvpn server and then just customize it to your needs. Again, I could be mistaken.

---

### Post by bone2006 on 2010-03-14
> **Iowan said:**
> If the tutorial is wrong/incomplete - it would be helpful to file a bug on Launchpad.

I honestly don't have enough knowledge on why it's not working, so my bug would be probably useless in tracking down the problem to the exact reason.

---

### Post by bone2006 on 2010-03-14
> **akakingess said:**
> I could be wrong, but I think you just need to create the file (server.conf) yourself and then configure it as you see fit. You may be able to search to see some other peoples examples of what they have as a config file for the openvpn server and then just customize it to your needs. Again, I could be mistaken.

Thanks, I ended up doing just that.  I googled for awhile and it appeared that the server.conf was there posted.  So I just ran the touch command and then copied and pasted the server.conf file.   Well long story short, it's not connecting and not working.

There's a few things I don't understand.  One is this in the server.conf file 
push "dhcp-option DOMAIN example.com"

I don't have a domain and really don't care to register for even a free domain if I don't have to do this.  Do I have to have a domain to have openVPN to work?  I have a static IP and have been using that just fine, but if I have to get a domain, I guess I can register for a free one?

I deleted that line and it didn't work.  I tried putting the IP address instead of the domain and it didn't work.

---

### Post by bone2006 on 2010-03-14
I appologize, I posted the wrong link for the tutorial I was following.

That tutorial told me to extract the file and the server.conf was there as well with this command

sudo gzip -d /etc/openvpn/server.conf.gz

This was the instructions I was following, but I now see that it starts off saying there's an updated instruction.  I'm going to try the updated instructions then:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by akakingess on 2010-03-14
No, you do not need to register for a domain, but it is maybe referring to your network domain (instead of a workgroup)? Also, just so you know, I have not yet gotten OpenVPN to work yet, but I am one to tinker around without reading anything and just see what I can break/make work. Part of the fun for me I guess.

---

