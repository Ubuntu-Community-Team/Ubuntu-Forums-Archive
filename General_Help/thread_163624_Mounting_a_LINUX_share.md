---
title: "Mounting a LINUX share?"
date: 2006-04-21
forum: General Help
---

### Post by B3Nji on 2006-04-21
OK, here is my problem. I have followed this great guide from [http://www.ubuntuforums.org/newreply.php?do=newreply&p=611584]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=611584")

[QUOTE=FLeiXiuS]Ha, I wish things worked magically without you having to give them magical powers...

They aren't mounted, but they are viewable.  If you like to mount them...READ the jibber jabber below.

To start off, you will need smbfs.  
$ sudo apt-get install smbfs

Samba won't do it automatically.  You have to specify it to do so in your fstab file.  This is located at /etc/fstab.  You will need sudo access to write to it.  

To mount a file system temporarily.
mount -t cifs -o username=USERNAME,password=PASSWORD,uig=UID,gid=GID //IPADDRESS/SHARE /path/to/mount/to

Ok so let me explain the variables above.  

USERNAME is the username on the windows machine the share has access to.  If it's publically available the username will be 'guest'.  If this is the case then you do not need the 'password=PASSWORD' since it's PUBLICALLY AVAILABLE RIGHT!?  

The UID is the user's ID on your local machine in which to give permissions to the share.  For the default user on UBUNTU this number is 1000.  If you are using another username which you created after you installed, you will find this name in /etc/passwd.  

The GID has the same influence as UID.  GID is the group ID, basically the group to give local permissions to.  Default again is 1000 and you may look in /etc/group for other answers.

//IPADDRESS/SHARE is the remote share.  I like to use IP address, but for those who don't have a static network, meaning set IP addresses on their machines, then this won't do no good.  You could use the NetBios name.  If the computers name is fleixius with an IP of 192.168.0.65 and the share name is nick.  The remote shares location would be //fleixius/nick or //192.168.0.65/nick.

/path/to/mount/to is the location on the local machine where you want to mount the remote file system to.  This is up to you, just make sure you have permissions.  I generally like creating a folderin /mnt called network where I mount a network share.  Then I create a symbolic link from there to my home directory to make it easier accessing.

Example:
$ sudo mount -t cifs -o username=guest,uid=1000,gid=1000 //fleixius/nick /mnt/network

To mount on boot automically, MAGICALLY follow the following.

Open your /etc/fstab as sudo.
$ sudo gedit /etc/fstab

At the end of the file add something simular to the following.  By this I mean you can edit / remove parts which don't work for you.

//IPADDRESS/SHARE /path/to/mount to cifs defaults,uid=1000,gid=1000,username=USERNAME,password=PASSWORD,umask=007 0 0

Save and exit.

Voila, hope that helps.

/me waves the magic wand as I mount -a.

PS. sudo mount -a will remount the file systems located in /etc/fstab.  :-)[/QUOTE]

But I get a Permission denied. When I access my share normally it does not ask for a username and password. So I put in USERNAME=default and PASSWORD=default as suggested, it still says access denied. 

What do I do? 

Cheers for all you help.

---

### Post by Zorro on 2006-04-21
[QUOTE=B3Nji]OK, here is my problem. I have followed this great guide from [http://www.ubuntuforums.org/newreply.php?do=newreply&p=611584]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=611584")



But I get a Permission denied. When I access my share normally it does not ask for a username and password. So I put in USERNAME=default and PASSWORD=default as suggested, it still says access denied. 

What do I do? 

Cheers for all you help.[/QUOTE]


Whats the permissions on your mount point set to?  I seem to recall I had an issue with that... :/

---

### Post by B3Nji on 2006-04-21
[QUOTE=Zorro]Whats the permissions on your mount point set to?  I seem to recall I had an issue with that... :/[/QUOTE]

Do you mean my mount point of my shares in my server? or the permissions im giving it when im trying to mount the drive? 
My fstab settings on my server is simply

ext3 defaults 0 0 

next for my three hard drives I want to mount on my laptop. 

Sorry if I dont understand what you mean, I am a linux n00b.
Cheers

---

### Post by Zorro on 2006-04-21
The directory/mount point on the ubuntu machine you are trying to mount the shares to.. if you follow.. 

paste the relevant line from your fstab in here... 
 As an entry in my fstab to mount a samba share is...
//192.168.0.221/mythmusic /mnt/share smbfs rw,user,auto,username=zorro,password=#### 0 0


the directory /mnt/share is owned by the user of my machine not root... 

Im not an expert either, no doubt someone might have a clearer more exact explination..  But I'm glad to help where I can ;)

---

### Post by B3Nji on 2006-04-21
ok, what im doing is just trying to temporarly mount it atm then I will put that line into fstab.
Here is what im getting 

> ben@massive:~$ sudo mount -t cifs -o uid=1000,gid=1000 //192.168.0.2/music /media/music
Password:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
ben@massive:~$


---

### Post by Zorro on 2006-04-21
check who 'owns' /media/music and what write permisions are on it..

---

