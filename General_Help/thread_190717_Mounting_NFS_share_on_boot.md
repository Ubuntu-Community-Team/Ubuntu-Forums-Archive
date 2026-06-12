---
title: "Mounting NFS share on boot"
date: 2006-06-06
forum: General Help
---

### Post by juicybananahead on 2006-06-06
Greetings! I'm currently experiencing a niggling problem: the NFS share in my /etc/fstab is not mounting at boot. Once I've booted up ```
sudo mount -a
``` will successfully mount the NFS share, which means that there is no problem with fstab yet it does not mount at bootup. Why? I didn't have this problem with Breezy. Here's my fstab anyhow:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

# NFS on cerberos
cerberos:/home/group    /home/cerberos  nfs     ro,soft,intr,rsize=8192 0       0

```

Any help gratefully received!
// juicy

---

### Post by flar on 2006-06-06
I also have this exact problem. I thought it might just have been me but now I'll file a bug report.

---

### Post by juicybananahead on 2006-06-08
[QUOTE=flar]I also have this exact problem. I thought it might just have been me but now I'll file a bug report.[/QUOTE]
Hmmmm, can you post the link to the bug report please, Flar?

---

### Post by Arno_A on 2006-06-08
I have the same problem. The NFS mount sometimes works ok, but quite often the first thing I have to do after bootup is to issue the sudo mount -a command.

---

### Post by juicybananahead on 2006-06-09
Bug report filed [here]("https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/49137")

// juicy

---

### Post by grendelkhan on 2006-06-09
Do you have that hostname in your /etc/hosts file or are you using a net bios name?  I mount my nfs shares by ip address and I never have problems.

Something I did discover though, I needed to have portmapper installed and move it up before nfs-common in run mode 1.

---

### Post by juicybananahead on 2006-06-09
[QUOTE=grendelkhan]Do you have that hostname in your /etc/hosts file or are you using a net bios name?  I mount my nfs shares by ip address and I never have problems.

Something I did discover though, I needed to have portmapper installed and move it up before nfs-common in run mode 1.[/QUOTE]
Hi Grendel,

That hostname (cerberos) is mapped to an ip address (192.168.1.10) using a local dns server (dnsmasq running on a Linksys WRT54G), not my own /etc/hosts file. I have portmapper installed already... but I'll try using an ip address instead of a hostname in my fstab and see if it makes a difference. What puzzles me though is that I used the exact same fstab with Breezy and didn't have this problem.

// juicy

---

### Post by patrick295767 on 2006-06-10
you might be using the autofs   [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)
  
Good how to :
[http://nfs.sourceforge.net/nfs-howto/server.html](http://nfs.sourceforge.net/nfs-howto/server.html)
  
([http://www.ubuntuforums.org/showthread.php?t=155330](http://www.ubuntuforums.org/showthread.php?t=155330))

---

