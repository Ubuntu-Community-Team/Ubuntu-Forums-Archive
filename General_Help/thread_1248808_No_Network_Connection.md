---
title: "No Network Connection"
date: 2009-08-24
forum: General Help
---

### Post by Disco Cat on 2009-08-24
I've been struggling with my computer for a while now since its network connection recently died under mysterious circumstances.  The computer was originally running 7.10, but has been upgraded over the troubleshooting period to 9.04.  When the video card kicked the bucket, the network connection seemed to go with it.

I get no internet connection, though I can use WOL from my router to start the computer up.  If using a live-cd, the internet is perfectly fine and works as it should.

I have tried changing /etc/network/interfaces both to set up a static ip and to use dhcp, but neither worked.

I upgraded Ubuntu to 9.04 using the live-cd and chroot, hoping it might autoconfig it in such a way that would resolve the problem, but it didn't.

I have also formatted and installed ubuntu 9.04 using the instructions here:
[https://help.ubuntu.com/community/Installation/OverSSH](https://help.ubuntu.com/community/Installation/OverSSH)
but it didn't help either.

At the moment, if I run "/etc/init.d/networking restart" the error returned is:
```
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
```

I don't have physical access to this computer; it is in Canada and I am in the Czech Republic.  If anyone has any idea what is wrong or can offer any clues as to where to look, I would be eternally grateful.  

_Additional Information_
cat /etc/network/interfaces:
```

## /etc/network/interfaces

#Network Config:
# The Loopback network interfaces
auto lo
iface lo inet loopback

# The primary network interfaces
auto eth0
iface eth0 inet dhcp

```

Can't think of any other files of use right now.

---

### Post by blueridgedog on 2009-08-24
So, at this point, it is a fresh install of 9.04 that hat network access when booted off of the LiveCD, but not when installed.  You have terminal access via some sort of IP to terminal interface and can run commands.  

Let's identify the hardware and see if there is a module loaded for it.  Can you post the output of the following commands?
```

ifconfig
```

and
```

lspci | grep Ethernet
```

and

```
lsmod
```

I may not be able to solve it, as it seems odd, but at least we can put our heads together.

---

### Post by Disco Cat on 2009-08-25
Thanks for the offer of help.  I ended up trying a fresh install using VNC with the live CD and it seems to have set things straight again.

---

