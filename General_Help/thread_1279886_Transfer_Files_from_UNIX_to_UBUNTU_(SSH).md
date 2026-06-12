---
title: "Transfer Files from UNIX to UBUNTU (SSH)"
date: 2009-10-01
forum: General Help
---

### Post by Aiton on 2009-10-01
I have a school account on a unix system and I would like to transfer my files over to my ubuntu computer, or better yet create the drive on my computer. I downloaded sshfs but not sure how to use it.

My school directory is itxunix.albany.edu so would it be something like sshfs (username)@itsunix.albany.edu -localhost. I am very beginner at this

---

### Post by trstncmpbll on 2009-10-01
why not keep it simple and throw them on a memory key

---

### Post by Aiton on 2009-10-01
I am not sure how to do that. I figured out how to do it but I have another issue now.

I did > sudo sshfs (username)@itsunix.albany.edu: ./Desktop/"S Drive"

but now when I try to double click it. it says Could not display "/home/aiton/Desktop/S Drive". and when I try to remove it it says "failed to remove: Device or resource busy"

---

### Post by karlson on 2009-10-01
> **Aiton said:**
> I am not sure how to do that. I figured out how to do it but I have another issue now.

I did 

but now when I try to double click it. it says Could not display "/home/aiton/Desktop/S Drive". and when I try to remove it it says "failed to remove: Device or resource busy"

If you are logging into the school computer from your UBUNTU machine then do this:

sudo scp -r <username>@<school machine>: /<path to your key>

---

### Post by Altadena on 2009-10-01
[FONT=Arial][SIZE=2]Hi Aiton,

You can follow this procedures to transfer file encrypted with ssh:

[/SIZE][/FONT]   
[LIST=1]
[*][FONT=Arial][SIZE=2]install openSSH (the installation also create the ssh daemon that will start at system startupu);
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]configure the the port you want to use for ssh tunneling (the default is 22) in the file  [/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=&quot]/etc/ssh/sshd_config;[/FONT][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][FONT=&quot]make sure this port is open on your Ubuntu server firewall and on the school network firewall.  You should contact the school network administrator to make sure that the port you want to use is open for TCP;[/FONT][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][FONT=&quot]install vsftpd server on Ubuntu [/FONT][/SIZE][/FONT]```
sudo apt-get install vsftpd
```[FONT=Arial][SIZE=2]. this program is a ftp server for Ubuntu that supports SSH file transfer;[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Main configuration settings for vsftpd:[/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=2]No anonymous[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]SSL enable (this ensures that you can use FTPES from a ftp client);[/SIZE][/FONT]
[/LIST]
 
[*][FONT=Arial][SIZE=2]By default, users will have access to their 'home' directory with ftp.  if you need access to other directory of your Ubuntu system, you should create symbolic links from the user's home directory to the directory you want to transfer files to.  To create symbolic links yo use the command ```
ln -s <directory>
```[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][FONT=&quot]install FileZilla on your home computer. FileZilla is an ftp client very easy to use that supports ftps (ftp over ssh) file transfer. There is also a portable version of FileZilla that you can install on a USB pen and use with any computer;[/FONT][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][FONT=&quot]start FileZilla[/FONT][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][FONT=&quot]Use the following connection string to connect to the remote Ubuntu server (I made the assumption that you are going to use port 22):[/FONT][/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=2][FONT=&quot]ftpes//ubuntuserver.org:22; user id; password.[/FONT][/SIZE][/FONT]
[/LIST]
 
[/LIST]
[FONT=Arial][SIZE=2]Good luck :),

-A[/SIZE][/FONT]

---

### Post by Aiton on 2009-10-01
> If you are logging into the school computer from your UBUNTU machine then do this:

sudo scp -r <username>@<school machine>: /<path to your key>

ok thanks and how would I delete or open the folders. to delete i try sudo rmdir (Directory) and it says failed to remove Directory not empty

and to open it says I dont have permission.

Also how would I mount the drive onto my desktop instead of transferring everything

---

### Post by karlson on 2009-10-01
> **Aiton said:**
> ok thanks and how would I delete or open the folders. to delete i try sudo rmdir (Directory) and it says failed to remove Directory not empty

and to open it says I dont have permission.


ls -ld <directory> to see what the ownership and permissions are

rm -rf <directory> to remove it.


> Also how would I mount the drive onto my desktop instead of transferring everything

Why would you want to do this rather then copy everything and then remove what you don't need?

---

### Post by Aiton on 2009-10-01
> **karlson said:**
> ls -ld <directory> to see what the ownership and permissions are

rm -rf <directory> to remove it.




Why would you want to do this rather then copy everything and then remove what you don't need?

ok one more question. if I do ls -ld and it shows ownership how do I change permissions on it lets say from root to the user

---

### Post by karlson on 2009-10-01
> **Aiton said:**
> ok one more question. if I do ls -ld and it shows ownership how do I change permissions on it lets say from root to the user

Not sure you can on a key drive without reformatting it.  I think that in general those drives are FATXX formatted and permissions are actually implied rather then real.

---

### Post by The Cog on 2009-10-01
Maybe I'm a bit late to this party, but when I want to do ssh transfers, I normally use nautilus. In the address bar, type an address like **sftp://username@itsunix.albany.edu** and it will ask for the password. Or use the menu **File | Connect to server...**

---

