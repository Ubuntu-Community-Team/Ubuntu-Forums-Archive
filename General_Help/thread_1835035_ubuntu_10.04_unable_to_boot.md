---
title: "ubuntu 10.04 unable to boot"
date: 2011-08-28
forum: General Help
---

### Post by ashv3524 on 2011-08-28
Hi, while trying to upgrade to a newer version of GIMP using Debian Sid, synaptic got messed up and the libpango1 package broke. To fix it, I tried removing it, which also removed mountall and plymouth. Foolishly, I of course rebooted, and now the system won't boot.... the text boot error messages refer to filesystems being read-only, and then it just hangs. Recovery mode doesn't seem to function either. Is there a way for me to get those packages re-installed using a recovery/live cd?

the last error messages are:
init: plymouth-stop pre-start process (1030) terminated with status 2
init: unable to connect to the system bus: failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory
init: ureadahead main process (386) killed by ABRT signal

Any help getting my system running again would be much appreciated....

---

### Post by ashv3524 on 2011-08-28
I have been able to access the filesystem using a 10.04 livecd. Is there a way for me to copy/install mountall and plymouth to the filesystem of the broken machine? What files would I need to copy from where? Any help would be greatly appreciated!

---

### Post by ashv3524 on 2011-08-30
For anyone who might run into this or a similar issue in future, I was able to fix this problem by downloading the latest packages for 10.04 amd64 for plymouth, upstart and mountall from packages.ubuntu.com (for example [http://packages.ubuntu.com/lucid-updates/upstart](http://packages.ubuntu.com/lucid-updates/upstart)), copying the binary files within those packages to their respective folders, and then restarting the computer. 

I used archive manager to extract the binaries from their amd64 .deb files, and archive manager also showed me the destination paths for the files. I used the 10.04 livecd to access the filesystem on the busted pc.

---

