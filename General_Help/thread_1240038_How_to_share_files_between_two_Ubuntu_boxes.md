---
title: "How to share files between two Ubuntu boxes?"
date: 2009-08-14
forum: General Help
---

### Post by abcuser on 2009-08-14
Hi,
I know how to share files between Linux and Windows. But how does someone share files between two Linux/Ubuntu boxes?

My system: Ubuntu 9.04
Regards

---

### Post by aeiah on 2009-08-14
NFS or ssh/scp. i find ssh/scp to be fine for me because its easy to set up and i just use it to transfer video files and music from my main box to my netbook. i access folders on my main box by mounting the folders i want over ssh and browse like i would locally. NFS is a proper solution though, and one that once set up will probably offer more efficiency

---

### Post by Couto on 2009-08-14
> **abcuser said:**
> Hi,
I know how to share files between Linux and Windows. But how does someone share files between two Linux/Ubuntu boxes?

My system: Ubuntu 9.04
Regards

Are they both Ubuntu machines? I don't know if it works with one Ubuntu machine and another machine using a different Distribution.

If they are both Ubuntu Machines look into [Ubuntu One]("http://https://ubuntuone.com/")

---

### Post by amac777 on 2009-08-14
If you already know how to share files from Linux to Windows, you should be able to share between Linux and Linux using the exact same method. (One easy way: just right click the folder you want to share and setup the "sharing options".)

---

### Post by soapBAR2 on 2009-08-14
> **abcuser said:**
> Hi,
I know how to share files between Linux and Windows. But how does someone share files between two Linux/Ubuntu boxes?

My system: Ubuntu 9.04
Regards

**Don't be offput by the length of this tutorial**. I tried to cover absolutely everything, but if you have enough of a clue to install Ubuntu, 99% of what's here is stuff you'll already know ;).

Here goes - I'd highly recommend SAMBA (now called cifs). On the machine you want the server on, type:

```
sudo apt-get install samba
```

and edit /etc/samba/smb.conf

and at the bottom, add a share definition. Here's a template:

[Share]
path = /mnt/Share
comment = Share
public = yes
read only = no
guest ok = yes
valid users = user guest nobody me
write list = user nobody guest me
create mask = 0777

Most of that is pretty self-explanatory. [NAME] at the top declares the name it's being shared as, path is where the folder you want to share is located, create mask is what permissions any files created from the remote computer will be (in my template, 0777 = rwxrwxrwx = anyone can do everything to it). Valid users and write list entries MUST BE users that are registered on your server machine, and you will have to log in as that user from the remote machine if you have guest disabled (so, if your user/pass on your ubuntu machine is abcuser/mypassword and resucba/drowssapym on your second machine, you'd connect using abcuser/mypassword). Add as many share definitions as you want, share as many folders as you want. 

Once you're done with your settings, restart your SAMBA/CIFS daemon by typing

```
sudo /etc/init.d/samba restart
```

There are many ways to connect from the remote computer, but the best is to mount it in fstab. First, install smbfs using 

```
sudo apt-get install smbfs
```

Second, create an empty directory (my example is "/mnt/share") using mkdir /mnt/share.  Secondly, create a file with your user and password in it (in my example, sudo nano /location/of/your/credentials/file), using the format:

username=yourserverusernamehere
password=yourserveruserpasswordhere

(Use nano, because it properly formats the text file). Then, sudo nano /etc/fstab and add the following line:

//SERVER_SHARE_IP/SHARE_NAME /mnt/share cifs credentials=/location/of/your/credentials/file,iocharset=utf8,file_mode=0777,dir_mode=0777,nosetuids,noperm,user 0 0

Where:
SERVER_SHARE_IP is the server's IP address (you can do it by name, but unless you're using DHCP, it's easier to do it by address)
SHARE_NAME is the share name (the bit in []s from before)
/mnt/share is the share directory on the remote computer
/location/of/your/credentials/file is the location of the credentials file you created in step two.

Once you've finished editing /etc/fstab, just type

```
sudo mount -a
```

and it will mount everything in /etc/fstab for you. Also remember to protect your credentials file by chown and chgrp to root, and chmod to 700 (NB. Won't work if you save it in your home directory).

PS. Obviously, both computers need to be on and connected to your network at the time for this to work!

---

### Post by abcuser on 2009-08-14
Hi,
thanks all for help. I know have got info from Linux admin, that samba share folder is already set-up on first Linux box (it is Suse Linux).

From my Ubuntu Server I have mounted samba directory just like I would access Windows directory:
```
sudo smbmount //computer_ip_address/dir_name /mnt/samba -o username="user_id"
```

Then "ls /mnt/samba" and I can see content of shared directory.

Thanks for ideas,
Regards

---

