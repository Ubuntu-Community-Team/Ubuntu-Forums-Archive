---
title: "External Hard drive : Network"
date: 2012-08-12
forum: General Help
---

### Post by murals6 on 2012-08-12
Hi,
 I'm sorry if I'm posting at the wrong forum. The issue I have is, I have connected my Hard Drive (1TB WD Passport) to my ES3000 CisCo Router. I can see the HD by going to the router's ip address 192.168.1.1 . I would like to know how to access this through my Desktop and Laptop, both are in the same network running ubuntu 12.04.

I'm new to Ubuntu. Please help.

Thanks in Advance.

Murali

---

### Post by termite2001 on 2012-08-16
I have a WD 3TB networked through the host computer. I just told it to share the drive.

---

### Post by OM55 on 2012-08-16
You can also mount the network drive. Here is how to do it:

1. Create the mount point: mkdir /<mount point>
For example:
```
mkdir /home/YourUserName/MyPassport

```2. Mount the network drive (in this example the owner of the mount is 'root' so will be read-only for regular users):
```
sudo mount -t cifs -o username=<your username on the share>,password=<your password on the share> //<server name or IP>/<share name> /MyPassport

```or (a Linux EX4 drive)

```
sudo mount -t smbfs -o username=<your username on the share>,password=<your password on the share> //<server name or IP>/<share name> /<mount point>

```For example (using 192.168.1.1 as the drive's IP):

```
sudo mount -t cifs -o username=YourShareUserName,password=YourSharePassword //192.168.1.1/ShareName /home/YourUserName/MyPassport

```3. To mount the share with full read-write permissions (as long as the share allows write permission) add 'uid=<your Linux username'>:

```
sudo mount -t cifs -o uid=<your local Linux username>,username=<your username on the share>,password=<your password on the share> //<server name or IP>/<share name> /<mount point>

```For example (using 192.168.1.1 as the drive's IP):

```
sudo mount -t cifs -o uid=YourLocalUserName,username=YourShareUserName,password=YourSharePassword //192.168.1.1/X /home/YourUserName/MyPassword

```Notice that all those mounts will disappear after the next boot. So you can either create a shell script that will auto-mount when you need it, or make the mount permanent by making the changes in the /etc/fstab file

Hope that helps!

---

