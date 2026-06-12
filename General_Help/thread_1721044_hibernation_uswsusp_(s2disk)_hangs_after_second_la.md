---
title: "hibernation uswsusp (s2disk) hangs after second launching"
date: 2011-04-04
forum: General Help
---

### Post by rustamych on 2011-04-04
ubuntu 10.04, laptop samsung x22, mem 2G, swap 4.5G, video ATI Radeon Hd 2400. I try to use uswsusp, command s2disk, for hibernation. First two launching  are ok, the system goes to sleep and awake very well. But third launching hands in the moment of suspending console: 

s2disl: Snapshotting system
PM: Preallocation image memory ... done (allocated 103854 pages)
PM: Allocated 415416 kbytes in 0.18 second
suspending console(s) (use no_console_suspend to debug)

I noted that after restarting the system last commands in console dissapeared. What may be the solution of the problem?

Config file:

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda5
compress = y
early writeout = y
image size = 2000000000
RSA key file = /etc/uswsusp.key
#shutdown method = platform
shutdown method = shutdown
suspend loglevel = 20
max loglevel = 100

Command swapon -s 
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	4551812	0	-1

Command sudo blkid
/dev/sda5: UUID="776fc8c2-211e-4943-a707-f2bda85d1206" TYPE="swap" 

File /etc/fstab
UUID=776fc8c2-211e-4943-a707-f2bda85d1206 none            swap    sw              0       0

File /etc/initramfs-tools/conf.d/resume
RESUME=UUID=776fc8c2-211e-4943-a707-f2bda85d1206

---

