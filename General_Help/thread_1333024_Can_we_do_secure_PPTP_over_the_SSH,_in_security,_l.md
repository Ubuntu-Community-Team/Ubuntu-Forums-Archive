---
title: "Can we do secure PPTP over the SSH, in security, like a VPN?"
date: 2009-11-21
forum: General Help
---

### Post by frenchn00b on 2009-11-21
Since Openvpn is too complicated, i.e. not Human to be installed and not standard, as microsoft, PPTP over SSH could be a solution?

Is this secured? Any ideas how to make it, if it is still an up to date way to be in our network?

Is PPTP still valuable tool. It is said not to use it anymore.

If ok, is there HOWTO / TUTO good for Debian Squeeze?

```
I'm one of those paranoid types. Is it possible to ssh tunnel my samba mount?

Sure it is. The following lines on a shell should have the desired result.
ssh -f -N -L 9900:myserver.cims.nyu.edu:139 myname@myserver.cims.nyu.edu

mount -t smbfs -o username=myname,port=9900 //localhost/myname /local.mount.point

```

can I do something like this for pptp? whcih port?

[B][COLOR="Red"]pptp is not secure but is more standard than openvpn. 
openvpn needs lot of exe and complication. 
You take windows XP, setup the connection with pptp and it works 
no openvpn exe files. 

[/COLOR][/B]

--
I found this doc. but ok , [http://help.lockergnome.com/windows/...ict555941.html](http://help.lockergnome.com/windows/...ict555941.html)

---

