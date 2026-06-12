---
title: "copy/paste from one computer to another"
date: 2011-09-21
forum: General Help
---

### Post by Artanis.ro on 2011-09-21
Lets say that I have at my home 2 computers both running ubuntu and connected to the same router.

How can I copy some large files from one computer to another? Is it possible to mount a folder from one of the computers to the other, even if the other doesn't have sharing on that particular folder?

Please tell me how to do this from the command line.

Thank you

---

### Post by patryk77 on 2011-09-21
You can enable folder sharing with samba, but I generally just use SFTP (FTP over SSH).

sudo apt-get install openssh-server

Then you can use the sftp command from the terminal:

sftp [email]user@i.p.ad.dy[/email]

Or Filezilla:
sudo apt-get install filezilla

Just make sure to add the site as SFTP and not FTPS/FTPES

---

### Post by Cheesehead on 2011-09-21
From the command line, an easy way is to use the 'scp' command. scp copies the file using ssh, so you need to have ssh access to the target machine.

See 'man scp' for a lot of the extra options.

```
scp /path/to/local/original_file username@aaa.bbb.ccc.ddd:/path/to/target/directory/

or

scp username@aaa.bbb.ccc.ddd:/path/to/orignal_file /path/to/local/target/directory/

or even

scp username1@aaa.bbb.ccc.ddd:/path/to/original_file username2@eee.fff.ggg.hhh:/path/to/target/directory


```

---

### Post by brucehohl on 2011-09-21
You can do this with sftp and Nautilus as follows:

0- Install openssh-server on pc1

1- Open Nautilus on pc2; Press Cntr+l (lower case L) to get the Location bar.

2- In the location bar type (for example): 
sftp://user1@pc1/home/user1
sftp://<user_name>@<pc1_or_IP_address/optional/path

3- An 'Enter Password' window will appear.  Enter password for user1 (i.e. some user account on pc1, and I usually select 'Y = Remember password until you logout'

Now you are connected or 'mounted'.  An icon will appear on your desktop. To disconnect right click on the icon and select 'Unmount'.


You did ask how to do this from the command line so in that case:
0- Install openssh-server on pc1
1- Open gnome-terminal on pc2 or use a virtual terminal (Cntl+Atl+F1)
2- $ sftp user1@pc2
3- Enter password for user1 at prompt
4- You will get this prompt: sftp> 
5- Type in ? to see command help. Mostly you will be using 'cd', 'get' & 'put'

---

