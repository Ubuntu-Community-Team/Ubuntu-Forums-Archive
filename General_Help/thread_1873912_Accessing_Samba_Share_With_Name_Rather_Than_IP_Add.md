---
title: "Accessing Samba Share With Name Rather Than IP Address"
date: 2011-11-02
forum: General Help
---

### Post by kaprikawn on 2011-11-02
Hi,

I'd like to access a samba share from my Ubuntu machine using the name of the server rather than the IP address because the server has not got a static IP address.  I'm doing the mount using the /etc/fstab file.  The following works fine:

```
//192.168.1.3/pandrom /home/me/pandrom     cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777   0 0
```

However, given the lack of static IP on the server, I actually need to do it using the following:

```
//otter/pandrom /home/me/pandrom     cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777   0 0
```

But doing it like this and then doing a 'sudo mount -a' throws up the following error message:

> mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

The server is running Angstrom Linux if that makes any difference.

Where am I going wrong?

Thanks in advance.

---

### Post by galvatron408 on 2011-12-03
I don't think you understand the purpose of names and ip addresses.

Your question is like saying... I'd like to call my friend on my cell phone using his name rather than his phone number because my friend doesn't have a static phone number.

---

### Post by thaelim on 2011-12-03
What are trying to do is definitely possible (contrary to what the last poster said).

First a few questions:
[LIST]
[*]Can you access the server using its name in e.g. Nautilus? This would confirm that CIFS name resolution is working.
[*]Are you trying to run mount -a after a reboot? If so the mount opereation might already in progress - hence the error.
[/LIST]

---

### Post by quanumphaze on 2012-01-06
As another user experiencing the same problem I would like to add some more info. It was once working with smbnetfs before I upgraded to 11.10

For me it appears to be a CIFS name resolution problem
This works fine
```
sudo mount.cifs //192.168.0.2/nameofshare ~/mnt -o uid=1000,gid=1000,user=X,password=X
```
But if I use the server's name it fails.

If I use smbnetfs or the smb kioslave in KDE it only shows me the workgroups. Using the IP in KDE works but smbnetfs doesn't allow for that.

---

### Post by bab1 on 2012-01-06
> **quanumphaze said:**
> As another user experiencing the same problem I would like to add some more info. It was once working with smbnetfs before I upgraded to 11.10

For me it appears to be a CIFS name resolution problem
This works fine
```
sudo mount.cifs //192.168.0.2/nameofshare ~/mnt -o uid=1000,gid=1000,user=X,password=X
```
But if I use the server's name it fails.

If I use smbnetfs or the smb kioslave in KDE it only shows me the workgroups. Using the IP in KDE works but smbnetfs doesn't allow for that.

It is a netbios name resolution problem.  Both Windows and Samba use netbios (WINS) protocols to achieve this.  One of the good things about WINS is the ability to have a fixed COMPUTER NAME and a DHCP assigned IP address.  There are several ways to provide netbios name resolution.  The easiest method for Samba (SMB/CIFS) is to broadcast the netbios name and IP address.  This can be setup in the smb.conf file.  The line with *name resolve order * can be uncommented and should look like this```
name resolve order = bcast
```

This should be enough for that host to broadcast its netbios name to the rest of the network.  One of the machines will be designated as the Local Master Browser of the network and create a list of all the computers that have shares  

If the Samba client routines are installed installed (cifs-utils I believe), you should then be able to mount the share by //netbios_name/share_name.  You should also be able to use a GUI to browse by name.

The only caveat is the netbios name should be 15 characters or less.  If the hostname is longer it will get mangled.  You can prevent that by assigning a netbios name in the smb.conf file.  In the [global] section add ```
netbios name = <some_name>
```  This insures that the name is 15 characters or less and you will recognize this name.

Edit:  You DO NOT need a WINS server with this solution nor do you need winbind (a utility to map Windows *user* accounts to Linux user accounts

---

### Post by quanumphaze on 2012-01-10
Thanks bab1! Works for me now.

I'll experiment a bit now that I know where to look.

---

