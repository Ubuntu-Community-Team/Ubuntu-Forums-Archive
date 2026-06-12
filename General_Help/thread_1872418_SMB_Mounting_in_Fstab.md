---
title: "SMB Mounting in Fstab"
date: 2011-10-30
forum: General Help
---

### Post by BULLIT22 on 2011-10-30
Hey all, 

Got an fstab mounting question. I successfully mounted my smb shares from another PC on my Ubuntu 10.10 desktop no problems. When I tried to set this up on my laptop running 11.10, It will not mount. Fstab entry looks like this,

//My-PC/media /media/server cifs credentials=/root/smb/cred,rw,iocharset=utf8,uid=1000,gid=1000 0 0

When I try and mount manually with ,

mount //My-PC/media 

I get this for the output,

mount: only root can mount //My-PC/media

Any help would be great.

---

### Post by Slim Odds on 2011-10-30
> **BULLIT22 said:**
> Hey all, 

Got an fstab mounting question. I successfully mounted my smb shares from another PC on my Ubuntu 10.10 desktop no problems. When I tried to set this up on my laptop running 11.10, It will not mount. Fstab entry looks like this,

//My-PC/media /media/server credentials=/root/smb/cred,rw,iocharset=utf8,uid=1000,gid=1000 0 0

When I try and mount manually with ,

mount //My-PC/media 

I get this for the output,

mount: only root can mount //My-PC/media

Any help would be great.
```
sudo mount //My-PC/media 

```

---

### Post by Rhizoid on 2011-10-30
Your fstab entry will need the user option set to allow an ordinary user (i.e. other than root)to mount a filesystem.

If you add the user option as above, they likely won't have permissions to use the credentials file stored in root's home directory - I'd suggest moving it to the user's home directory instead: e.g. credentials=/home/user/.credentials/credentials.file as root will have rights to view it in addition to the user.

What output do you get if you issue: ```
ping My-PC
``` in terminal?

---

### Post by BULLIT22 on 2011-10-30
> **Rhizoid said:**
> Your fstab entry will need the user option set to allow an ordinary user (i.e. other than root)to mount a filesystem.

If you add the user option as above, they likely won't have permissions to use the credentials file stored in root's home directory - I'd suggest moving it to the user's home directory instead: e.g. credentials=/home/user/.credentials/credentials.file as root will have rights to view it in addition to the user.

What output do you get if you issue: ```
ping My-PC
``` in terminal?


I tried that as well. I put a set of creds in my home directory and changed everything in the fstab file and tried then. still got the same output from mount. I can also access the SMB shares just fine through the network browser in Ubuntu. tried PING and it connected just fine.

---

### Post by BULLIT22 on 2011-10-30
Cancel that...just tried ping again and it is no longer working.

---

### Post by Rhizoid on 2011-10-30
> **BULLIT22 said:**
> Cancel that...just tried ping again and it is no longer working.

Likely your router isn't doing name resolution for your LAN - either use samba for name resolution if you need it to be more dynamic, or just change the My-PC bit to the IP address of My-PC if this is a one off.

Cheers,

---

### Post by BULLIT22 on 2011-10-30
> **Rhizoid said:**
> Likely your router isn't doing name resolution for your LAN - either use samba for name resolution if you need it to be more dynamic, or just change the My-PC bit to the IP address of My-PC if this is a one off.

Cheers,

The router is doing name resolution as my other PC's are connecting to the server just fine with this setup. Only difference is the updated OS on the Laptop.

---

### Post by Rhizoid on 2011-10-30
> **BULLIT22 said:**
> The router is doing name resolution as my other PC's are connecting to the server just fine with this setup. Only difference is the updated OS on the Laptop.

I'd give it a try with the IP address in fstab and see if it works - at least that will give you connectivity.  If that fails then something else is the problem.

---

### Post by BULLIT22 on 2011-10-30
> **Slim Odds said:**
> ```
sudo mount //My-PC/media 

```


trying this gives me a error  about wrong fs type.

---

### Post by BULLIT22 on 2011-10-30
> **Rhizoid said:**
> I'd give it a try with the IP address in fstab and see if it works - at least that will give you connectivity.  If that fails then something else is the problem.

Alright, just tried this and still getting no connectivity to the server through mount. error,

Only root can mount

---

### Post by BULLIT22 on 2011-10-30
Hooked it up via LAN cable and still not working. Same router.

---

### Post by Slim Odds on 2011-10-30
> **BULLIT22 said:**
> trying this gives me a error  about wrong fs type.

Add the file system type to your fstab

---

### Post by BULLIT22 on 2011-10-30
> **Slim Odds said:**
> Add the file system type to your fstab

I'm using cifs on the other PC's and it works.

---

### Post by Rhizoid on 2011-10-30
```
sudo mount -t cifs -o credentials=/path/to/credentials.file,uid=1000,gid=1000 //ip.address.of.server/sharename /mount/point
```

Edit the above with your info in place and run it in terminal - lerrus know how it goes!

---

### Post by BULLIT22 on 2011-10-30
> **Rhizoid said:**
> ```
sudo mount -t cifs -o credentials=/path/to/credentials.file,uid=1000,gid=1000 //ip.address.of.server/sharename /mount/point
```Edit the above with your info in place and run it in terminal - lerrus know how it goes!

Worked this way with the IP address, not with the name. when I change fstab to IP it will not mount

---

### Post by Rhizoid on 2011-10-30
> **BULLIT22 said:**
> Worked this way with the IP address, not with the name. when I change fstab to IP it will not mount

Try this in fstab;

```
//ip.address.of.server/sharename    /mount/point    cifs    user,credentials=/path/to/credentials.file,uid=1000,gid=1000
```

To be able to mount as an ordinary user, make sure the user has rights to at least read the credentials file.

Cheers,

---

### Post by BULLIT22 on 2011-10-30
That worked fine. although at the rate my IP changes I'll be changing it every 2 weeks. Need to find a better way....

---

### Post by Slim Odds on 2011-10-30
> **BULLIT22 said:**
> That worked fine. although at the rate my IP changes I'll be changing it every 2 weeks. Need to find a better way....

Look into winbind

---

### Post by Rhizoid on 2011-10-31
> **Slim Odds said:**
> Look into winbind...or just fix the IP address of the serving computer.  Who wouldn't want a fixed IP for a server?

---

