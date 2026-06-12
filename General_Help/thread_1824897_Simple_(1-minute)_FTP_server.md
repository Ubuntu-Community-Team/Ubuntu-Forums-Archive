---
title: "Simple (1-minute) FTP server"
date: 2011-08-14
forum: General Help
---

### Post by W3ird_N3rd on 2011-08-14
After many years of using Linux, I'm still looking for this: a simple FTP server.

Something I can just install, enter user/pass/homedir and fire it up. Boom! FTP. CLI/configfiles are okay, but I just want to be able to cut to the chase.

I don't want to mess with system users. I have no interest in virtual hosts. I don't see the point in reading pages and pages of documentation. There are plenty of things for which I do that (I'm not *that* lazy), but in this case, I just need something simple.

Examples of this on Windows are slimftpd (in 25KB!) and Filezilla server, where you can just fire them up, enter user/pass/homedir and it's done. I'm sure something like this has to exist for Linux - I'm just unable to find it.

I need absolutely NO features - just FTP.

---

### Post by elliotbeken on 2011-08-14
What i do is install ssh (sudp apt-get install ssh) and just use sftp://ipaddress in my filezilla ftp client. this will let users get access to their home dirs and it is also secure 

hope this helps

---

### Post by spiky001 on 2011-08-14
You dont even need filezilla it can be done from nautlus as well

---

### Post by W3ird_N3rd on 2011-08-14
> **elliotbeken said:**
> What i do is install ssh (sudp apt-get install ssh) and just use sftp://ipaddress in my filezilla ftp client. this will let users get access to their home dirs and it is also secure 

hope this helps
This indeed works, but it allows whoever logs in access to the entire filesystem. That's a bit *too* much really.

Okay, I do need one feature: a base directory the user can't get out of.
> **spiky001 said:**
> You dont even need filezilla it can be done from nautlus as well
I need a server, not a client.

[edit]
I've found that vsftpd does pretty much the same - yeah, it works pretty quick, but directly grants access to the entire filesystem.

I don't want to be spending hours on this like I'm doing now. I wish there was a more elegant, simple solution to this.

---

### Post by Wim Sturkenboom on 2011-08-15
It takes me about a minute to configure vsftpd (if I have my notes next to me ;) )

Modifications on default config
```

# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
# WimS
# disable anonymous
anonymous_enable=NO

# Uncomment this to enable any form of FTP write command.
# WimS
# enable writes
write_enable=YES

```

Additions to default config
```

#WimS; additional config
#jail user to their homedirectory
chroot_local_user=YES

#WimS: only allow selected users
userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd.user_list

```

And the user list (/etc/vsftpd.user_list)
```

# admin users need access for backups
brian
wim

# website administrators (basically developers) might want access to upload pages
# you can add them here
commandcentre
tacroom

```

Setting up ftps takes another minute or so :)

---

### Post by tredegar on 2011-08-15
File transfer utilities don't get much simpler than [woof]("http://www.linux.com/archive/feature/60098")

---

### Post by mutley89 on 2011-08-15
> **tredegar said:**
> File transfer utilities don't get much simpler than [woof]("http://www.linux.com/archive/feature/60098")

This is ideal for what I want, however i tried it and get :

```
 woof -i 192.168.2.4  pokerstove.txt 
Now serving on http://192.168.2.4:8080/
-Satellite-C650.local - - [15/Aug/2011 14:52:16] "GET /pokerstove.txt HTTP/1.1" 200 -
----------------------------------------
Exception happened during processing of request from ('192.168.2.4', 38729)
Traceback (most recent call last):
  File "/usr/lib/python2.7/SocketServer.py", line 284, in _handle_request_noblock
    self.process_request(request, client_address)
  File "/usr/lib/python2.7/SocketServer.py", line 310, in process_request
    self.finish_request(request, client_address)
  File "/usr/lib/python2.7/SocketServer.py", line 323, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.7/SocketServer.py", line 641, in __init__
    self.finish()
  File "/usr/lib/python2.7/SocketServer.py", line 694, in finish
    self.wfile.flush()
  File "/usr/lib/python2.7/socket.py", line 303, in flush
    self._sock.sendall(view[write_offset:write_offset+buffer_size])
error: [Errno 32] Broken pipe
----------------------------------------
```Edit: Fix here: [http://aur.archlinux.org/packages.php?ID=46323](http://aur.archlinux.org/packages.php?ID=46323)
Download the tarball and use woof-nofork.patch

---

### Post by W3ird_N3rd on 2011-08-15
> **Wim Sturkenboom said:**
> It takes me about a minute to configure vsftpd (if I have my notes next to me ;) )

Modifications on default config
```

# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
# WimS
# disable anonymous
anonymous_enable=NO

# Uncomment this to enable any form of FTP write command.
# WimS
# enable writes
write_enable=YES

```

Additions to default config
```

#WimS; additional config
#jail user to their homedirectory
chroot_local_user=YES

#WimS: only allow selected users
userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd.user_list

```

And the user list (/etc/vsftpd.user_list)
```

# admin users need access for backups
brian
wim

# website administrators (basically developers) might want access to upload pages
# you can add them here
commandcentre
tacroom

```

Setting up ftps takes another minute or so :)
Thanks!

Given your notes, yes, you can set it up in a minute. If you don't have those notes, you first need to read several pages to get it like this.

And there's still something, with this config the user is jailed to their home directory. Which in many cases would be fine, but the home directory is on a small SSD. I'd rather see the user jailed to /media/truckloadofspace/userftpdir. Figuring out how to do that will surely take more than a minute. Not that I'm that lazy, but sometimes you need things to work quickly. Sometimes there's a deadline.

I've seen myself too often at a PC quoting Trinity "I don't have time for this s***." After that, a rage similar to the one in the movie follows. :popcorn:

I'm sure that vsftpd is a fine ftp server (and I'm just going to keep your notes and figure out how to change the home dir, if that's possible), but the elegance with which software like SlimFTPd on Windows (which doesn't even have a GUI and is BSD-licensed, so I wonder how hard it would be to port it to *nix) shows that it *can* be simple makes me sad.

I also believe having system users for FTP-users is downright wrong and I don't care how many developers disagree with me. You should just be able to enter username, password, homedir and rights and as long as the FTP-software has rights to that directory, everything should be fine. Nothing else should have to be done. But that fairytale seem to work only on Windows so far.
> **tredegar said:**
> File transfer utilities don't get much simpler than [woof]("http://www.linux.com/archive/feature/60098")
Nice, the problem was I needed to receive some files, and I didn't want to ask the other side to forward ports or set up anything.

So the server had to be on my side. On a LAN or if I want to offer a file it's easier to set up an HTTP-server. Generally on a LAN I can just use NFS.

---

### Post by Wim Sturkenboom on 2011-08-15
I was just joking ;) Took me a little longer the first time as well (about 250 times a long, I think ;). Just posted it as reference.

With regards to your truckloadsofspace. Without knowing your 'design', it's difficult to say but why didn't you put the home directory on truckloadsofspace? I don't know if you can jail the user to another directory (basically not as far as I can see).

---

### Post by W3ird_N3rd on 2011-08-15
> **Wim Sturkenboom said:**
> With regards to your truckloadsofspace. Without knowing your 'design', it's difficult to say but why didn't you put the home directory on truckloadsofspace?
Because I'm a silly Ubuntu user. I have my home on my SSD so thumbnails and other small files can be loaded quickly (it's a desktop). And for the account I use to login that's perfectly sufficient.

For a virtual FTP user who should have never been a system user in the first place it's less than ideal.

My "design" is to put all big files and multimedia on truckloadofspace (I don't actually call it that, it's actually WD15EADS for me).

Chatlogs go to truckloadofspace because of the number of writes. /tmp is a tmpfs ramdisk as is /var/tmp and /var/log.

Pretty much everything else is for the SSD. OS, program files, homedir.
> I don't know if you can jail the user to another directory (basically not as far as I can see).
apt-get remove vsftpd. :(

---

### Post by W3ird_N3rd on 2011-08-16
I got what I want, it took me a little under an hour, I think. Which is more than a minute. Anyway. As I always share solutions (even though no-one cares), here goes. This is a single-user setup. I can't be bothered to figure out how to add more users.

Install proftpd.

sudo gedit /etc/proftpd/proftpd.conf

Add this:
> # Use only AuthUserFiles when authenticating, and not the system's /etc/passwd
AuthOrder mod_auth_file.c

AuthUserFile	/etc/proftpdusers.local
AuthGroupFile	/etc/proftpdgroups.local
DefaultRoot /path/to/dir/to/jail/user

Uncomment this:
> #RequireValidShell		off
ftpasswd --name USERNAME --passwd --home /path/to/dir/to/jail/user --shell /bin/false -uid 1 -gid 1

sudo mv ftpd.passwd /etc/proftpdusers.local

sudo gedit /etc/proftpdgroups.local

Put this in:
> group1:dontcare:1:USERNAME

sudo chown 1:1 /path/to/dir/to/jail/user (if you don't do this the FTP user won't be able to upload/delete/etc)

FileZilla server or SlimFTPd should REALLY be ported to Linux.

---

### Post by iconoclast hero on 2011-08-16
> **W3ird_N3rd said:**
> I got what I want, it took me a little under an hour, I think. Which is more than a minute. Anyway. As I always share solutions (even though no-one cares), here goes. 
FileZilla server or SlimFTPd should REALLY be ported to Linux.

Don't be so sure no-one cares.  I wanted to say thank you and that I've been following this thread to see what turned up.  I ultimately went with proftpd a while back and haven't gotten around to finishing all of what I wanted to do, but I do have most of it working.  I agree that it would be nice if FileZilla was ported over...  I switched to that from bulletproof ftp which was also very easy.  I think the problem with linux is that it is just too configurable to be simple.

---

### Post by OwlBoy on 2011-09-09
> **elliotbeken said:**
> What i do is install ssh (sudp apt-get install ssh) and just use sftp://ipaddress in my filezilla ftp client. this will let users get access to their home dirs and it is also secure 

hope this helps

Exactly what I wanted. Thanks for the tip!

---

