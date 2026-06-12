---
title: "Samba Roaming Profile Network &quot;/home&quot; Folder"
date: 2010-03-03
forum: General Help
---

### Post by moshansky on 2010-03-03
Hi,
[U]
**Background of the project:**[/U]
I'm trying to setup a Ubuntu workstation in a corporate environment, right now just as a proof of concept but hopefully soon I will do the real thing. The problem is trying to establish a Linux equivalent of a roaming profile. The user logs into the Ubuntu Machine using their Windows Active Directory Credentials. (A big victory) Then I would like the client to mount their /home folder off of a Windows 2008 Small Business Server. So far I can make Ubuntu mount everyone's /home folders but I would like to narrow it down to only mount the specific user who has logged in and with proper permissions.

**_What I'm trying to accomplish:_**
Mount the proper /home folder from the server with that users permissions so they are the owner, have full access etc.
Only Mount the current users folder. Or any logged on etc. (I just don't want to mount every folder for every user that exists in Active Directory)
Do it automagically.;)


To give you and idea: I login as "dirtandgas\test" (dirtandgas is our test domain) and here is the line from the FSTAB that's used to mount the directory.
```

//server/redirectedfolders /home/DIRTANDGAS cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode0777,dir_mode0777,rw,uid=892863608 0 0

```Now I know if I changed that to the following, it would only mount the one directory, but I don't want to have to maintain the FSTAB on each computer for each user. (the point of using active directory)

```

//server/redirectedfolders**/test** /home/DIRTANDGAS**/test** cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode0777,dir_mode0777,rw,uid=892863608 0 0

```So here is my ideal solution to work something like this....
```

 //server/redirectedfolders**/[$USERNAME]** /home/DIRTANDGAS**/[$USERNAME]**  cifs credentials=/root/**[USER Credentials]**,iocharset=utf8,file_mode0777,dir_mode0777,rw,uid=**[$USERNAME's UID]**  0 0
 
```But my understanding is FSTAB does it's magic at boot, which would mean there's no way to query which user is logging in.

I'm not sure what to use to do this mount (autofs??) during the login process, and to automate it using the credentials provided to the Gnome Login Screen. I'm thoroughly stuck as to where to go from here, so if anyone has any ideas please share, or if I'm using an entirely wrong approach to this all.

Many Thanks!

---

### Post by moshansky on 2010-03-04
So with more Research, I think I can do this using a script run during the /etc/gdm/PostLogin/

However I still need to run the mount command as:
```

mount  -t cifs //server/redirectedfolders**/[$USERNAME]** /home/DIRTANDGAS**/[$USERNAME]**  -o credentials=**[USER Credentials]**,iocharset=utf8,file_mode0777,dir_mode0777,rw,uid=**[$USERNAME's UID]**  0 0

```The big problem I see, is how do I get the credentials entered into the GDM Login Screen into this script. 
Login Name: dirtandgas\test >> [$Username]
Password:    password >> [$User credentials]

---

### Post by Agent ME on 2010-03-04
If your user's files are being hosted on a windows computer, I think you'll lose all permissions settings on the files. Just a warning. If you do get it working and run into this, you'll probably want to add a parameter to mount to give all files permissions of 700.

---

### Post by dcstar on 2010-03-04
Linux System folders - like /home top level user folders - require full Linux filesystem support.

Native Windows filesystems like NTFS and FAT do not fully support Linux filesystem requirements and can never be used for Linux system folders.

---

### Post by moshansky on 2010-03-22
So In order to do this well I used PAM and libpam_mount to mount the home directory from our Windows SBS Server. This handles authentication as well as mounting at login and unmounting at logoff. Check this tutorial for more information about PAM Mount... [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) or our blog at [http://blog.itinc.biz/2010/03/integrating-linux-into-windows-domain.html ]("http://blog.itinc.biz/2010/03/integrating-linux-into-windows-domain.html")for tutorials on what we did manage to accomplish.

Although there seems to be problems with the process, most likely due to permissions issues and the lack thereof on the windows side. Perhaps in the future I'll redo this instead using a NFS Server and see how well it works.

Thanks Everyone for the help!

---

