---
title: "Newbie here... Wifi problems?"
date: 2010-08-15
forum: General Help
---

### Post by Koolkallll on 2010-08-15
Just got Ubuntu like 20 minutes ago and was wondering how to set up Wifi connection? I have an unhidden router to connect to. Thanks.

---

### Post by fragos on 2010-08-16
If you've not configured any security in your router there's nothing to configure to access the internet but to access files between systems is another story and depends on if your networked computers are Windows or not. I'm all Linux so I can use Network File System, NFS as follows:

I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the Laptop server there must be an /etc/exports file with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree on the Laptop server. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

Run "sudo exportfs -rv" on the Laptop server for the system to read /etc/exports and allow the Desktop client access. You'll need to do this whenever you reboot your Laptop or edit /etc/rc.local and add the line "exportfs -rv" which will then run as root when the system boots.

On the Desktop client create a folder to mount to. In my case I placed that folder in my home folder. You need only do this once as it reusable.

On the Desktop client side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

