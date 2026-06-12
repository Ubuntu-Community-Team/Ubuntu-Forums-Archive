---
title: "cifs errors at startup"
date: 2011-01-14
forum: General Help
---

### Post by themainliner on 2011-01-14
OK I seen and frown through several posts trying to address this issue, or similar issues. I'll be honest up front my issues is essentially...well cosmetic I guess.

I want to be able to get rid of these cifs errors that are stopping me going form the loading screen (Ubuntu 10.10, with four changing colour dots under it) to the login screen - **without a screen full of output text**. When I log in, despite all the errors my network drives are connected and ready to use.

This is what my /etc/fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda2 during installation
UUID=1fcdfb17-1579-4629-88a6-588d72b396e9 /	ext4    errors=remount-ro	0       1

# swap was on /dev/sda3 during installation
UUID=efcd6c71-67ee-42a0-8652-bb29293afe4d	none	swap	sw		0       0

/dev/scd0       	/media/cdrom0   	udf,iso9660 user,noauto,exec,utf8 	0       0
/dev/sda2		/media/Games		ext4    defaults			1       2

# /dev/fd0        	/media/floppy0  auto    rw,user,noauto,exec,utf8 	0       0

//192.168.1.10/sharename	/mnt/sharename	cifs	credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev 0 0
//192.168.1.10/anothersharename	/mnt/anothersharename	cifs	credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev 0 0

```

This is a selection from my logs:
```
messages
...
Jan 14 20:13:56 moonbase kernel: [   23.354318] CIFS: Unknown mount option _netdev
Jan 14 20:13:56 moonbase kernel: [   23.362951] CIFS: Unknown mount option _netdev
Jan 14 20:13:56 moonbase kernel: [   23.366296] CIFS: Unknown mount option _netdev
Jan 14 20:13:56 moonbase kernel: [   23.446656] CIFS: Unknown mount option _netdev
Jan 14 20:13:56 moonbase kernel: [   23.455754] CIFS: Unknown mount option _netdev
Jan 14 20:13:56 moonbase kernel: [   23.556149] CIFS: Unknown mount option _netdev
...
```
```
dmesg
...
[   23.353825] Slow work thread pool: Starting up
[   23.354318] CIFS: Unknown mount option _netdev
[   23.362951] CIFS: Unknown mount option _netdev
[   23.366296] CIFS: Unknown mount option _netdev
[   23.446656] CIFS: Unknown mount option _netdev
[   23.455754] CIFS: Unknown mount option _netdev
[   23.556149] CIFS: Unknown mount option _netdev
```

So I'm guessing that the netdev syntax (i.e. position in the fstab entry) is incorrect. I would dearly love to find a concrete definitive answer and remove these unattractive and beardy outputs from my loading screen.

I blame Shuttleworth for talking about paper-cuts and making me focus on the way Linux boots up compared to that other OS from Redmond... :D

---

### Post by hawkmage on 2011-01-14
Here are the options for mount.cifs 
```
Options:
    user=<arg>
    pass=<arg>
    dom=<arg>

Less commonly used options:
    credentials=<filename>,guest,perm,noperm,setuids,nosetuids,rw,ro,
    sep=<char>,iocharset=<codepage>,suid,nosuid,exec,noexec,serverino,
    mapchars,nomapchars,nolock,servernetbiosname=<SRV_RFC1001NAME>
    directio,nounix,cifsacl,sec=<authentication mechanism>,sign

Options not needed for servers supporting CIFS Unix extensions
    (e.g. unneeded for mounts to most Samba versions):
    uid=<uid>,gid=<gid>,dir_mode=<mode>,file_mode=<mode>,sfu

Rarely used options:
    port=<tcpport>,rsize=<size>,wsize=<size>,unc=<unc_name>,ip=<ip_address>,
    dev,nodev,nouser_xattr,netbiosname=<OUR_RFC1001NAME>,hard,soft,intr,
    nointr,ignorecase,noposixpaths,noacl,prefixpath=<path>,nobrl
```
I am not sure what you are trying to do with that option but it is not listed.

---

### Post by themainliner on 2011-01-14
I had understood that _netdev was a mount.cifs option to prevent the command being executed before the networking components we available. If I don't use that option I get a variety of network not available options.

So as I'm not getting them _netdev appears to be doing something...but returning errors of it's own...

*bashes head on desk*

---

### Post by themainliner on 2011-01-14
So the _netdev option seems to be invalid.

These are my usually boot screen spoilers:

**boot.log**```
mount error(101): Network is unreachable

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

mountall: mount /mnt/share1 [1262] terminated with status 32

mount error(101): Network is unreachable

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

mountall: mount /mnt/share2 [1380] terminated with status 32

mount error(101): Network is unreachable

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

mountall: mount /mnt/share3 [1352] terminated with status 32

mount error(101): Network is unreachable

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

mountall: mount /mnt/share4 [1369] terminated with status 32

mount error(101): Network is unreachable

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

mountall: mount /mnt/share5 [1386] terminated with status 32
```

---

