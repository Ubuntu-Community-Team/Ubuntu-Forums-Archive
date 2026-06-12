---
title: "Restrict SSH user to one folder"
date: 2011-04-01
forum: General Help
---

### Post by NertSkull on 2011-04-01
I've looked around and haven't been able to really understand how to do this yet.

How can I set up a SSH user to access a single folder (and it's subfolders) on my system.

I want to give my brother access to a folder under /media/Data/Files

But I don't want him to access any other part of my system.

I've set up a user (using useradd and gave him a password but no home directory).

I want to have him use SSH to log in to my machine, start in the /media/Data/Files directory, and not be able to get out of that directory - but add/change/delete/etc any of the files.

Can someone point me in the right direction here?  Thanks

---

### Post by Azdour on 2011-04-01
Hi,

While I've never tried this I have found the following that may help you, see post 7:

[http://www.gossamer-threads.com/lists/openssh/users/45984](http://www.gossamer-threads.com/lists/openssh/users/45984)

---

### Post by perspectoff on 2011-04-01
If you just want him to have ability to upload/download files, then consider WebDAV instead.

Using WebDAV, he can access files from almost any browser on any computer, and from almost any OS. 

WebDAV entails setting up an Apache server and then a folder (with passwords) for the files.

Here are some instructions:

Ubuntuguide:
[http://ubuntuguide.org/wiki/U_WebDAV](http://ubuntuguide.org/wiki/U_WebDAV)

Kubuntuguide:
[http://ubuntuguide.org/wiki/K_WebDAV](http://ubuntuguide.org/wiki/K_WebDAV)

Another alternative is a FTP server, such as vsftp or proftp.

He can then use a client like FileZilla (available on all OSs).

Info:
Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Maverick#FTP_Server)

Some people even set up VPN connections, if there is a LAN with a series of folders that need to be accessed. OpenVPN is often used in this scenario.

Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#VPN_servers](http://ubuntuguide.org/wiki/Ubuntu:Maverick#VPN_servers)


Lastly, if you want to stick with SSH, you can just create a new user for him, and restrict the privileges (through user management). Just don't give him sudo or administrator privileges. You can restrict his user profile in many ways with user privileges. When he connects with SSH, he will only be able to connect with those privileges.

User privileges:
Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#User_Administration](http://ubuntuguide.org/wiki/Ubuntu:Maverick#User_Administration)

SSH:
Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#SSH](http://ubuntuguide.org/wiki/Ubuntu:Maverick#SSH)

---

### Post by NertSkull on 2011-04-01
I guess I could set up an ftp server.  

I already use SSH extensively myself.  So I'm not thrilled about the idea of having to set up another server (ftp or Webdav) just for him.  

I guess if there really isn't a way to do this with SSH I can look into that.  But I'm kind of hoping I could do it with SSH, if for no other reason I'm most familiar with that.

I know he uses WinSCP which connects to SSH pretty easily.  And I know he's familiar with Putty.

I would have thought there was a way to set up user groups and directory permissions to enforce this.  Maybe even create a hard link as a home directory to get him there first and then keep permissions to not move elsewhere. 

I haven't played with such things yet though.

---

### Post by perspectoff on 2011-04-01
Sorry, I was editing my post when you replied.

Set up a new user for him with restricted privileges. Then go ahead and use SSH. I do that on most of my computers that have multiple users.

It is worthwhile to learn how to restrict user privileges anyway. That is the main way that Linux can be more secure than other operating systems.

---

### Post by NertSkull on 2011-04-01
Excellent, I'll take a look at some of those and see what I can come up with.  Thanks

---

### Post by gradysghost on 2011-04-01
I know you've received quite a bit of help already, but I just wanted to point something out.  Use the right tool for the job.

Do you want him to just have data access?  If so, SSH is not the right tool.  SSH is an interactive protocol.  Over a local network, a Samba share might be more appropriate.  Over a WAN, FTP is probably the better option, especially since most FTP servers (ProFTPD, f. ex.) support directory lock-in natively.

---

### Post by NertSkull on 2011-04-01
Yeah I'm kind of beginning to think SFTP may be the way to go.

But is there a way to allow him to log on through SSH keys.  We already have that set up and I would like to be able to keep letting him use a key based login (so he doesn't have to do passwords).

I'm looking into proftp right now to see if that's possible, but I haven't seen it yet

---

### Post by NertSkull on 2011-04-01
SUCCESS!!!

So, from what I can tell, this is a way to do this using SSH.  And its actually pretty simple, and seems to work just fine.  I am not a security expert, so take it for what its worth.

OpenSSH apparently has this ability built in, few people just seem to use it (admittedly setting up ftp servers probably isn't that bad).  Here's what you have to do (or at least what I did to make it work.

1. Decide where you want to put the users directory.  I didn't want him in my home directory but on a 2nd HDD that has more room.  You could make this work using the /home directory as well though.

2. Set up that directory.  The entire path MUST be owned by root.

```
sudo mkdir /media/Data/sftp_users
```

3. Then make sure that directory is all root

```
sudo chown root:root /media
sudo chown root:root /media/Data
sudo chown root:root /media/Data/sftp_users
```

4. Then make the user account (i.e. if the username was to be john)

```
sudo adduser --home /media/Data/sftp_users/john john
```
This will create the user name, directory and group called john

5. Create a group that you want to put the new user in.  Something like sftponly

```
sudo groupadd sftponly
```

6. Make sure the user is added to the group.  Also **change ownership of their directory to root**

```
sudo usermod -a -G john john
sudo usermod -a -G sftponly john
sudo chown root:root /media/Data/sftp_users/john
```

7. Now the user is set up, so we set up OpenSSH.  First step is to set up the internal sftp server.  Open up your sshd_config file and change the Subsystem line to this (I commented it out and added a new one)
```
sudo nano /etc/ssh/sshd_config
```
```
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
```

8. Now set up the chroot environment - add these lines at the BOTTOM of your sshd_config (you should still be in it, or sudo nano /etc/ssh/sshd_config)

```
Match Group sftponly
        ChrootDirectory /media/Data/sftp_users/%u
        ForceCommand internal-sftp
        PasswordAuthentication yes
        X11Forwarding no
        AllowTcpForwarding no

```

Match the "sftponly" here to whatever your group is.

The %u will allow any user set up appropriately to use this.  You could just put in the specific username if you only had one (that's probably what I'll end up doing)

Also I took out the "PasswordAuthentication yes" line, because I'll be using SSH keys to authenticate, but you could do that.

9. Save and restart the ssh server (sudo restart ssh)

10. Done.  You should be able to log in to your SSH server now using something like "sftp john@localhost" or whatever you normally would use.

11. You probably need to create a "working" directory.  The user directory has to be owned by root for the chroot and sftp stuff to work.  But, because of that, the user can't do anything within that folder.  So I created a sub-directory with user ownership (I created a "john" subdirectory) that the user owns.  Then they can create files within that.

NOTE:: I just barely got this working, I don't know how well it works, or how secure it is. 

All I know is I can't change directories out of that home directory.  If I find that there are problems I'll post what I find out.

Also there are much quicker commands to do much of this, but I wanted to try and be clear on what I did (mainly for my own future referrence) but it may be useful to others also.

---

