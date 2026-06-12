---
title: "Samba share not mounted at boot"
date: 2006-06-19
forum: General Help
---

### Post by jeff777 on 2006-06-19
I recently switched to Ubuntu from Gentoo.  Ubuntu has worked great for me apart from one problem:  The shared drive from my Windows computers is not mounted automatically at boot.  

I've added it to my /etc/fstab and I am able to mount the drive once the system boots.  If I type sudo mount -a the drive is available.  The only problem is that it is not mounted automatically.  

Since mount -a works, I'm thinking the init script that mounts the network drive is not being run.  I'm not really familar with how init works in Ubuntu.  Can anyone give me any suggestions on solving this problem?  Here is my /etc/fstab:

 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
//Ravana/Torrents /home/jeff/Torrents cifs defaults,uid=1000,gid=1000,guest    0	0

---

### Post by nemesa on 2006-06-19
1, It should works great, maybe you should add "auto" manually.

Related part from fstab:

```

//192.168.0.2/INTERNET  /media/remote/sxq1 smbfs user,auto,username=xxx,password=xxx,uid=1000,gid=1000 0 0

```

and with these options it works.

2, NOTE, that there is a bug related to this feature:

[https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874)
(read the post at 2006-06-13 07:43:05 UTC to fix the problem)

---

### Post by ayoli on 2006-06-19
i'm not sure, but did you try IP instead of hostname in your fstab line, ie:

//xxx.xxx.xxx.xxx/Torrents /home/jeff/Torrents cifs defaults,uid=1000,gid=1000,guest 0 0

---

### Post by ayoli on 2006-06-19
[QUOTE=nemesa]1, It should works great, maybe you should add "auto" manually.
[/QUOTE]
auto should be default and useless, look at other lines such as :
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda2 /home ext3 defaults 0 2
they're mounted automatically without auto option

---

### Post by jeff777 on 2006-06-19
Thanks for the responses.  Yes, I have tried changing the hostname to the ip address.  I have also tried setting smbmount and smbumount setuid root and adding the user line to fstab.  Neither has helped.  I don't think my problem is related to the bug either, as my system doesn't lock up.

I suspect the problem is that the script that mounts the network shares during boot is not running correctly.  Can anyone tell me the name and/or location of the init script that should mount the samba share?  How can I confirm if it's being run?  I don't see any boot messages relating to network drive being mounted.

---

### Post by mike4ubuntu on 2006-06-20
Who maintains smbfs?  I went to:

[HTML] https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/+viewstatus[/HTML]

to see what the status of the bug fix was, but there is nobody even assigned to it.  Is there an official bug tracker for Ubuntu?

---

### Post by nemesa on 2006-06-20
[QUOTE=mike4ubuntu]Who maintains smbfs?  I went to:

[HTML] https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/+viewstatus[/HTML]

to see what the status of the bug fix was, but there is nobody even assigned to it.  Is there an official bug tracker for Ubuntu?[/QUOTE]

[https://launchpad.net/distros/ubuntu/+source/hal/+bug/50141](https://launchpad.net/distros/ubuntu/+source/hal/+bug/50141)

---

### Post by jeff777 on 2006-06-21
I solved the problem by adding "mount -a" to /etc/rc.local.  The samba share is mounted when the computer finishes booting, so I guess that's good enough for me.  
Theoretically, init should take care of this, but whatever.  Linux is like that.

I'll remove the line from rc.local in a couple of months and see if whatever is causing this problem has gone away. :D

---

