---
title: "Remote Desktop on x64 Natty"
date: 2011-09-17
forum: General Help
---

### Post by test_tube_baby on 2011-09-17
Hello,

I have followed instructions on remote desktop for ubuntu on my computer. I set up port forwarding on my router to the right ports. I'm gonna do this with VNC.

Right now, I can access my computer within my network.

How do I do this from outside my network via the internet?

Help is appreciated
Thanks

---

### Post by CharlesA on 2011-09-17
One word: Don't.

VNC is very insecure as it is unencrypted and there are better methods of getting remote access to a box.

It is fine locally, but If you are going to be accessing it via the internet, I would recommend either forwarding X over ssh or looking into something such as FreeNX or TeamViewer or the like.

---

### Post by test_tube_baby on 2011-09-17
> **CharlesA said:**
> One word: Don't.

VNC is very insecure as it is unencrypted and there are better methods of getting remote access to a box.

It is fine locally, but If you are going to be accessing it via the internet, I would recommend either forwarding X over ssh or looking into something such as FreeNX or TeamViewer or the like.

Thanks for your reply Charles. I will do it using Xssh then. But can I get some more explicit instructions, as I am a newbie.

---

### Post by haqking on 2011-09-17
> **CharlesA said:**
> One word: Don't.

VNC is very insecure as it is unencrypted and there are better methods of getting remote access to a box.

It is fine locally, but If you are going to be accessing it via the internet, I would recommend either forwarding X over ssh or looking into something such as FreeNX or TeamViewer or the like.

+1

VNC sends cleartext though you can use secure versions of it.

The best way to administer is through SSH.  Open port 22 (though some change this port as it is known to be ssh) on your router and have the SSH forwarded to the LAN IP, you ssh username@wanipaddress 

You can also use teamviewer as suggested also if you are connecting to a Desktop machine running a GUI, or as mentioned ssh- X which forwards the remote X server to your local X server.

---

### Post by test_tube_baby on 2011-09-17
> **haqking said:**
> +1

VNC sends cleartext though you can use secure versions of it.

The best way to administer is through SSH.  Open port 22 (though some change this port as it is known to be ssh) on your router and have the SSH forwarded to the LAN IP, you ssh username@wanipaddress 

You can also use teamviewer as suggested also if you are connecting to a Desktop machine running a GUI, or as mentioned ssh- X which forwards the remote X server to your local X server.


Thanks,
How do I know what my wan ip address is?

---

### Post by haqking on 2011-09-17
> **test_tube_baby said:**
> Thanks,
How do I know what my wan ip address is?


look on your router is the easiest way.

or

[http://www.whatismyip.com/](http://www.whatismyip.com/) and it will tell you.

there are various CLI methods also using curl or wget

oh bear in mind it is likely unless your ISP gave you or your paid for it you wont have a static address so this address will change.  So you might want to look as _[http://dyn.com/dns/dyndns-free/](http://dyn.com/dns/dyndns-free/)_ if thats the case for a dynamic DNS name to connect to instead

---

