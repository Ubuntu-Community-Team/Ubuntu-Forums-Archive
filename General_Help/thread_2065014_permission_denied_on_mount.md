---
title: "permission denied on mount"
date: 2012-09-30
forum: General Help
---

### Post by qwertyjjj on 2012-09-30
I get a permission denied error when attempting to mount a shared file from a server.
It was setup with guest access ticked so am not sure what is wrong.
When the password prompt appears I just press return for blank:

```

usb@usb:~$ sudo mount -t smbfs //192.168.0.9/Videos /mnt/Videos -o username=guest
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
usb@usb:~$ cd /mnt
usb@usb:/mnt$ ls -l
total 4
drwxr-xr-x 2 root root 4096 Sep 30 23:15 Videos
usb@usb:/mnt$ 

usb@usb:/mnt$ smbclient -L 192.168.0.9 -Uguest
Enter guest's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (jmediacentre-A880G server (Samba, Ubuntu))
	**Videos          Disk  **    
	Media           Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	JMEDIACENTRE-A88     jmediacentre-A880G server (Samba, Ubuntu)
	USB                  usb server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            JMEDIACENTRE-A880G
usb@usb:/mnt$

```

---

### Post by critin on 2012-09-30
Were you able to get in before, is this something new?
Was it also setup with no password needed?  All folders and files inside shared?  Did you configure Samba with no password needed?

---

### Post by Morbius1 on 2012-10-01
When you get a second you might want to go into smb.conf on the server and fix this:
> [COLOR=Blue]**jmediacentre-A880G**[/COLOR] server (Samba, Ubuntu)netbios names can only be 15 characters long or less. That one is 18.

You could change your hostname on the server to correct this but the fastest way to fix this for samba purposes is to use smb.conf itself. Add a line under the workgroup line on the server's smb.conf that looks like this:
```
netbios name = jmediactr-A880G 
```[COLOR=Blue]*Doesn't have to be that exact name but keep it 15 characters long or less.*[/COLOR]

Then restart samba services:
```
sudo service smbd restart
sudo service nmbd restart
```

---

