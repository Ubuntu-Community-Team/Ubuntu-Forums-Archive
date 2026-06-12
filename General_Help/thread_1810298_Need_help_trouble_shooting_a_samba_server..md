---
title: "Need help trouble shooting a samba server."
date: 2011-07-22
forum: General Help
---

### Post by Keypel on 2011-07-22
Need help trouble shooting a samba server.

Here is the output of findsmb

```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.1     OPENWRT       +[WORKGROUP] [Unix] [Samba 3.0.24]
192.168.1.15    FREENAS        [WORKGROUP] [Unix] [Samba 3.5.8]
192.168.1.200   PC-01          [WORKGROUP] [Unix] [Samba 3.5.4]
```

The one I am havening problems with is OPENWRT samba server.

It is 99% working. 
"xbox" can list/read/write, 
"Windows Explorer" can list/read/write
"Nautilus" can list/read/write
but "Media Companion" can't even list.

I think I can eliminate Media Companion as the problem since all other samba servers work with it.

I want to trouble shoot this but don't even know where to start. How do I figure out what makes OPENWRT samba server different from the other 100% working FREENAS and PC-01 Servers?

How would you go about trouble shooting this?

--

---

### Post by capscrew on 2011-07-22
> **Keypel said:**
> Need help trouble shooting a samba server.

Here is the output of findsmb

```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.1     OPENWRT       +[WORKGROUP] [Unix] [Samba 3.0.24]
192.168.1.15    FREENAS        [WORKGROUP] [Unix] [Samba 3.[COLOR="Red"]**5.8**[/COLOR]]
192.168.1.200   PC-01          [WORKGROUP] [Unix] [Samba 3.[COLOR="Red"]**5.4]**[/COLOR]
```

The one I am havening problems with is OPENWRT samba server.

It is 99% working. 
"xbox" can list/read/write, 
"Windows Explorer" can list/read/write
"Nautilus" can list/read/write
but "Media Companion" can't even list.

I think I can eliminate Media Companion as the problem since all other samba servers work with it.

I want to trouble shoot this but don't even know where to start. How do I figure out what makes OPENWRT samba server different from the other 100% working FREENAS and PC-01 Servers?
The difference is in the versions of Samba.  See the red highlights above. Is it important?  It sure looks like it is.> 

How would you go about trouble shooting this?

--

You can up the debugging using the -d3 switch with the commands.  It will report to the screen (STDOUT)

You can use *findsmb* or *smbclient* or *smbtree*.  The command *smbtree* is useful as it browses the LAN for all shares (in use or not).  The command *smbclient* queries a specific host.

I use them like this```

findsmb -d3
smbtree -d3
smbclient -d3 -L <host>
```

---

