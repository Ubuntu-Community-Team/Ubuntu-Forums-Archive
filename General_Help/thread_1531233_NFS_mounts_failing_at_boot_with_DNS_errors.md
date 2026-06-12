---
title: "NFS mounts failing at boot with DNS errors"
date: 2010-07-14
forum: General Help
---

### Post by dpatterson on 2010-07-14
I have several NFS entries in my /etc/fstab file.
Each entry generates an error during boot (from /var/log/boot.log):
[FONT=Courier New]mount.nfs: DNS resolution failed for macpro.dpc: Name or service not known
mountall: mount /mnt/BaseLines [656] terminated with status 32

[FONT=Verdana]This occurs even if I specify an IP address in fstab rather than a host name. I was really surprised by that.

The odd thing is that by the time the system is up, not only is DNS working as expected, but the NFS shares are mounted as expected.

I'd just ignore it for now, accept that it prevents Apache from starting since some of the server's files live on the NFS shares (this is a development system).

[/FONT][/FONT][FONT=Courier New][FONT=Verdana]It appears that the DNS  resolver isn't running when the mounts are attempted and that they are  attempted again later, after the resolver *is* running.

[/FONT][/FONT][FONT=Courier New][FONT=Verdana]I did an
[FONT=Courier New]$ sudo apt-get update
$ sudo apt-get upgrade
[/FONT]just in case there were updates that fixed a known issue. No joy.

Environment:
[/FONT][/FONT]
[LIST]
[*][FONT=Courier New][FONT=Verdana]VMWare Fusion 2.0.5 virtual machine[/FONT][/FONT]
[LIST]
[*][FONT=Courier New][FONT=Verdana]  2CPUs[/FONT][/FONT]
[*][FONT=Courier New][FONT=Verdana]  512MB RAM[/FONT][/FONT]
[/LIST]
 
[*][FONT=Courier New][FONT=Verdana]Ubuntu 10.04 Server install[/FONT][/FONT]
[/LIST]
[FONT=Courier New][FONT=Verdana] Suggestions?

TIA,

Dave
[/FONT][/FONT]

---

### Post by dpatterson on 2010-07-15
<bump />

---

